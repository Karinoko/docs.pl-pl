---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="24845-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda</span><span class="sxs-lookup"><span data-stu-id="24845-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="24845-103">Zwraca zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="24845-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24845-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24845-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24845-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24845-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="24845-106">[out] Zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="24845-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="24845-107">[out] Ile razy ten wątek musi zwolnić blokady przed zwróceniem do trwa bez właściciela.</span><span class="sxs-lookup"><span data-stu-id="24845-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24845-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24845-108">Return Value</span></span>  
 <span data-ttu-id="24845-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="24845-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="24845-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24845-110">HRESULT</span></span>|<span data-ttu-id="24845-111">Opis</span><span class="sxs-lookup"><span data-stu-id="24845-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24845-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="24845-112">S_OK</span></span>|<span data-ttu-id="24845-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="24845-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="24845-114">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="24845-114">S_FALSE</span></span>|<span data-ttu-id="24845-115">Nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="24845-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="24845-116">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="24845-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24845-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24845-117">Remarks</span></span>  
 <span data-ttu-id="24845-118">Jeśli zarządzanego wątku jest właścicielem blokady monitora dla tego obiektu:</span><span class="sxs-lookup"><span data-stu-id="24845-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="24845-119">Metoda zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="24845-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="24845-120">Obiekt wątku jest prawidłowy, dopóki kończy działanie wątku.</span><span class="sxs-lookup"><span data-stu-id="24845-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="24845-121">Jeśli nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie `ppThread` i `pAcquisitionCount` nie uległy zmianie, a metoda zwraca wartości S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="24845-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="24845-122">Jeśli `ppThread` lub `pAcquisitionCount` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="24845-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="24845-123">W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, które, wątek jest właścicielem blokady monitora w tym obiekcie metoda zwraca HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="24845-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24845-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24845-124">Requirements</span></span>  
 <span data-ttu-id="24845-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24845-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24845-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24845-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24845-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24845-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24845-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24845-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24845-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24845-129">See Also</span></span>  
 [<span data-ttu-id="24845-130">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="24845-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="24845-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="24845-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)