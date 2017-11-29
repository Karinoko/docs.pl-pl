---
title: Wyliczenie CorDebugPlatform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugPlatformEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugPlatformEnum
helpviewer_keywords: CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52842d40895a658ec9dbb1263f18c48ec999a0ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="0e91d-102">Wyliczenie CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="0e91d-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="0e91d-103">Udostępnia wartości platform docelowych, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0e91d-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e91d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e91d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="0e91d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0e91d-105">Members</span></span>  
  
|<span data-ttu-id="0e91d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0e91d-106">Member</span></span>|<span data-ttu-id="0e91d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0e91d-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0e91d-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="0e91d-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="0e91d-109">Platforma docelowa jest sprzęt Intel x86 z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="0e91d-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="0e91d-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="0e91d-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="0e91d-111">Platforma docelowa jest sprzęt AMD64 lub Intel EM64T z systemem Windows 64-bitowym.</span><span class="sxs-lookup"><span data-stu-id="0e91d-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="0e91d-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="0e91d-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="0e91d-113">Platforma docelowa jest sprzęt Intel IA-64 z systemem Windows 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="0e91d-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="0e91d-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="0e91d-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="0e91d-115">Platforma docelowa jest systemu operacyjnego dla komputerów Macintosh PowerPC sprzętu.</span><span class="sxs-lookup"><span data-stu-id="0e91d-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="0e91d-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="0e91d-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="0e91d-117">Platforma docelowa jest Macintosh systemu operacyjnego na Intel x86 sprzętu.</span><span class="sxs-lookup"><span data-stu-id="0e91d-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="0e91d-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="0e91d-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="0e91d-119">Platforma docelowa jest Macintosh systemu operacyjnego na sprzęcie ARM systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0e91d-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="0e91d-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="0e91d-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="0e91d-121">Platforma docelowa jest Macintosh systemu operacyjnego na sprzęcie AMD64.</span><span class="sxs-lookup"><span data-stu-id="0e91d-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e91d-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e91d-122">Requirements</span></span>  
 <span data-ttu-id="0e91d-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e91d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e91d-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e91d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e91d-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e91d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e91d-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e91d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="0e91d-127">`CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` elementy są dostępne w programie .NET Framework 4.5.2 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0e91d-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e91d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e91d-128">See Also</span></span>  
 [<span data-ttu-id="0e91d-129">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0e91d-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)