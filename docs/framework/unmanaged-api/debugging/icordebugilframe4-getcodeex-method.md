---
title: Metoda ICorDebugILFrame4::GetCodeEx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetLocalVariableEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc80882353bd7a9861f4db79b83493d1cef7bfee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="e19e0-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="e19e0-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="e19e0-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e19e0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e19e0-104">Pobiera wskaźnik do kodu, który jest wykonywany tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e19e0-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e19e0-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e19e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e19e0-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e19e0-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy język pośredni (IL), zdefiniowany przez profiler ReJIT żądanie znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="e19e0-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="e19e0-108">[out] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e19e0-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e19e0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e19e0-109">Remarks</span></span>  
 <span data-ttu-id="e19e0-110">Ta metoda jest podobna do [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do kodu określonego przez profiler ReJIT żądanie.</span><span class="sxs-lookup"><span data-stu-id="e19e0-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="e19e0-111">Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); w wypadku metody został zinstrumentowany, jego IL nie będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="e19e0-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="e19e0-112">`ILCODE_REJIT_IL`Umożliwia debugera IL zdefiniowany przez profiler ReJIT żądanie dostępu do.</span><span class="sxs-lookup"><span data-stu-id="e19e0-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="e19e0-113">Jeśli nie ma instrumentacji IL, `ppCode` jest **null**, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="e19e0-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e19e0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e19e0-114">Requirements</span></span>  
 <span data-ttu-id="e19e0-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e19e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e19e0-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e19e0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e19e0-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e19e0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e19e0-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e19e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19e0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e19e0-119">See Also</span></span>  
 [<span data-ttu-id="e19e0-120">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="e19e0-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="e19e0-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e19e0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e19e0-122">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="e19e0-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)