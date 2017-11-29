---
title: "ICLRPolicyManager::SetActionOnTimeout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 924a8a64fb698ec0e78397ad791f445297c0fee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="a7e69-102">ICLRPolicyManager::SetActionOnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7e69-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="a7e69-103">Określa akcję zasady, którą powinno mieć środowisko uruchomieniowe języka wspólnego (CLR), gdy upłynie limit czasu określonej operacji.</span><span class="sxs-lookup"><span data-stu-id="a7e69-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7e69-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7e69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7e69-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a7e69-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący, który chcesz określić limit czasu akcji.</span><span class="sxs-lookup"><span data-stu-id="a7e69-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="a7e69-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a7e69-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a7e69-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a7e69-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="a7e69-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a7e69-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="a7e69-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a7e69-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="a7e69-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a7e69-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="a7e69-112">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję zasad do wykonania, kiedy upłynie limit czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="a7e69-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7e69-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7e69-113">Return Value</span></span>  
  
|<span data-ttu-id="a7e69-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7e69-114">HRESULT</span></span>|<span data-ttu-id="a7e69-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a7e69-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7e69-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7e69-116">S_OK</span></span>|<span data-ttu-id="a7e69-117">`SetActionOnTimeout`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7e69-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a7e69-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7e69-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7e69-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a7e69-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7e69-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7e69-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7e69-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a7e69-121">The call timed out.</span></span>|  
|<span data-ttu-id="a7e69-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7e69-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7e69-123">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a7e69-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7e69-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7e69-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7e69-125">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a7e69-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7e69-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7e69-126">E_FAIL</span></span>|<span data-ttu-id="a7e69-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a7e69-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7e69-128">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a7e69-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7e69-129">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7e69-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7e69-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a7e69-130">E_INVALIDARG</span></span>|<span data-ttu-id="a7e69-131">Nie można ustawić limitu czasu dla określonego `operation`, lub podano nieprawidłową wartość dla `operation`.</span><span class="sxs-lookup"><span data-stu-id="a7e69-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7e69-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7e69-132">Remarks</span></span>  
 <span data-ttu-id="a7e69-133">Wartość limitu czasu może być domyślny limit czasu ustawiony przez środowisko CLR lub wartość określonego przez hosta w wywołaniu [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a7e69-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="a7e69-134">Nie wszystkie wartości działania zasad można określić jako zachowanie limitu czasu dla operacji CLR.</span><span class="sxs-lookup"><span data-stu-id="a7e69-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="a7e69-135">`SetActionOnTimeout`zwykle służą tylko do eskalować zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a7e69-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="a7e69-136">Na przykład host można określić, że wątek przerwań przekształcone niegrzeczny wątku przerwań, ale nie można określić odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="a7e69-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="a7e69-137">W poniższej tabeli opisano poprawne `action` wartości prawidłowe `operation` wartości.</span><span class="sxs-lookup"><span data-stu-id="a7e69-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="a7e69-138">Wartość`operation`</span><span class="sxs-lookup"><span data-stu-id="a7e69-138">Value for `operation`</span></span>|<span data-ttu-id="a7e69-139">Prawidłowe wartości`action`</span><span class="sxs-lookup"><span data-stu-id="a7e69-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="a7e69-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a7e69-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="a7e69-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="a7e69-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="a7e69-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="a7e69-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="a7e69-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7e69-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a7e69-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7e69-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a7e69-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-145">-   eExitProcess</span></span><br /><span data-ttu-id="a7e69-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="a7e69-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a7e69-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a7e69-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a7e69-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="a7e69-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="a7e69-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7e69-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="a7e69-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7e69-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="a7e69-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-152">-   eExitProcess</span></span><br /><span data-ttu-id="a7e69-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="a7e69-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a7e69-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a7e69-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="a7e69-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="a7e69-156">OPR_ProcessExit</span></span>|<span data-ttu-id="a7e69-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-157">-   eExitProcess</span></span><br /><span data-ttu-id="a7e69-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="a7e69-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="a7e69-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="a7e69-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="a7e69-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7e69-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7e69-161">Requirements</span></span>  
 <span data-ttu-id="a7e69-162">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7e69-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e69-163">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7e69-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7e69-164">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7e69-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7e69-165">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e69-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e69-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7e69-166">See Also</span></span>  
 [<span data-ttu-id="a7e69-167">EClrOperation — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a7e69-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="a7e69-168">EPolicyAction — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a7e69-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="a7e69-169">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e69-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a7e69-170">ICLRPolicyManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e69-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)