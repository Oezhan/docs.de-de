---
title: Implementieren des GridItem-Steuerelementmusters der Benutzeroberflächenautomatisierung
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: bfe7fb8ab64f148d8ca5af0e419ca60690a1acce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408287"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementieren des GridItem-Steuerelementmusters der Benutzeroberflächenautomatisierung
> [!NOTE]
>  Diese Dokumentation ist für .NET Framework-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Klassen verwenden möchten, die im <xref:System.Windows.Automation>-Namespace definiert sind. Aktuelle Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]finden Sie auf der Seite zur [Windows-Automatisierungs-API: UI-Automatisierung](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Dieses Thema enthält Richtlinien und Konventionen zum Implementieren von <xref:System.Windows.Automation.Provider.IGridItemProvider>, einschließlich Informationen über Eigenschaften. Links zu zusätzlichen Referenzen sind am Ende dieser Übersicht aufgelistet.  
  
 Die <xref:System.Windows.Automation.GridItemPattern> -Steuerelementmuster wird verwendet, um einzelne untergeordnete Steuerelemente von Containern zu unterstützen, implementieren <xref:System.Windows.Automation.Provider.IGridProvider>. Beispiele für Steuerelemente, die dieses Steuerelementmuster implementieren, finden Sie unter [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementierungsrichtlinien und -konventionen  
 Bei der Implementierung <xref:System.Windows.Automation.Provider.IGridProvider>, beachten Sie die folgenden Richtlinien und Konventionen:  
  
-   Rasterkoordinaten (Grid-Koordinaten) sind nullbasiert, wobei die obere linke Zelle die Koordinaten (0, 0) hat.  
  
-   Zusammengeführte Zellen ihren <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> und <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> -Eigenschaft entsprechend ihrer zugrunde liegenden Ankerzelle gemäß der Definition von der Benutzeroberflächenautomatisierungs-Anbieter. In der Regel sind dies die oberste Zeile und die am weitesten links liegende Spalte.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> bietet keine aktive Bearbeitung des Rasters wie etwa zusammenführen oder Teilen von Zellen.  
  
-   Steuerelemente implementieren <xref:System.Windows.Automation.Provider.IGridItemProvider> in der Regel durchlaufen werden kann (d. h. ein Benutzeroberflächenautomatisierungs-Client kann zu benachbarten Steuerelementen wechseln) mithilfe der Tastatur.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Erforderliche Member für IGridItemProvider  
 Die folgenden Eigenschaften und Methoden sind für das Implementieren von <xref:System.Windows.Automation.Provider.IGridItemProvider> erforderlich.  
  
|Erforderliche Member|Memberart|Hinweise|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Eigenschaft|Keiner|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Eigenschaft|Keiner|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Eigenschaft|Keiner|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Eigenschaft|Keiner|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Eigenschaft|Keiner|  
  
 Diesem Steuerelementmuster sind keine Methoden oder Ereignisse zugeordnet.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Ausnahmen  
 Diesem Steuerelementmuster sind keine Ausnahmen zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Steuerelementmuster für Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Unterstützung von Steuerelementmustern in einem Benutzeroberflächenautomatisierungs-Anbieter](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Steuerelementmuster für Benutzeroberflächenautomatisierung für Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementieren des Grid-Steuerelementmusters der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Übersicht über die Benutzeroberflächenautomatisierungs-Struktur](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Verwenden der Zwischenspeicherung in der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
