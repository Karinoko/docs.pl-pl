---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="332a1-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="332a1-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="332a1-103">Modyfikuje zasady powiązanie dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="332a1-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="332a1-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="332a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="332a1-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="332a1-106">[in] Tożsamość zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="332a1-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="332a1-107">[in] Nową tożsamość zestawu zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="332a1-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="332a1-108">[in] Wskaźnik do buforu, który zawiera dane zasad powiązania dla zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="332a1-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="332a1-109">[in] Rozmiar powiązania zasady mają zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="332a1-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="332a1-110">[in] Logiczne połączenie lub [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wartości, wskazując kontroli przekierowania.</span><span class="sxs-lookup"><span data-stu-id="332a1-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="332a1-111">[out] Wskaźnik do buforu, który zawiera nowe powiązanie danych zasad.</span><span class="sxs-lookup"><span data-stu-id="332a1-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="332a1-112">[w, out] Wskaźnik do rozmiaru buforu nowych zasad powiązania.</span><span class="sxs-lookup"><span data-stu-id="332a1-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="332a1-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="332a1-113">Return Value</span></span>  
  
|<span data-ttu-id="332a1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="332a1-114">HRESULT</span></span>|<span data-ttu-id="332a1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="332a1-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="332a1-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="332a1-116">S_OK</span></span>|<span data-ttu-id="332a1-117">Zasada została pomyślnie zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="332a1-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="332a1-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="332a1-118">E_INVALIDARG</span></span>|<span data-ttu-id="332a1-119">`pwzSourceAssemblyIdentity`lub `pwzTargetAssemblyIdentity` miał odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="332a1-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="332a1-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="332a1-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="332a1-121">`pbNewApplicationPolicy`jest za mały.</span><span class="sxs-lookup"><span data-stu-id="332a1-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="332a1-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="332a1-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="332a1-123">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="332a1-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="332a1-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="332a1-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="332a1-125">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="332a1-125">The call timed out.</span></span>|  
|<span data-ttu-id="332a1-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="332a1-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="332a1-127">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="332a1-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="332a1-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="332a1-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="332a1-129">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="332a1-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="332a1-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="332a1-130">E_FAIL</span></span>|<span data-ttu-id="332a1-131">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="332a1-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="332a1-132">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="332a1-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="332a1-133">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="332a1-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="332a1-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="332a1-134">Remarks</span></span>  
 <span data-ttu-id="332a1-135">`ModifyApplicationPolicy` Metodę można wywołać dwa razy.</span><span class="sxs-lookup"><span data-stu-id="332a1-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="332a1-136">Pierwsze wywołanie należy podać wartość null dla `pbNewApplicationPolicy` parametru.</span><span class="sxs-lookup"><span data-stu-id="332a1-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="332a1-137">To wywołanie, którą będzie zwracać z wartością niezbędne dla `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="332a1-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="332a1-138">Drugie wywołanie należy podać tę wartość dla `pcbNewAppPolicySize`, a następnie wskaż bufor tego rozmiaru dla `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="332a1-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332a1-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="332a1-139">Requirements</span></span>  
 <span data-ttu-id="332a1-140">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="332a1-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="332a1-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="332a1-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="332a1-142">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="332a1-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="332a1-143">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="332a1-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332a1-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="332a1-144">See Also</span></span>  
 [<span data-ttu-id="332a1-145">ICLRHostBindingPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="332a1-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)