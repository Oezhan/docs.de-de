---
title: IMetaDataTables2::GetMetaDataStreamInfo-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStreamInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1631ae8398a8daa910931ff705440a2be0cf21b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="af5ff-102">IMetaDataTables2::GetMetaDataStreamInfo-Methode</span><span class="sxs-lookup"><span data-stu-id="af5ff-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="af5ff-103">Ruft den Namen, die Größe und den Inhalt des Metadatenstreams am angegebenen Index.</span><span class="sxs-lookup"><span data-stu-id="af5ff-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5ff-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="af5ff-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af5ff-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="af5ff-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="af5ff-106">[in] Der Index des angeforderten Metadaten-Streams.</span><span class="sxs-lookup"><span data-stu-id="af5ff-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="af5ff-107">[out] Ein Zeiger auf den Namen des Datenstroms.</span><span class="sxs-lookup"><span data-stu-id="af5ff-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="af5ff-108">[out] Ein Zeiger auf die Metadaten-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="af5ff-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="af5ff-109">[out] Die Größe in Bytes, der `ppv`.</span><span class="sxs-lookup"><span data-stu-id="af5ff-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5ff-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="af5ff-110">Requirements</span></span>  
 <span data-ttu-id="af5ff-111">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af5ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af5ff-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af5ff-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af5ff-113">**Bibliothek:** als Ressource in MsCorEE.dll verwendet</span><span class="sxs-lookup"><span data-stu-id="af5ff-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af5ff-114">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af5ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5ff-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="af5ff-115">See Also</span></span>  
 [<span data-ttu-id="af5ff-116">IMetaDataTables2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="af5ff-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="af5ff-117">IMetaDataTables-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="af5ff-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)