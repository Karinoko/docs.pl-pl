---
title: "Hosting — Interfejsy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3cad92c204fa10f72d7a9a61460f1234206cb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="2a3c5-102">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2a3c5-102">Hosting Interfaces</span></span>
<span data-ttu-id="2a3c5-103">W tej sekcji opisano interfejsów, które niezarządzanych hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w swoich aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="2a3c5-104">Interfejsy hostingu środowiska .NET Framework w wersji 2.0 zastępują interfejsy .NET Framework w wersji 1.0, 1.1.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="2a3c5-105">Brak istotnych różnic między dwoma zestawami interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="2a3c5-106">Mieszanie ich może spowodować nieoczekiwane zachowanie i nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="2a3c5-107">Wersje programu .NET Framework 3.0 i 3.5 używać interfejsów hostingu programu .NET Framework w wersji 2.0, a nie znajdą się wszystkie funkcje hostingu.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="2a3c5-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Interfejsy hostingu zastępują interfejsy .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="2a3c5-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2a3c5-109">In This Section</span></span>  
 [<span data-ttu-id="2a3c5-110">Przestarzałe hostingu interfejsy i współklasy środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2a3c5-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="2a3c5-111">Opisuje interfejsy hostingu, wprowadzona w wersji systemu .NET Framework 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="2a3c5-112">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2a3c5-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="2a3c5-113">Opisuje interfejsy hostingu, wprowadzone w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="2a3c5-114">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="2a3c5-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="2a3c5-115">Opisuje interfejsy hostingu, wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a3c5-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a3c5-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2a3c5-116">Related Sections</span></span>  
 [<span data-ttu-id="2a3c5-117">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="2a3c5-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="2a3c5-118">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2a3c5-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="2a3c5-119">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2a3c5-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="2a3c5-120">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="2a3c5-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="2a3c5-121">Hosting</span><span class="sxs-lookup"><span data-stu-id="2a3c5-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="2a3c5-122">Hosty w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="2a3c5-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)