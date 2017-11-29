---
title: "IHostTask::SetCLRTask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="35812-102">IHostTask::SetCLRTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="35812-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="35812-103">Kojarzy `ICLRTask` wystąpienia z bieżącym [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="35812-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35812-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35812-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35812-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35812-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="35812-106">[in] Wskaźnik interfejsu do `ICLRTask` wystąpienia ma być skojarzona z bieżącym `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="35812-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35812-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="35812-107">Return Value</span></span>  
  
|<span data-ttu-id="35812-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35812-108">HRESULT</span></span>|<span data-ttu-id="35812-109">Opis</span><span class="sxs-lookup"><span data-stu-id="35812-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35812-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="35812-110">S_OK</span></span>|<span data-ttu-id="35812-111">`SetCLRTask`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="35812-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="35812-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35812-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35812-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="35812-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35812-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35812-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35812-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="35812-115">The call timed out.</span></span>|  
|<span data-ttu-id="35812-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35812-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35812-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="35812-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35812-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35812-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35812-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="35812-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35812-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35812-120">E_FAIL</span></span>|<span data-ttu-id="35812-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="35812-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35812-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="35812-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35812-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="35812-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35812-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35812-124">Remarks</span></span>  
 <span data-ttu-id="35812-125">Wywołania CLR `SetCLRTask` do skojarzenia `ICLRTask` wystąpienia z bieżącym `IHostTask` wystąpienia, która została utworzona przez wywołanie do [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="35812-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35812-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35812-126">Requirements</span></span>  
 <span data-ttu-id="35812-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35812-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35812-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35812-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35812-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35812-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35812-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35812-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35812-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35812-131">See Also</span></span>  
 [<span data-ttu-id="35812-132">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="35812-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="35812-133">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="35812-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="35812-134">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="35812-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="35812-135">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="35812-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)