---
title: '&lt;Beispiel&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598549"
---
# <a name="ltexamplegt-visual-basic"></a>&lt;Beispiel&gt; (Visual Basic)
Gibt ein Beispiel für das Element an.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parameter  
 `description`  
 Eine Beschreibung des Codebeispiels.  
  
## <a name="remarks"></a>Hinweise  
 Die `<example>` -Tag kann ein Beispiel zur Verwendung einer Methode oder anderen Bibliothekmembers angegeben. Dies schließt im Allgemeinen die Verwendung des [\<code](../../../visual-basic/language-reference/xmldoc/code.md)-Tags ein.  
  
 Dokumentationskommentare werden zu einer Datei verarbeitet, indem sie mit [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) kompiliert werden.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet die `<example>` Tag enthalten ein Beispiel für die Verwendung der `ID` Feld.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Kommentartags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
