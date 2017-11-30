---
title: "ICorDebugStepper::SetUnmappedStopMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetUnmappedStopMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 163a26ff38d0a4bbae5710d6d841ea29682a8984
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="0fbc5-102">ICorDebugStepper::SetUnmappedStopMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fbc5-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="0fbc5-103">Ustawia wartość, która określa typ Niemapowane kodu, w którym zostanie zatrzymanie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fbc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fbc5-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fbc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fbc5-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="0fbc5-106">[in] Wartość cordebugunmappedstop — wyliczenie, która określa typ Niemapowane kodu, w której debuger będzie zatrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="0fbc5-107">Wartość domyślna to STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="0fbc5-108">Wartość STOP_UNMANAGED jest prawidłowa tylko z debugowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fbc5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fbc5-109">Remarks</span></span>  
 <span data-ttu-id="0fbc5-110">Gdy debuger znajduje się w czasie kompilacji (JIT), który nie ma odpowiedniego mapowania na język pośredni firmy Microsoft (MSIL), zatrzymuje wykonywanie, jeśli została ustawiona flaga określenie typu Niemapowane kodu; w przeciwnym razie krok w sposób niewidoczny dla użytkownika jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="0fbc5-111">Jeśli debuger nie używa stepper wprowadzenia metody, następnie go nie zawsze Przekrocz nad Niemapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="0fbc5-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fbc5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fbc5-112">Requirements</span></span>  
 <span data-ttu-id="0fbc5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fbc5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fbc5-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fbc5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fbc5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fbc5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fbc5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fbc5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>