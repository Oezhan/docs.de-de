---
title: ICorDebugAppDomain2::GetFunctionPointerType-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetFunctionPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85c07ec6177621b571a376ad58a386e8ed31ea63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a>ICorDebugAppDomain2::GetFunctionPointerType-Methode
Ruft einen Zeiger auf eine Funktion, die einer bestimmten Signatur ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `nTypeArgs`  
 [in] Die Anzahl der Argumente des Typs für die Funktion.  
  
 `ppTypeArgs`  
 [in] Ein Array von Zeigern, von denen jedes auf ein ICorDebugType verweist, die ein Type-Argument der Funktion darstellt. Das erste Element ist der Rückgabetyp; jedes andere Element ist ein Parameter.  
  
 `ppType`  
 [out] Ein Zeiger auf die Adresse des ein `ICorDebugType` -Objekt, das der Zeiger auf die Funktion darstellt.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]