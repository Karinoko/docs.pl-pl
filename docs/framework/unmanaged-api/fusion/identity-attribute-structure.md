---
title: "IDENTITY_ATTRIBUTE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="236a9-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="236a9-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="236a9-103">Zawiera informacje o atrybutach metadane dotyczące [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="236a9-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="236a9-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="236a9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="236a9-105">Members</span></span>  
  
|<span data-ttu-id="236a9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="236a9-106">Member</span></span>|<span data-ttu-id="236a9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="236a9-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="236a9-108">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera przestrzeń nazw atrybutu jest w.</span><span class="sxs-lookup"><span data-stu-id="236a9-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="236a9-109">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="236a9-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="236a9-110">Wskaźnik na ciąg znaków zakończony znakiem null zawierającym wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="236a9-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236a9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="236a9-111">Remarks</span></span>  
 <span data-ttu-id="236a9-112">`IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźniki do ciągów znaków zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="236a9-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="236a9-113">Te trzy ciągi opisano jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="236a9-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="236a9-114">Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="236a9-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="236a9-115">`IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiadający mu `IDENTITY_ATTRIBUTE_BLOB` przesunięcia na trzy ciągi, na liście wymieniono struktury `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="236a9-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236a9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="236a9-116">Requirements</span></span>  
 <span data-ttu-id="236a9-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236a9-118">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="236a9-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="236a9-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236a9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="236a9-120">See Also</span></span>  
 [<span data-ttu-id="236a9-121">IDefinitionIdentity — interfejs</span><span class="sxs-lookup"><span data-stu-id="236a9-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="236a9-122">Identity_attribute_blob — struktura</span><span class="sxs-lookup"><span data-stu-id="236a9-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="236a9-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="236a9-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)