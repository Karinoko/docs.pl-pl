---
title: "IHostIoCompletionManager::CreateIoCompletionPort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1942c34b0807b76bbe25aedc60b7b1c6fecc87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="642bf-102">IHostIoCompletionManager::CreateIoCompletionPort — Metoda</span><span class="sxs-lookup"><span data-stu-id="642bf-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="642bf-103">Żądania, hosta utworzyć nowego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="642bf-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="642bf-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="642bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="642bf-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="642bf-106">[out] Wskaźnik do dojścia do nowo utworzonej portu zakończenia We/Wy lub 0 (zero), jeśli nie można utworzyć portu.</span><span class="sxs-lookup"><span data-stu-id="642bf-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="642bf-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="642bf-107">Return Value</span></span>  
  
|<span data-ttu-id="642bf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="642bf-108">HRESULT</span></span>|<span data-ttu-id="642bf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="642bf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="642bf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="642bf-110">S_OK</span></span>|<span data-ttu-id="642bf-111">`CreateIoCompletionPort`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="642bf-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="642bf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="642bf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="642bf-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="642bf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="642bf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="642bf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="642bf-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="642bf-115">The call timed out.</span></span>|  
|<span data-ttu-id="642bf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="642bf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="642bf-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="642bf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="642bf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="642bf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="642bf-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="642bf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="642bf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="642bf-120">E_FAIL</span></span>|<span data-ttu-id="642bf-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="642bf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="642bf-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="642bf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="642bf-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="642bf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="642bf-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="642bf-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="642bf-125">Za mało pamięci nie była dostępna do przydzielenia do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="642bf-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642bf-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="642bf-126">Remarks</span></span>  
 <span data-ttu-id="642bf-127">Wywołania CLR `CreateIoCompletionPort` metody żądania, że host utworzyć nowego portu zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="642bf-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="642bf-128">Do tego portu, poprzez wywołanie tworzy ona powiązanie operacji We/Wy [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="642bf-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="642bf-129">Host raportuje stan ją do środowiska CLR, wywołując [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="642bf-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642bf-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="642bf-130">Requirements</span></span>  
 <span data-ttu-id="642bf-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="642bf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="642bf-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="642bf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="642bf-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="642bf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="642bf-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="642bf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642bf-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="642bf-135">See Also</span></span>  
 [<span data-ttu-id="642bf-136">ICLRIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="642bf-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="642bf-137">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="642bf-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)