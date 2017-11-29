---
title: "Funkcja Beingenumeration (niezarządzany wykaz interfejsów API)"
description: "Funkcja Beingenumeration resetuje moduł wyliczający na początku wyliczenia"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12a742774bff22030bdfaaa34e431059e016a4bf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="d74a3-103">Funkcja Beingenumeration</span><span class="sxs-lookup"><span data-stu-id="d74a3-103">BeginEnumeration function</span></span>
<span data-ttu-id="d74a3-104">Moduł wyliczający resetuje do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d74a3-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d74a3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d74a3-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="d74a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d74a3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d74a3-107">[in] Ten parametr nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="d74a3-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="d74a3-108">`ptr`[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d74a3-108">`ptr` [in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="d74a3-109">[in] Bitowe połączenie flagi lub wartości opisanych w [uwagi](#remarks) sekcji, która kontroluje właściwości zawarte w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="d74a3-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d74a3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d74a3-110">Return value</span></span>

<span data-ttu-id="d74a3-111">Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d74a3-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d74a3-112">Stała</span><span class="sxs-lookup"><span data-stu-id="d74a3-112">Constant</span></span>  |<span data-ttu-id="d74a3-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="d74a3-113">Value</span></span>  |<span data-ttu-id="d74a3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d74a3-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d74a3-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d74a3-115">0x80041008</span></span> | <span data-ttu-id="d74a3-116">Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony.</span><span class="sxs-lookup"><span data-stu-id="d74a3-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="d74a3-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="d74a3-117">0x8004101d</span></span> | <span data-ttu-id="d74a3-118">Drugie wywołanie `BeginEnumeration` został utworzony bez wywołania pośredniczące [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d74a3-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d74a3-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d74a3-119">0x80041006</span></span> | <span data-ttu-id="d74a3-120">Można rozpocząć nowego wyliczenia jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="d74a3-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d74a3-121">0</span><span class="sxs-lookup"><span data-stu-id="d74a3-121">0</span></span> | <span data-ttu-id="d74a3-122">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d74a3-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d74a3-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d74a3-123">Remarks</span></span>

<span data-ttu-id="d74a3-124">Ta funkcja jest zawijana wywołanie [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="d74a3-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="d74a3-125">Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d74a3-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="d74a3-126">Możesz łączyć jedną flagę z każdej grupy z flagą dowolnego z innej grupy.</span><span class="sxs-lookup"><span data-stu-id="d74a3-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="d74a3-127">Jednak flagi z tej samej grupy wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="d74a3-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="d74a3-128">**Grupa 1**</span><span class="sxs-lookup"><span data-stu-id="d74a3-128">**Group 1**</span></span>

|<span data-ttu-id="d74a3-129">Stała</span><span class="sxs-lookup"><span data-stu-id="d74a3-129">Constant</span></span>  |<span data-ttu-id="d74a3-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="d74a3-130">Value</span></span>  |<span data-ttu-id="d74a3-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d74a3-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="d74a3-132">0x4</span><span class="sxs-lookup"><span data-stu-id="d74a3-132">0x4</span></span> | <span data-ttu-id="d74a3-133">Zawierają właściwości, które tworzą tylko klucz.</span><span class="sxs-lookup"><span data-stu-id="d74a3-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="d74a3-134">0x8</span><span class="sxs-lookup"><span data-stu-id="d74a3-134">0x8</span></span> | <span data-ttu-id="d74a3-135">Zawierają właściwości, które są tylko odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d74a3-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="d74a3-136">**Grupa 2**</span><span class="sxs-lookup"><span data-stu-id="d74a3-136">**Group 2**</span></span>

<span data-ttu-id="d74a3-137">Stała</span><span class="sxs-lookup"><span data-stu-id="d74a3-137">Constant</span></span>  |<span data-ttu-id="d74a3-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="d74a3-138">Value</span></span>  |<span data-ttu-id="d74a3-139">Opis</span><span class="sxs-lookup"><span data-stu-id="d74a3-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="d74a3-140">0x30</span><span class="sxs-lookup"><span data-stu-id="d74a3-140">0x30</span></span> | <span data-ttu-id="d74a3-141">Ogranicz wyliczenie tylko właściwości systemu.</span><span class="sxs-lookup"><span data-stu-id="d74a3-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="d74a3-142">0x40</span><span class="sxs-lookup"><span data-stu-id="d74a3-142">0x40</span></span> | <span data-ttu-id="d74a3-143">Dołącz lokalnych i propagowany właściwości, z wyłączeniem właściwości systemu z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d74a3-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="d74a3-144">Dla klas:</span><span class="sxs-lookup"><span data-stu-id="d74a3-144">For classes:</span></span>

<span data-ttu-id="d74a3-145">Stała</span><span class="sxs-lookup"><span data-stu-id="d74a3-145">Constant</span></span>  |<span data-ttu-id="d74a3-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="d74a3-146">Value</span></span>  |<span data-ttu-id="d74a3-147">Opis</span><span class="sxs-lookup"><span data-stu-id="d74a3-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="d74a3-148">0x100</span><span class="sxs-lookup"><span data-stu-id="d74a3-148">0x100</span></span> | <span data-ttu-id="d74a3-149">Ogranicz wyliczenia właściwości zastąpione w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="d74a3-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="d74a3-150">0x100</span><span class="sxs-lookup"><span data-stu-id="d74a3-150">0x100</span></span> | <span data-ttu-id="d74a3-151">Ogranicz wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="d74a3-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="d74a3-152">0x300</span><span class="sxs-lookup"><span data-stu-id="d74a3-152">0x300</span></span> | <span data-ttu-id="d74a3-153">A zamaskować (zamiast flagę) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy albo `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d74a3-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d74a3-154">0x10</span><span class="sxs-lookup"><span data-stu-id="d74a3-154">0x10</span></span> | <span data-ttu-id="d74a3-155">Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d74a3-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d74a3-156">0x20</span><span class="sxs-lookup"><span data-stu-id="d74a3-156">0x20</span></span> | <span data-ttu-id="d74a3-157">Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d74a3-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="d74a3-158">Dla wystąpień:</span><span class="sxs-lookup"><span data-stu-id="d74a3-158">For instances:</span></span>

<span data-ttu-id="d74a3-159">Stała</span><span class="sxs-lookup"><span data-stu-id="d74a3-159">Constant</span></span>  |<span data-ttu-id="d74a3-160">Wartość</span><span class="sxs-lookup"><span data-stu-id="d74a3-160">Value</span></span>  |<span data-ttu-id="d74a3-161">Opis</span><span class="sxs-lookup"><span data-stu-id="d74a3-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d74a3-162">0x10</span><span class="sxs-lookup"><span data-stu-id="d74a3-162">0x10</span></span> | <span data-ttu-id="d74a3-163">Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy.</span><span class="sxs-lookup"><span data-stu-id="d74a3-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d74a3-164">0x20</span><span class="sxs-lookup"><span data-stu-id="d74a3-164">0x20</span></span> | <span data-ttu-id="d74a3-165">Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d74a3-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="d74a3-166">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d74a3-166">Requirements</span></span>  
 <span data-ttu-id="d74a3-167">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d74a3-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74a3-168">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d74a3-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d74a3-169">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d74a3-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74a3-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d74a3-170">See also</span></span>  
[<span data-ttu-id="d74a3-171">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="d74a3-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)