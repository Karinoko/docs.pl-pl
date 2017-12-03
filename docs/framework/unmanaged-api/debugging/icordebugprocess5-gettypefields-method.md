---
title: "ICorDebugProcess5::GetTypeFields — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields — Metoda
Zawiera informacje o polach, które należą do typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator typu, których pola informacje są pobierane.  
  
 `celt`  
 [in] Liczba [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, których informacje pole ma być pobrana.  
  
 `fields`  
 [out] Tablica [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, które dostarczają informacji o polach, które należą do tego typu.  
  
 `pceltNeeded`  
 [out] Wskaźnik do liczby [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów uwzględnionych w `fields`.  
  
## <a name="remarks"></a>Uwagi  
 `celt` Parametr, który określa numer pola, którego metoda używa do wypełniania informacji o polu `fields`, powinna być zgodna z wartością `COR_TYPE_LAYOUT::numFields` pola.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess5 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)