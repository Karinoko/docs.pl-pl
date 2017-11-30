---
title: "ICorDebugMergedAssemblyRecord::GetPublicKeyToken — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c286981def6f12f8e5b8fa5397f23535d4d4623
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="f66a8-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken — metoda</span><span class="sxs-lookup"><span data-stu-id="f66a8-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="f66a8-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f66a8-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f66a8-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f66a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f66a8-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="f66a8-106">[in] Maksymalna liczba bajtów w `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f66a8-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="f66a8-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f66a8-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="f66a8-108">[out] Wskaźnik do tablicy typu byte, który zawiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f66a8-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66a8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f66a8-109">Remarks</span></span>  
 <span data-ttu-id="f66a8-110">Token klucza publicznego zestawu jest ostatnich ośmiu bajtów skrótu SHA1 jego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f66a8-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f66a8-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f66a8-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f66a8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f66a8-112">Requirements</span></span>  
 <span data-ttu-id="f66a8-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f66a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f66a8-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f66a8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f66a8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f66a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f66a8-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f66a8-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66a8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f66a8-117">See Also</span></span>  
 [<span data-ttu-id="f66a8-118">Interfejs ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="f66a8-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="f66a8-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f66a8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)