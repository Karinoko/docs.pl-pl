---
title: "CorErrorIfEmitOutOfOrder — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorErrorIfEmitOutOfOrder
api_location: mscoree.dll
api_type: COM
f1_keywords: CorErrorIfEmitOutOfOrder
helpviewer_keywords: CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2cf80375622912c6bb9a59696f37aed2d594253
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="61fbf-102">CorErrorIfEmitOutOfOrder — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="61fbf-102">CorErrorIfEmitOutOfOrder Enumeration</span></span>
<span data-ttu-id="61fbf-103">Zawiera wartości flagi, które określają warunki, w których ma być generowany metadanych jest emitowany poza kolejnością komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="61fbf-103">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61fbf-104">Syntax</span></span>  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="61fbf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="61fbf-105">Members</span></span>  
  
|<span data-ttu-id="61fbf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="61fbf-106">Member</span></span>|<span data-ttu-id="61fbf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="61fbf-107">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="61fbf-108">Wskazuje zachowanie domyślne, który nie generuje komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="61fbf-108">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="61fbf-109">Wskazuje, że kompilator nie powinna generować komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="61fbf-109">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="61fbf-110">Wskazuje, czy kompilator powinien generować komunikat o błędzie, gdy pola, właściwości, zdarzenia, metody lub parametru jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-110">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="61fbf-111">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy metoda jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-111">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="61fbf-112">Wskazuje, że kompilator powinien generować komunikat o błędzie, jeśli pole jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-112">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="61fbf-113">Wskazuje, że kompilator powinien generować komunikat o błędzie, jeśli parametr jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-113">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="61fbf-114">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy właściwość jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-114">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="61fbf-115">Wskazuje, że kompilator powinien generować komunikat o błędzie, gdy zdarzenie jest emitowany poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="61fbf-115">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61fbf-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61fbf-116">Requirements</span></span>  
 <span data-ttu-id="61fbf-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61fbf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61fbf-118">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="61fbf-118">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="61fbf-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61fbf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fbf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61fbf-120">See Also</span></span>  
 [<span data-ttu-id="61fbf-121">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="61fbf-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)