---
title: "ICLRStrongName::GetHashFromBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: afb3614d4911b7e8b8666b1205af1c1d3d176b5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="6a818-102">ICLRStrongName::GetHashFromBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a818-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="6a818-103">Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="6a818-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a818-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a818-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a818-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a818-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="6a818-106">[in] Wskaźnik do adresu blok pamięci, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="6a818-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="6a818-107">[in] Długość, w bajtach bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a818-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6a818-108">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="6a818-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6a818-109">Użyj wartości zero dla domyślnego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="6a818-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6a818-110">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="6a818-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6a818-111">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6a818-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6a818-112">[out] Rozmiar w bajtach, zwracana `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6a818-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a818-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6a818-113">Return Value</span></span>  
 <span data-ttu-id="6a818-114">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="6a818-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a818-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a818-115">Requirements</span></span>  
 <span data-ttu-id="6a818-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a818-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a818-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6a818-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6a818-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a818-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a818-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a818-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a818-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a818-120">See Also</span></span>  
 [<span data-ttu-id="6a818-121">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="6a818-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)