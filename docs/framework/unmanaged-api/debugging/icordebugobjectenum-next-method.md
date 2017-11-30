---
title: "ICorDebugObjectEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72195dbf74639d5799bb96754019dddf0f30101a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="76ad8-102">ICorDebugObjectEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="76ad8-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="76ad8-103">Pobiera względną wirtualnych adresów (RVAs) określoną liczbę obiektów z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="76ad8-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ad8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76ad8-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76ad8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76ad8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="76ad8-106">[in] Liczba obiektów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="76ad8-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="76ad8-107">[out] Tablicy wskaźników, z których każdy wskazuje obiekt CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="76ad8-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="76ad8-108">[out] Wskaźnik do liczby faktycznie zwracanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="76ad8-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="76ad8-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="76ad8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76ad8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76ad8-110">Requirements</span></span>  
 <span data-ttu-id="76ad8-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76ad8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76ad8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76ad8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76ad8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76ad8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76ad8-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76ad8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ad8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76ad8-115">See Also</span></span>  
 