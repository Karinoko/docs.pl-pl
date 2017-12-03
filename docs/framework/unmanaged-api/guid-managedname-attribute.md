---
title: "GUID_ManagedName — Atrybut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GUID_ManagedName
api_location: alink.dll
api_type: COM
f1_keywords: GUID_ManagedName
helpviewer_keywords: GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf0facaa1107fcc6dcd93cbf0252024dc6f73b0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName — Atrybut
Definiuje atrybut niestandardowy interfejs, który określa nazwę zarządzanego przestrzeni nazw dla składnika modelu (COM) biblioteki.  
  
## <a name="syntax"></a>Składnia  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Nazwa zarządzanego przestrzeń nazw dla biblioteki.  
  
## <a name="definition"></a>Definicja  
 `GUID_ManagedName`zdefiniowano w Cor.h w następujący sposób:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Uwagi  
 Atrybut niestandardowy interfejs definiuje metadanych obiektu w bibliotece typów.  
  
 Użyj <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> pobrać zarządzanych nazwa atrybutu.  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty interfejsu](/cpp/windows/interface-attributes) w programie Visual C++ odwoływać się z dokumentacją.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono definicję biblioteki przy użyciu `GUID_ManagedName` atrybutu.  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Cor.h