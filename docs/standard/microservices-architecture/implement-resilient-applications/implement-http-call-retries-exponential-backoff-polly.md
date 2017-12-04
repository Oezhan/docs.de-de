---
title: Implementieren von HTTP-Aufruf Wiederholungen mit exponenzieller mit Polly
description: ".NET Microservices Architektur für Datenvolumes .NET-Anwendungen | Implementieren von HTTP-Aufruf Wiederholungen mit exponenzieller mit Polly"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="b8f8f-104">Implementieren von HTTP-Aufruf Wiederholungen mit exponenzieller mit Polly</span><span class="sxs-lookup"><span data-stu-id="b8f8f-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="b8f8f-105">Die empfohlene Vorgehensweise für Wiederholungen mit exponenzieller Wartezeit ist erweiterte .NET Bibliotheken wie der open Source nutzen [Polly](https://github.com/App-vNext/Polly) Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="b8f8f-106">Polly ist eine .NET-Bibliothek, die Flexibilität und Behandlung vorübergehender Fehler Funktionen bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="b8f8f-107">Sie können diese Funktionen durch Anwenden von Richtlinien Polly, z. B. versuchen Sie es erneut, Trennschalter sein Isolation, Timeout und Fallback problemlos implementieren.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="b8f8f-108">Polly Ziel .NET 4.x und das .NET Standard Version 1.0 (der .NET Core unterstützt).</span><span class="sxs-lookup"><span data-stu-id="b8f8f-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="b8f8f-109">Die wiederholungsrichtlinie in Polly ist der Ansatz in eShopOnContainers verwendet, wenn HTTP-Wiederholungsversuche implementieren.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="b8f8f-110">Sie können eine Schnittstelle implementieren, damit Sie einfügen können, Standardfunktionen für "HttpClient" oder eine robuste Version von "HttpClient" mithilfe von Polly, je nachdem welche wiederholen-Richtlinienkonfiguration, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="b8f8f-111">Das folgende Beispiel zeigt die Schnittstelle, die in eShopOnContainers implementiert.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="b8f8f-112">Sie können die Standardimplementierung verwenden, wenn Sie nicht als einen robusten Mechanismus verwenden, beim Entwickeln oder einfacher Ansätze testen möchten.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="b8f8f-113">Der folgende Code zeigt die standardmäßigen "HttpClient" Implementierung ermöglichen-Anforderungen mit Authentifizierungstoken als ein optionaler Fall.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="b8f8f-114">Die interessante Implementierung besteht darin, code mit Polly die robusten Mechanismen, implementieren Sie verwenden möchten, jedoch ein anderes, ähnliches-Klasse – im folgenden Beispiel Wiederholungen mit exponenzieller Wartezeit.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="b8f8f-115">Mit Polly definieren Sie eine wiederholungsrichtlinie mit der Anzahl der Wiederholungen, die exponentielle Backoff-Konfiguration und die Aktionen an, wenn eine HTTP-Ausnahme, wie die Protokollierung des Fehlers aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="b8f8f-116">In diesem Fall wird die Richtlinie konfiguriert, damit die Anzahl der Male, die beim Registrieren von Typen in den IoC-Container angegeben versucht wird.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="b8f8f-117">Aufgrund der exponentiellen Backoff-Konfiguration Wenn der Code eine Ausnahme HttpRequest erkennt erneute Versuche durchgeführt die HTTP-Anforderung nach einer Wartezeit von eine Zeitspanne, die sich exponentiell zu, je nachdem, wie die Richtlinie konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="b8f8f-118">Wichtige Methode ist HttpInvoker, was ist der HTTP-Anforderungen in der gesamten diese hilfsprogrammmklasse.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="b8f8f-119">Dass die Methode intern ausgeführt, wird die HTTP-Anforderung mit \_policyWrapper.ExecuteAsync, die die wiederholungsrichtlinie berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="b8f8f-120">Im eShopOnContainers Geben Sie Polly Richtlinien beim Registrieren der Typen auf IoC-Container, wie im folgenden Code aus der [MVC-Web-app auf die startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) Klasse.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="b8f8f-121">Beachten Sie, dass die IHttpClient Objekte als Singleton statt als vorübergehend instanziiert werden, sodass TCP-Verbindungen effizient vom Dienst verwendet werden und [ein Problem mit Sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) erfolgt nicht.</span><span class="sxs-lookup"><span data-stu-id="b8f8f-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="b8f8f-122">Jedoch über die Stabilität der wichtige Punkt ist, dass Sie die Richtlinie Polly WaitAndRetryAsync in ResilientHttpClientFactory in der Methode CreateResilientHttpClient anwenden, wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="b8f8f-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="b8f8f-123">[Vorherigen] (Implement-custom-http-call-retries-exponential-backoff.md) [weiter] (implementieren-Circuit-Breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="b8f8f-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>