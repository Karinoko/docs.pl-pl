---
title: ICorDebugType Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2871b406bb9da84d20d7c526ad4a703baae409
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422874"
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
Reprezentuje typ, podstawowe lub złożonych (który jest zdefiniowane przez użytkownika). Jeśli typ jest rodzajowy, `ICorDebugType` reprezentuje wystąpień typu ogólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateTypeParameters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Pobiera wskaźnika interfejsu do ICorDebugTypeEnum, który odwołuje się do ogólnego <xref:System.Type> parametrów klasy odwołuje się to `ICorDebugType`.|  
|[GetBase, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Pobiera wskaźnika interfejsu do `ICorDebugType` , która odwołuje się klasę podstawową klasy odwołuje się to `ICorDebugType`, jeśli taka istnieje.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Pobiera wskaźnika interfejsu do ICorDebugClass, który odwołuje się do konstruktora typu `ICorDebugType`.|  
|[GetFirstTypeParameter, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Pobiera wskaźnika interfejsu do `ICorDebugType` , która odwołuje się pierwszy ogólny <xref:System.Type> parametr dla konstruktora klasy odwołuje się to `ICorDebugType`.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Pobiera liczbę wymiarów w typie tablicy.|  
|[GetStaticFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Pobiera token w ramce stosu określonego wskaźnika interfejsu do ICorDebugValue zawierający wartość pola statycznego odwołuje się określonego pola.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Pobiera wartość CorElementType, która opisuje typ macierzysty środowisko uruchomieniowe języka wspólnego <xref:System.Type> odwołuje się to `ICorDebugType`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ jest rodzajowy, `ICorDebugClass` reprezentuje typ bez wystąpień. `ICorDebugType` Interfejsu reprezentuje typu ogólnego. Na przykład Hashtable\<K, V > może być reprezentowany przez `ICorDebugClass`, podczas gdy Hashtable\<Int32, String > może być reprezentowany przez `ICorDebugType`.  
  
 Typy ogólne nie są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`. Drugim interfejs został wprowadzony w programie .NET Framework w wersji 2.0 na wypadek wystąpienia typu.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
