---
title: "ICLRIoCompletionManager::OnComplete — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager.OnComplete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd38679d1b8d099e5eb6330e03e2333b03780dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="44f33-102">ICLRIoCompletionManager::OnComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="44f33-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="44f33-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) z stan żądania We/Wy, który został utworzony za pomocą wywołania [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="44f33-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44f33-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44f33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44f33-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="44f33-106">[in] Wartość HRESULT, która wskazuje stan operacji wiązania.</span><span class="sxs-lookup"><span data-stu-id="44f33-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="44f33-107">Wartość S_OK wskazuje, że operacja została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="44f33-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="44f33-108">HOST_E_INTERRUPTED wskazuje, że wywołanie zakończony przed zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="44f33-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="44f33-109">E_FAIL wskazuje, że wystąpił nieznany, nieodwracalny, krytyczny błąd.</span><span class="sxs-lookup"><span data-stu-id="44f33-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="44f33-110">[in] Liczba bajtów przesłanych podczas przetwarzania żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="44f33-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="44f33-111">[in] Wskaźnik do `OVERLAPPED` struktury, który został przekazany do wywołania `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="44f33-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44f33-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44f33-112">Return Value</span></span>  
  
|<span data-ttu-id="44f33-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44f33-113">HRESULT</span></span>|<span data-ttu-id="44f33-114">Opis</span><span class="sxs-lookup"><span data-stu-id="44f33-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44f33-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="44f33-115">S_OK</span></span>|<span data-ttu-id="44f33-116">`OnComplete`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="44f33-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="44f33-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44f33-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44f33-118">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="44f33-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44f33-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44f33-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44f33-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="44f33-120">The call timed out.</span></span>|  
|<span data-ttu-id="44f33-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44f33-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44f33-122">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="44f33-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44f33-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44f33-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44f33-124">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="44f33-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44f33-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44f33-125">E_FAIL</span></span>|<span data-ttu-id="44f33-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="44f33-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44f33-127">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="44f33-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44f33-128">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44f33-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f33-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44f33-129">Remarks</span></span>  
 <span data-ttu-id="44f33-130">Jeśli host implementuje abstrakcję zakończenia We/Wy, CLR sprawia, że żądań We/Wy za pośrednictwem hosta za pomocą metody [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="44f33-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="44f33-131">Następnie wywołuje hosta `OnComplete` metodę, aby powiadomić środowiska uruchomieniowego o wynikach takich żądań.</span><span class="sxs-lookup"><span data-stu-id="44f33-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44f33-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44f33-132">Requirements</span></span>  
 <span data-ttu-id="44f33-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f33-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f33-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44f33-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44f33-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44f33-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44f33-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f33-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f33-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44f33-137">See Also</span></span>  
 [<span data-ttu-id="44f33-138">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="44f33-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="44f33-139">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="44f33-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="44f33-140">IHostThreadPoolManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="44f33-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)