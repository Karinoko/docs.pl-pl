---
title: "ICorDebugManagedCallback3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="5f89e-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5f89e-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="5f89e-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="5f89e-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f89e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5f89e-104">Methods</span></span>  
  
|<span data-ttu-id="5f89e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f89e-105">Method</span></span>|<span data-ttu-id="5f89e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5f89e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f89e-107">CustomNotification — metoda</span><span class="sxs-lookup"><span data-stu-id="5f89e-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="5f89e-108">Wskazuje zgłoszono powiadomienie włączony debuger niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5f89e-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f89e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f89e-109">Remarks</span></span>  
 <span data-ttu-id="5f89e-110">Ten interfejs jest logiczną rozszerzenie [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5f89e-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f89e-111">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="5f89e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f89e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f89e-112">Requirements</span></span>  
 <span data-ttu-id="5f89e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f89e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f89e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f89e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f89e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f89e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f89e-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f89e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f89e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f89e-117">See Also</span></span>  
 [<span data-ttu-id="5f89e-118">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="5f89e-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [<span data-ttu-id="5f89e-119">ICorDebugManagedCallback2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5f89e-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="5f89e-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="5f89e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5f89e-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5f89e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)