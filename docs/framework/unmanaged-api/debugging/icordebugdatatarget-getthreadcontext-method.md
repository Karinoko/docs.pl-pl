---
title: "ICorDebugDataTarget::GetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetThreadContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 543956bb42d7477456426d7327f14b059b23d759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="16ed9-102">ICorDebugDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="16ed9-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="16ed9-103">Zwraca bieżący kontekst wątku określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="16ed9-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ed9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16ed9-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16ed9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16ed9-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="16ed9-106">[in] Identyfikator wątku, w którego kontekście ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="16ed9-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="16ed9-107">Identyfikator jest zdefiniowany przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="16ed9-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="16ed9-108">[in] Bitowe połączenie flag zależny od platformy, które wskazują części kontekście powinny być do odczytu.</span><span class="sxs-lookup"><span data-stu-id="16ed9-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="16ed9-109">[in] Rozmiar `pContext`.</span><span class="sxs-lookup"><span data-stu-id="16ed9-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="16ed9-110">[out] Bufor przechowywania kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="16ed9-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16ed9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16ed9-111">Remarks</span></span>  
 <span data-ttu-id="16ed9-112">Na platformach Windows `pContext` musi być `CONTEXT` Struktura (zdefiniowane w pliku WinNT.h), która jest odpowiednia dla typu maszyny, określony przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="16ed9-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="16ed9-113">`contextFlags`musi mieć takie same wartości jak `ContextFlags` pole `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="16ed9-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="16ed9-114">`CONTEXT` Struktura jest specyficznych dla procesora, zobacz szczegóły w pliku pliku WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="16ed9-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16ed9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16ed9-115">Requirements</span></span>  
 <span data-ttu-id="16ed9-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16ed9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16ed9-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16ed9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16ed9-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16ed9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16ed9-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16ed9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16ed9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16ed9-120">See Also</span></span>  
 [<span data-ttu-id="16ed9-121">ICorDebugDataTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="16ed9-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="16ed9-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="16ed9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="16ed9-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="16ed9-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)