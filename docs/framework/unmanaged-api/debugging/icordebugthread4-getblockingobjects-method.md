---
title: ICorDebugThread4::GetBlockingObjects — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55251a3adfa67c1dac3b6952a37217e3eeb4c04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421908"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects — Metoda
Udostępnia w kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Wskaźnik do kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszym elementem w wyliczeniu zwrócony odpowiada pierwszy struktury, która blokuje wątku. Drugi element odnosi się do blokowania elementu, który jest napotkała podczas uruchamiania wywołanie asynchroniczne procedury (APC) w przypadku zablokowania pierwszego i tak dalej.  
  
 Wyliczanie jest prawidłowa tylko na czas trwania bieżącego stanu zsynchronizowane.  
  
 Ta metoda musi zostać wywołany, gdy obiekt debugowany znajduje się w stanie zsynchronizowane.  
  
 Jeśli `ppBlockingObjectEnum` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.  
  
 Jeśli wątek został zablokowany i nie może być określony błąd, metoda zwraca wartość HRESULT, która wskazuje błąd; w przeciwnym razie zwraca wartość S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
