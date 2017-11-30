---
title: "ICLRStrongName::StrongNameSignatureVerification — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e326eadcf91fbab0edb81844172bfabbd0851dc7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="e9790-102">ICLRStrongName::StrongNameSignatureVerification — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9790-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="e9790-103">Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy, która zostanie poddana weryfikacji zgodnie z określonym flagi.</span><span class="sxs-lookup"><span data-stu-id="e9790-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9790-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9790-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9790-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9790-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e9790-106">[in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu można zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="e9790-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e9790-107">[in] Flagi, aby zmodyfikować zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e9790-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="e9790-108">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e9790-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e9790-109">`SN_INFLAG_FORCE_VER`(0x00000001) - wymusza weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="e9790-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="e9790-110">`SN_INFLAG_INSTALL`(0x00000002) — określa, że jest to plik manifestu jest weryfikowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e9790-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="e9790-111">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) — określa, że pamięć podręczna będzie zezwalał na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="e9790-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="e9790-112">`SN_INFLAG_USER_ACCESS`(0x00000008) — określa, czy zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9790-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="e9790-113">`SN_INFLAG_ALL_ACCESS`(0x00000010) — określa, czy pamięć podręczna zapewni żadnych gwarancji ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="e9790-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="e9790-114">`SN_INFLAG_RUNTIME`(0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="e9790-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e9790-115">[out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9790-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="e9790-116">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="e9790-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="e9790-117">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="e9790-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9790-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e9790-118">Return Value</span></span>  
 <span data-ttu-id="e9790-119">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="e9790-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9790-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9790-120">Requirements</span></span>  
 <span data-ttu-id="e9790-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9790-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9790-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e9790-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e9790-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9790-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9790-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9790-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9790-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9790-125">See Also</span></span>  
 [<span data-ttu-id="e9790-126">StrongNameSignatureVerificationEx — metoda</span><span class="sxs-lookup"><span data-stu-id="e9790-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="e9790-127">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="e9790-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)