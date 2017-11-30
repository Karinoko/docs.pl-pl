---
title: "Funkcja ResetSecurity (niezarządzany wykaz interfejsów API)"
description: "Funkcja ResetSecurity przypisuje token personifikacji bieżącego wątku."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2790012a429c6a0551d8321a80570f3f8be2142b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="03a7b-103">Funkcja ResetSecurity</span><span class="sxs-lookup"><span data-stu-id="03a7b-103">ResetSecurity function</span></span>
<span data-ttu-id="03a7b-104">Przypisuje token personifikacji dostarczony do bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="03a7b-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="03a7b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03a7b-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="03a7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03a7b-106">Parameters</span></span>

`token`  
<span data-ttu-id="03a7b-107">[in] Token personifikacji do skojarzenia z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="03a7b-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="03a7b-108">Wartość może być `null`.</span><span class="sxs-lookup"><span data-stu-id="03a7b-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="03a7b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03a7b-109">Return value</span></span>

<span data-ttu-id="03a7b-110">Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="03a7b-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="03a7b-111">Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błędu.</span><span class="sxs-lookup"><span data-stu-id="03a7b-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="03a7b-112">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="03a7b-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="03a7b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03a7b-113">Requirements</span></span>  
 <span data-ttu-id="03a7b-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a7b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a7b-115">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="03a7b-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="03a7b-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03a7b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a7b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03a7b-117">See also</span></span>  
[<span data-ttu-id="03a7b-118">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="03a7b-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)