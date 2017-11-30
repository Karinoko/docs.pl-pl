---
title: "ICorProfilerInfo2::GetCodeInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetCodeInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c2526c286e4014b32e63ec34f9d212a5f657756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="6dc2c-102">ICorProfilerInfo2::GetCodeInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="6dc2c-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="6dc2c-103">Pobiera zakres kodu natywnego skojarzonego z określonym `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dc2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dc2c-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6dc2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dc2c-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="6dc2c-106">[in] Identyfikator funkcji, z którym jest skojarzona kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="6dc2c-107">[in] Rozmiar `codeInfos` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="6dc2c-108">[out] Wskaźnik do łączna liczba [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="6dc2c-109">[out] Bufor podany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="6dc2c-110">Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktury, z których każdy zawiera opis blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dc2c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dc2c-111">Remarks</span></span>  
 <span data-ttu-id="6dc2c-112">Zakresy są sortowane w kolejności rosnącej przesunięcie język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="6dc2c-113">Po `GetCodeInfo2` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor był wystarczająco duży, aby pomieścić wszystkie `COR_PRF_CODE_INFO` struktury.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="6dc2c-114">Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="6dc2c-115">Jeśli `cCodeInfos` podzielonej przez rozmiar `COR_PRF_CODE_INFO` struktury jest mniejszy niż `pcCodeInfos`, Przydziel większy `codeInfos` buforu, zaktualizuj `cCodeInfos` z nowej, większy rozmiar i wywołanie `GetCodeInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="6dc2c-116">Alternatywnie można wywołać `GetCodeInfo2` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="6dc2c-117">Następnie można ustawić `codeInfos` buforu rozmiar, aby wartość zwracana w `pcCodeInfos`, pomnożonych przez rozmiar `COR_PRF_CODE_INFO` struktury i wywołanie `GetCodeInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="6dc2c-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dc2c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dc2c-118">Requirements</span></span>  
 <span data-ttu-id="6dc2c-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dc2c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dc2c-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dc2c-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dc2c-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dc2c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dc2c-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc2c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc2c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dc2c-123">See Also</span></span>  
 [<span data-ttu-id="6dc2c-124">GetCodeInfo3 — metoda</span><span class="sxs-lookup"><span data-stu-id="6dc2c-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [<span data-ttu-id="6dc2c-125">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6dc2c-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="6dc2c-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="6dc2c-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6dc2c-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="6dc2c-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)