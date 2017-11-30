---
title: "ICorDebug::CanLaunchOrAttach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5bd657c73dfaf7643405b4b657edeffa6e33cd68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="aac42-102">ICorDebug::CanLaunchOrAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="aac42-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="aac42-103">Zwraca wartość wskazującą, czy jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego uruchamianie nowego procesu lub dołączanie do określonego istniejącego procesu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="aac42-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aac42-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aac42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aac42-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="aac42-106">[in] Identyfikator istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="aac42-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="aac42-107">[in] Przekazywanie `true` Jeśli jest planowane uruchamianie z włączonym debugowaniem Win32 lub dołączyć z debugowaniem Win32 włączone; w przeciwnym razie przekazania `false`.</span><span class="sxs-lookup"><span data-stu-id="aac42-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aac42-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aac42-108">Return Value</span></span>  
 <span data-ttu-id="aac42-109">S_OK Jeśli usług debugowania określić uruchamianie nowego procesu lub dołączanie do procesu danego jest to możliwe, podane informacje o bieżącej konfiguracji komputera i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="aac42-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="aac42-110">Możliwe wartości HRESULT to:</span><span class="sxs-lookup"><span data-stu-id="aac42-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="aac42-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aac42-111">S_OK</span></span>  
  
-   <span data-ttu-id="aac42-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="aac42-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="aac42-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="aac42-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="aac42-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="aac42-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac42-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aac42-115">Remarks</span></span>  
 <span data-ttu-id="aac42-116">Ta metoda jest wyłącznie informacyjne.</span><span class="sxs-lookup"><span data-stu-id="aac42-116">This method is purely informational.</span></span> <span data-ttu-id="aac42-117">Interfejs nie zakończy uruchomienie lub dołączanie do procesu, niezależnie od wartości zwróconych przez `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="aac42-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="aac42-118">Jeśli planujesz uruchamianie z włączonym debugowaniem Win32 lub Dołącz z włączonym debugowaniem Win32, Przekaż `true` dla `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="aac42-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="aac42-119">HRESULT zwrócony przez `CanLaunchOrAttach` mogą różnić się w przypadku użycia tej opcji.</span><span class="sxs-lookup"><span data-stu-id="aac42-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac42-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aac42-120">Requirements</span></span>  
 <span data-ttu-id="aac42-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aac42-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac42-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aac42-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aac42-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aac42-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aac42-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac42-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac42-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aac42-125">See Also</span></span>  
 [<span data-ttu-id="aac42-126">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="aac42-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)