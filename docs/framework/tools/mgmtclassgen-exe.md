---
title: "Mgmtclassgen.exe (Management Strongly Typed Class Generator) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CIM types"
  - "Management Strongly Typed Class Generator"
  - "WMI class"
  - "Mgmtclassgen.exe"
  - "early-bound managed classes"
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# Mgmtclassgen.exe (Management Strongly Typed Class Generator)
Mit dem Management Strongly Typed Class Generator\-Tool können Sie schnell eine früh gebundene Klasse für eine angegebene WMI \(Windows Management Instrumentation\)\-Klasse generieren.  Die generierte Klasse vereinfacht den Code, den Sie für den Zugriff auf eine Instanz der WMI\-Klasse schreiben müssen.  
  
## Syntax  
  
```  
  
mgmtclassgen   
WMIClass [options]   
```  
  
|Argument|Beschreibung|  
|--------------|------------------|  
|*WMIClass*|Die WMI \(Windows Management Instrumentation\)\-Klasse, für die eine früh gebundene verwaltete Klasse generiert wird.|  
  
|Option|Beschreibung|  
|------------|------------------|  
|**\/l**  *language*|Gibt die Programmiersprache an, in der die früh gebundene verwaltete Klasse generiert werden soll.  Als Sprachargument können Sie **CS** \(C\#, Standard\), **VB** \(Visual Basic\),  **MC** \(C\+\+\) oder **JS** \(JScript\) festlegen.|  
|**\/m**  *machine*|Gibt den Computer an, auf dem sich die WMI\-Klasse befindet und mit dem eine Verbindung hergestellt werden soll.  Die Standardeinstellung ist der lokale Computer.|  
|**\/n**  *path*|Gibt den Pfad zum WMI\-Namespace an, der die WMI\-Klasse enthält.  Wenn Sie keinen Pfad angeben, generiert das Tool den Code für *WMIClass* im **Root\\cimv2**\-Standardnamespace.|  
|**\/o**  *classnamespace*|Gibt den .NET\-Namespace an, in dem die verwaltete Codeklasse generiert werden soll.  Wenn Sie keinen Klassennamespace angeben, generiert das Tool den Namespace aus dem WMI\-Namespace und dem Schemapräfix.  Das Schemapräfix ist der Bestandteil des Klassennamens, der dem Unterstrich vorangeht.  Für die **Win32\_OperatingSystem**\-Klasse im **Root\\cimv2**\-Namespace würde die Klasse beispielsweise in **ROOT.CIMV2.Win32** generiert werden.|  
|**\/p**  *filepath*|Gibt den Pfad zur Datei an, in der der generierte Code gespeichert werden soll.  Wenn Sie keinen Dateipfad angeben, erstellt das Tool die Datei im aktuellen Verzeichnis.  Es benennt die Klasse und die Datei, in der diese erstellt wird, anhand des *WMIClass*\-Arguments.  Die Namen der Klasse und der Datei stimmen mit dem Namen der *WMIClass* überein. Wenn *WMIClass* einen Unterstrich enthält, wird der Teil des Namens nach dem Unterstrich verwendet.  Wenn etwa der *WMIClass*\-Name das Format **Win32\_LogicalDisk** aufweist, werden die generierte Klasse und Datei mit "logicaldisk" bezeichnet.  Wenn bereits eine gleichnamige Datei vorhanden ist, wird diese überschrieben.|  
|**\/pw**  *password*|Gibt das Kennwort für die Anmeldung an einem Computer an, der durch die **\/m**\-Option angegeben ist.|  
|**\/u**  *user name*|Gibt den Benutzernamen für die Anmeldung an einem Computer an, der durch die **\/m**\-Option angegeben ist.|  
|**\/?**|Zeigt Befehlssyntax und Optionen für das Tool an.|  
  
## Hinweise  
 "Mgmtclassgen.exe" verwendet die <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName>\-Methode.  Sie können daher mit einem beliebigen benutzerdefinierten Codeanbieter Code in anderen verwalteten Sprachen als C\#, Visual Basic und JScript generieren.  
  
 Beachten Sie, dass die generierten Klassen an das Schema gebunden sind, für das sie generiert werden.  Änderungen am zugrunde liegenden Schema wirken sich auf die Klasse erst nach einer Neugenerierung aus.  
  
 In der folgenden Tabelle wird die Zuordnung von WMI Common Information Model \(CIM\)\-Typen zu Datentypen in einer generierten Klasse dargestellt:  
  
|CIM\-Typ|Datentyp in der generierten Klasse|  
|--------------|----------------------------------------|  
|CIM\_SINT8|**SByte**|  
|CIM\_UINT8|**Byte**|  
|CIM\_SINT16|**Int16**|  
|CIM\_UINT16|**UInt16**|  
|CIM\_SINT32|**Int32**|  
|SIM\_UINT32|**UInt32**|  
|CIM\_SINT64|**Int64**|  
|CIM\_UINT64|**UInt64**|  
|CIM\_REAL32|**Single**|  
|CIM\_REAL64|**Double**|  
|CIM\_BOOLEAN|**Boolean**|  
|CIM\_String|**String**|  
|CIM\_DATETIME|**DateTime** oder **TimeSpan**|  
|CIM\_REFERENCE|**ManagementPath**|  
|CIM\_CHAR16|**Char**|  
|CIM\_OBJECT|**ManagementBaseObject**|  
|CIM\_IUNKNOWN|**Objekt**|  
|CIM\_ARRAY|Array der zuvor aufgeführten Objekte|  
  
 Beim Generieren einer WMI\-Klasse werden Sie folgende Verhaltensweisen feststellen:  
  
-   Eine öffentliche Standardeigenschaft oder \-methode darf den gleichen Namen wie eine vorhandene Eigenschaft oder Methode aufweisen.  In diesem Fall wird der Name der Eigenschaft oder Methode in der generierten Klasse geändert, um Namenskonflikte zu vermeiden.  
  
-   Der Name einer Eigenschaft oder Methode in einer generierten Klasse darf ein Schlüsselwort der Zielprogrammiersprache sein.  In diesem Fall wird der Name der Eigenschaft oder Methode in der generierten Klasse geändert, um Namenskonflikte zu vermeiden.  
  
-   Qualifizierer in WMI sind Modifizierer, die Informationen zum Beschreiben einer Klasse, Instanz, Eigenschaft oder Methode enthalten.  In WMI werden Eigenschaften in einer generierten Klasse mithilfe von Standardqualifizierern wie **Read**, **Write** und **Key** beschrieben.  Beispiel: Eine Eigenschaft, die mit einem **Read**\-Qualifizierer modifiziert wird, wird in der generierten Klasse nur mit einem **get**\-Eigenschaftenaccessor definiert.  Da eine mit dem **Read**\-Qualifizierer markierte Eigenschaft schreibgeschützt sein soll, ist kein **set**\-Accessor definiert.  
  
-   Eine numerische Eigenschaft kann durch den **Values**\-Qualifizierer und den **ValueMaps**\-Qualifizierer modifiziert werden, um anzugeben, dass sie nur auf bestimmte zulässige Werte festgelegt werden kann.  Mit diesen **Values** und **ValueMaps** wird eine Enumeration erstellt, und die Eigenschaft wird der Enumeration zugewiesen.  
  
-   Eine Klasse, die nur eine Instanz aufweisen darf, wird in WMI mit dem Begriff "Singleton" bezeichnet.  Der Standardkonstruktor für eine Singleton\-Klasse initialisiert die Klasse daher zur einzigen Instanz dieser Klasse.  
  
-   Eine WMI\-Klasse kann über Eigenschaften verfügen, bei denen es sich um Objekte handelt.  Wenn Sie für eine solche WMI\-Klasse eine stark typisierte Klasse generieren, empfiehlt es sich, für die Typen der eingebetteten Objekteigenschaften stark typisierte Klassen zu generieren.  Dies ermöglicht Ihnen den stark typisierten Zugriff auf die eingebetteten Objekte.  Beachten Sie, dass der generierte Code den Typ des eingebetteten Objekts möglicherweise nicht erkennen kann.  In einem solchen Fall wird im generierten Code ein Kommentar erstellt, in dem Sie auf das Problem hingewiesen werden.  Sie können den generierten Code dann ändern, um den Typ der Eigenschaft an den der anderen generierten Klasse anzugleichen.  
  
-   Der Datenwert des CIM\_DATETIME\-Datentyps kann in WMI entweder einen bestimmten Zeitpunkt \(Datum und Uhrzeit\) oder ein Zeitintervall darstellen.  Wenn der Datenwert einen Zeitpunkt \(Datum und Uhrzeit\) darstellt, ist der Datentyp in der generierten Klasse **DateTime**.  Wenn der Datenwert ein Zeitintervall darstellt, ist der Datentyp in der generierten Klasse **TimeSpan**.  
  
 Es besteht auch die Möglichkeit, mithilfe der Verwaltungserweiterung für Server\-Explorer in Visual Studio .NET eine stark typisierte Klasse zu generieren.  
  
 Weitere Informationen über WMI finden Sie im Thema **Windows Management Instrumentation** in der Platform SDK\-Dokumentation.  
  
## Beispiele  
 Der folgende Befehl generiert eine verwaltete Klasse in C\#\-Code für die **Win32\_LogicalDisk**\-WMI\-Klasse im **Root\\cimv2**\-Namespace.  Das Tool schreibt die verwaltete Klasse in die Quelldatei, die sich unter "c:\\disk.cs" im **ROOT.CIMV2.Win32**\-Namespace befindet.  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Im folgenden Codebeispiel wird die programmgesteuerte Verwendung einer generierten Klasse veranschaulicht.  Zunächst wird eine Instanz der Klasse aufgelistet und der Pfad ausgegeben.  Anschließend wird eine Instanz der zu initialisierenden generierten Klasse mit einer Instanz von WMI erstellt.  `Process` ist die für **Win32\_Process** generierte Klasse, und `LogicalDisk` ist die für **Win32\_LogicalDisk** im **Root\\cimv2**\-Namespace generierte Klasse.  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## Siehe auch  
 <xref:System.Management>   
 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName>   
 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName>   
 [Tools](../../../docs/framework/tools/index.md)   
 [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md)