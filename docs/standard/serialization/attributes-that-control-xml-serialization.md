---
title: Attribute zur Steuerung der XML-Serialisierung
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 3c6e46c97a943f1c77ffd12dd2b3bc85a64b3c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585038"
---
# <a name="attributes-that-control-xml-serialization"></a>Attribute zur Steuerung der XML-Serialisierung
Sie können die in der folgenden Tabelle aufgeführten Attribute auf Klassen und Klassenmember anwenden, um zu steuern, wie Instanzen der Klasse durch die <xref:System.Xml.Serialization.XmlSerializer>-Klasse serialisiert bzw. deserialisiert werden. Wie die XML-Serialisierung mithilfe dieser Attribute gesteuert wird, wird unter [Steuern der XML-Serialisierung mit Attributen](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) beschrieben.  
  
 Diese Attribute können auch verwendet werden, um die durch einen XML-Webdienst generierten literalen SOAP-Nachrichten zu steuern. Weitere Informationen zur Anwendung dieser Attribute auf eine XML-Webdienstmethode finden Sie unter [XML-Serialisierung mit XML-Webdiensten](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md).  
  
 Weitere Informationen zu Attributen finden Sie unter [Attribute](../../../docs/standard/attributes/index.md).  
  
|Attribut|Betrifft|Bedeutung|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert, wodurch ein Array von <xref:System.Xml.XmlAttribute>-Objekten zurückgegeben wird.|Beim Deserialisieren wird das Array mit <xref:System.Xml.XmlAttribute>-Objekten gefüllt, die für alle im Schema unbekannten XML-Attribute stehen.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert, wodurch ein Array von <xref:System.Xml.XmlElement>-Objekten zurückgegeben wird.|Beim Deserialisieren wird das Array mit <xref:System.Xml.XmlElement>-Objekten gefüllt, die für alle im Schema unbekannten XML-Elemente stehen.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert, wodurch ein Array von komplexen Objekten zurückgegeben wird.|Die Member des Arrays werden als Member eines XML-Arrays generiert.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert, wodurch ein Array von komplexen Objekten zurückgegeben wird.|Die abgeleiteten Typen, die in ein Array eingefügt werden können. Wird in der Regel in Verbindung mit einem <xref:System.Xml.Serialization.XmlArrayAttribute>-Objekt angewendet.|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert.|Der Member wird als XML-Attribut serialisiert.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert.|Der Member kann durch Verwendung einer Enumeration eindeutig bestimmt werden.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Öffentliches Feld, Eigenschaft, Parameter oder Rückgabewert.|Das Feld oder die Eigenschaft wird als XML-Element serialisiert.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Öffentliches Feld, das ein Enumerationsbezeichner ist.|Der Elementname eines Enumerationsmembers.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Öffentliche Eigenschaften und Felder.|Die Eigenschaft oder das Feld wird beim Serialisieren der Klasse, in dem sie bzw. es enthalten ist, ignoriert.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Öffentliche abgeleiteten Klassendeklarationen, und Rückgabewerte von öffentlichen Methoden für WSDL-Dokumente (Web Services Description Language).|Diese Klasse wird beim Generieren von Schemas eingeschlossen (und daher bei der Serialisierung erkannt).|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Deklarationen öffentlicher Klassen.|Steuert die XML-Serialisierung des Attributziels als XML-Stammelement. Mit diesem Attribut können Sie Namespace und Elementnamen genauer angeben.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Öffentliche Eigenschaften und Felder.|Die Eigenschaft oder das Feld soll als XML-Text serialisiert werden.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Deklarationen öffentlicher Klassen.|Der Name und Namespace des XML-Typs.|  
  
 Zusätzlich zu diesen Attributen, die sich alle im <xref:System.Xml.Serialization>-Namespace befinden, können Sie auch das <xref:System.ComponentModel.DefaultValueAttribute>-Attribut auf ein Feld anwenden. Durch **DefaultValueAttribute** wird der Wert festgelegt, der dem Member automatisch zugewiesen wird, falls kein Wert angegeben wurde.  
  
 Informationen zur Steuerung der XML-Serialisierung von codiertem SOAP finden Sie unter [Attribute zur Steuerung der Serialisierung von codiertem SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [XML- und SOAP-Serialisierung](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Steuern der XML-Serialisierung mit Attributen](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [Vorgehensweise: Angeben eines alternativen Elementnamens für einen XML-Stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [Vorgehensweise: Serialisieren eines Objekts](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Vorgehensweise: Deserialisieren eines Objekts](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
