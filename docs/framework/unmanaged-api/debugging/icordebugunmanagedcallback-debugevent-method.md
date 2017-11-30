---
title: "ICorDebugUnmanagedCallback::DebugEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 008ae1bd1a5774604bf2c0f196352dcf07da6ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="80d04-102">ICorDebugUnmanagedCallback::DebugEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="80d04-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="80d04-103">Powiadamia debugera natywnego zdarzenia uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="80d04-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d04-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80d04-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80d04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80d04-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="80d04-106">[in] Wskaźnik do natywnej zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="80d04-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="80d04-107">[in] `true`, jeżeli interakcji z stan procesu zarządzanego nie jest możliwe po wystąpieniu zdarzenia niezarządzane, dopóki wywołania debugera [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="80d04-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80d04-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80d04-108">Remarks</span></span>  
 <span data-ttu-id="80d04-109">Jeśli debugowany wątek wątku Win32, nie należy używać żadnych członków środowiska Win32, debugowanie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="80d04-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="80d04-110">Możesz wywołać `ICorDebugController::Continue` tylko w wątku Win32 i tylko wtedy, gdy kontynuowanie poza zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="80d04-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="80d04-111">`DebugEvent` Wywołania zwrotnego nie jest zgodna z standardowych zasad dla wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="80d04-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="80d04-112">Podczas wywoływania `DebugEvent`, proces zostanie w surowych, stanem zatrzymany debugowania systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="80d04-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="80d04-113">Proces nie będą synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="80d04-113">The process will not be synchronized.</span></span> <span data-ttu-id="80d04-114">Automatycznie wprowadzi zsynchronizowane stan, gdy jest to niezbędne do spełnienia żądania informacji o kodu zarządzanego, co może spowodować innych zagnieżdżonych `DebugEvent` wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="80d04-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="80d04-115">Wywołanie [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) dla procesu, aby zignorować zdarzenie wyjątku przed kontynuowaniem procesu.</span><span class="sxs-lookup"><span data-stu-id="80d04-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="80d04-116">Wywołanie tej metody wysyła żądanie Kontynuuj DBG_CONTINUE zamiast DBG_EXCEPTION_NOT_HANDLED i automatycznie usuwa punkty przerwania poza pasmem i wyjątków pojedynczy krok.</span><span class="sxs-lookup"><span data-stu-id="80d04-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="80d04-117">Zdarzenia poza pasmem są dostępne w dowolnym momencie, nawet wtedy, gdy debugowanej aplikacji pojawia się zatrzymana i zaległych zdarzeń wewnątrzpasmowe już istnieje.</span><span class="sxs-lookup"><span data-stu-id="80d04-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="80d04-118">W programie .NET Framework w wersji 2.0 debuger powinien natychmiast kontynuować mimo zdarzenie punktu przerwania poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="80d04-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="80d04-119">Debuger powinien być używany [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) i [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody do dodawania i usuwania punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="80d04-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="80d04-120">Te metody pomija wszystkie punkty przerwania poza pasmem automatycznie.</span><span class="sxs-lookup"><span data-stu-id="80d04-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="80d04-121">W związku z tym punkty przerwania tylko poza pasmem, które get wysyłane powinna być pierwotnych punktów kontrolnych, które znajdują się już w strumieniu instrukcji, takie jak wywołania Win32 `DebugBreak` funkcji.</span><span class="sxs-lookup"><span data-stu-id="80d04-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="80d04-122">Nie należy próbować użyć `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), lub wszystkich innych członków [API — debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md).</span><span class="sxs-lookup"><span data-stu-id="80d04-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d04-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80d04-123">Requirements</span></span>  
 <span data-ttu-id="80d04-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d04-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d04-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80d04-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80d04-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80d04-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80d04-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d04-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d04-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80d04-128">See Also</span></span>  
 [<span data-ttu-id="80d04-129">ICorDebugUnmanagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="80d04-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)