---
title: "ICLRDataTarget2::FreeVirtual — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.FreeVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1619e9eb02eec1985c3c550626ef955162d1b984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="9e42c-102">ICLRDataTarget2::FreeVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e42c-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="9e42c-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) dostęp do usług danych do wolnej pamięci, która była przydzielona wcześniej do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9e42c-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e42c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e42c-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e42c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e42c-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="9e42c-106">[in] A `CLRDATA_ADDRESS` wartość, która określa początkowy adres pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="9e42c-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="9e42c-107">[in] Rozmiar w bajtach, pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="9e42c-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="9e42c-108">[in] Flagi, które kontrolują zwalnianie pamięci.</span><span class="sxs-lookup"><span data-stu-id="9e42c-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="9e42c-109">Zobacz Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9e42c-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e42c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e42c-110">Remarks</span></span>  
 <span data-ttu-id="9e42c-111">`FreeVirtual` Metody służy jako otoka logiczne dla środowiska Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9e42c-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="9e42c-112">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e42c-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e42c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e42c-113">Requirements</span></span>  
 <span data-ttu-id="9e42c-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e42c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e42c-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9e42c-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9e42c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e42c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e42c-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e42c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e42c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e42c-118">See Also</span></span>  
 [<span data-ttu-id="9e42c-119">ICLRDataTarget2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9e42c-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="9e42c-120">AllocVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="9e42c-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)