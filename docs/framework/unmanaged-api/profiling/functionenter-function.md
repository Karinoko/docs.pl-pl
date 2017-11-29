---
title: "FunctionEnter — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="9008d-102">FunctionEnter — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9008d-102">FunctionEnter Function</span></span>
<span data-ttu-id="9008d-103">Powiadamia profilera, czy formant jest przekazywany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="9008d-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9008d-104">`FunctionEnter` Funkcja jest przestarzała w programie .NET Framework w wersji 2.0 i wykorzystanie przez niego będą powodować spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="9008d-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="9008d-105">Użyj [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zamiast tego działania.</span><span class="sxs-lookup"><span data-stu-id="9008d-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9008d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9008d-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9008d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9008d-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="9008d-108">[in] Identyfikator funkcji, do którego jest przekazywany formantu.</span><span class="sxs-lookup"><span data-stu-id="9008d-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9008d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9008d-109">Remarks</span></span>  
 <span data-ttu-id="9008d-110">`FunctionEnter` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="9008d-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="9008d-111">Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="9008d-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="9008d-112">Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9008d-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="9008d-113">Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).</span><span class="sxs-lookup"><span data-stu-id="9008d-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="9008d-114">Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9008d-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9008d-115">Implementacja `FunctionEnter` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9008d-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="9008d-116">Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="9008d-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9008d-117">Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionEnter` zwraca.</span><span class="sxs-lookup"><span data-stu-id="9008d-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="9008d-118">Ponadto `FunctionEnter` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="9008d-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9008d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9008d-119">Requirements</span></span>  
 <span data-ttu-id="9008d-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9008d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9008d-121">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9008d-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9008d-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9008d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9008d-123">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9008d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9008d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9008d-124">See Also</span></span>  
 [<span data-ttu-id="9008d-125">Functionenter2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="9008d-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="9008d-126">Functionleave2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="9008d-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="9008d-127">Functiontailcall2 — funkcja</span><span class="sxs-lookup"><span data-stu-id="9008d-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="9008d-128">SetEnterLeaveFunctionHooks2 — metoda</span><span class="sxs-lookup"><span data-stu-id="9008d-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="9008d-129">Statyczne funkcje globalne profilowania</span><span class="sxs-lookup"><span data-stu-id="9008d-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)