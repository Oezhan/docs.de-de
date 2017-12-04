---
title: Beim Bereitstellen von Windows-Container auf Azure-Container-Dienst (d. h. Kubernetes)
description: ".NET Microservices Architektur für Datenvolumes .NET-Anwendungen | Beim Bereitstellen von Windows-Container auf Azure-Container-Dienst (d. h. Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="f7523-103">Beim Bereitstellen von Windows-Container auf Azure-Container-Dienst (d. h. Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="f7523-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="f7523-104">Azure Containerdienst wird die Konfiguration der beliebten Open Source-Tools und Technologien speziell für Azure optimiert.</span><span class="sxs-lookup"><span data-stu-id="f7523-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="f7523-105">Sie erhalten eine geöffnete Projektmappe, die Portabilität, die sowohl für die Container als auch für Ihre Anwendungskonfiguration bietet.</span><span class="sxs-lookup"><span data-stu-id="f7523-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="f7523-106">Wählen Sie die Größe, die Anzahl der Hosts und die Orchestrator-Tools.</span><span class="sxs-lookup"><span data-stu-id="f7523-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="f7523-107">Azure-Container-Dienst übernimmt die Infrastruktur für Sie.</span><span class="sxs-lookup"><span data-stu-id="f7523-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="f7523-108">Wenn Sie bereits mit Open Source-Orchestrators wie Kubernetes, Docker Containerhostclustern oder DC/OS arbeiten, müssen Sie Ihre vorhandene Management-Methoden zum Container Arbeitslasten in die Cloud verschieben zu ändern.</span><span class="sxs-lookup"><span data-stu-id="f7523-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="f7523-109">Verwenden Sie die Anwendung-Verwaltungstools, dass Sie bereits mit vertraut, und eine Verbindung über die standard-API-Endpunkte für den Orchestrator Ihrer Wahl herstellen.</span><span class="sxs-lookup"><span data-stu-id="f7523-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="f7523-110">Alle diese Orchestrators sind ausgereifte Umgebungen, wenn Sie Linux-Docker-Containern verwendet werden, aber sie außerdem Unterstützung für Windows-Containern wie der 2017 (einige zuvor, einige jüngst, abhängig von der Orchestrator).</span><span class="sxs-lookup"><span data-stu-id="f7523-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="f7523-111">Z. B. in Kubernetes, Unterstützung für Container systemeigen (wesentlicher) mit Windows-Container auf Kubernetes ist auch eine effiziente und zuverlässige (in der Vorschau bis 2017 frühzeitig fallen).</span><span class="sxs-lookup"><span data-stu-id="f7523-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f7523-112">[Zurück](when-to-deploy-windows-containers-to-service-fabric.md)
[Weiter](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="f7523-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>