---
title: "IMetaDataImport::GetClassLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cece37a6321fc68cbff2957f9753af5f2f916f5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="cb5d4-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb5d4-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="cb5d4-103">Pobiera informacje o układzie dla klasy odwołuje się określony element TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb5d4-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb5d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb5d4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cb5d4-106">[in] Token TypeDef dla klasy z układem do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="cb5d4-107">[out] Jedna z wartości 1, 2, 4, 8 lub 16, reprezentujący rozmiaru pakietu klasy.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="cb5d4-108">[out] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cb5d4-109">[in] Maksymalny rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="cb5d4-110">[out] Liczba elementów zwracanych w `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="cb5d4-111">[out] Rozmiar w bajtach klasy reprezentowany przez `td`.</span><span class="sxs-lookup"><span data-stu-id="cb5d4-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5d4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb5d4-112">Requirements</span></span>  
 <span data-ttu-id="cb5d4-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5d4-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb5d4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb5d4-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb5d4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb5d4-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5d4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb5d4-117">See Also</span></span>  
 [<span data-ttu-id="cb5d4-118">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="cb5d4-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cb5d4-119">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="cb5d4-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)