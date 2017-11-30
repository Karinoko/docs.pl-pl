---
title: "CLRRuntimeHost — Klasa coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="101bf-102">CLRRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="101bf-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="101bf-103">Zawiera interfejsy zarządzania wykonywanie kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="101bf-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="101bf-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="101bf-105">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="101bf-105">Interfaces</span></span>  
  
|<span data-ttu-id="101bf-106">Interface</span><span class="sxs-lookup"><span data-stu-id="101bf-106">Interface</span></span>|<span data-ttu-id="101bf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="101bf-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="101bf-108">ICLRRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="101bf-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="101bf-109">Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="101bf-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="101bf-110">ICLRValidator — interfejs</span><span class="sxs-lookup"><span data-stu-id="101bf-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="101bf-111">Udostępnia metody weryfikacji przenośnych obrazy wykonywalne oraz szczegółowe raportowanie błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="101bf-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="101bf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="101bf-112">Requirements</span></span>  
 <span data-ttu-id="101bf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101bf-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="101bf-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="101bf-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="101bf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="101bf-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101bf-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="101bf-117">See Also</span></span>  
 [<span data-ttu-id="101bf-118">Współklasy hostingu</span><span class="sxs-lookup"><span data-stu-id="101bf-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)