---
title: "ICorDebugHeapValue2::CreateHandle — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7feef9af174a63976729f91b5a0b4967fea55b23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="c5f30-102">ICorDebugHeapValue2::CreateHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5f30-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="c5f30-103">Tworzy dojście o określonym typie dla wartości sterty reprezentowany przez ten obiekt ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="c5f30-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5f30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5f30-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5f30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5f30-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="c5f30-106">[in] Wartość wyliczenia CorDebugHandleType, która określa typ dojścia do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="c5f30-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="c5f30-107">[out] Wskaźnik do adres obiektu ICorDebugHandleValue reprezentujący nowy uchwyt dla tej wartości stosu.</span><span class="sxs-lookup"><span data-stu-id="c5f30-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5f30-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5f30-108">Remarks</span></span>  
 <span data-ttu-id="c5f30-109">Dojście zostaną utworzone w domenie aplikacji, które jest skojarzone z wartością sterty i staną się nieprawidłowe, jeśli domena aplikacji zostanie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="c5f30-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="c5f30-110">Wiele wywołań tej funkcji dla tej samej wartości sterty spowoduje utworzenie wielu dojść.</span><span class="sxs-lookup"><span data-stu-id="c5f30-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="c5f30-111">Ponieważ uchwytów wpływ na wydajność modułu zbierającego elementy bezużyteczne, debuger ograniczyć się do stosunkowo małej liczby dojść (około 256), które są aktywne w czasie.</span><span class="sxs-lookup"><span data-stu-id="c5f30-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5f30-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5f30-112">Requirements</span></span>  
 <span data-ttu-id="c5f30-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5f30-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f30-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5f30-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5f30-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5f30-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5f30-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f30-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>