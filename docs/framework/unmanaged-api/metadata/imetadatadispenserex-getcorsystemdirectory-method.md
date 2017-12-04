---
title: IMetaDataDispenserEx::GetCORSystemDirectory-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="b53ea-102">IMetaDataDispenserEx::GetCORSystemDirectory-Methode</span><span class="sxs-lookup"><span data-stu-id="b53ea-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="b53ea-103">Ruft das Verzeichnis, das die aktuelle common Language Runtime (CLR) enthält.</span><span class="sxs-lookup"><span data-stu-id="b53ea-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="b53ea-104">Diese Methode ist nur für die Verwendung von Out-of-Process-Debugger unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b53ea-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="b53ea-105">Wenn aus einer anderen Komponente aufgerufen wird, gibt es E_NOTIMPL zurück.</span><span class="sxs-lookup"><span data-stu-id="b53ea-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53ea-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b53ea-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b53ea-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="b53ea-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="b53ea-108">[out] Der Puffer, der den Namen des Verzeichnisses erhalten.</span><span class="sxs-lookup"><span data-stu-id="b53ea-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b53ea-109">[in] Die Größe in Bytes, der `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53ea-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="b53ea-110">[out] Die Anzahl der Bytes, die tatsächlich im zurückgegebenen `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53ea-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53ea-111">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b53ea-111">Requirements</span></span>  
 <span data-ttu-id="b53ea-112">**Plattform:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53ea-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53ea-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b53ea-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b53ea-114">**Bibliothek:** als Ressource in MsCorEE.dll verwendet</span><span class="sxs-lookup"><span data-stu-id="b53ea-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b53ea-115">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53ea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53ea-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b53ea-116">See Also</span></span>  
 [<span data-ttu-id="b53ea-117">IMetaDataDispenserEx-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="b53ea-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="b53ea-118">IMetaDataDispenser-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="b53ea-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)