---
title: ICorDebugThread3::GetActiveInternalFrames — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ac87de35478e5eabdc8cdc3568baf2086923e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423026"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames — Metoda
Zwraca tablicę wewnętrzny ramki ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cInternalFrames`  
 [in] Liczba ramek wewnętrznego w `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Wskaźnik do `ULONG32` zawierającą numer wewnętrzny ramek na stosie.  
  
 `ppInternalFrames`  
 [w, out] Wskaźnik do adresu tablicy wewnętrznej ramek na stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiekt został utworzony pomyślnie.|  
|E_INVALIDARG|`cInternalFrames` nie jest równa zero i `ppInternalFrames` jest `null`, lub `pcInternalFrames` jest `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` jest mniejszy niż liczba ramek wewnętrznego.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Wewnętrzny ramki są struktur danych wypychana na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych.  
  
 Po pierwsze wywołanie `GetActiveInternalFrames`, należy ustawić `cInternalFrames` parametru na wartość 0 (zero) i `ppInternalFrames` parametru na wartość null. Gdy `GetActiveInternalFrames` zwraca najpierw `pcInternalFrames` zawiera liczbę wewnętrzny ramek na stosie.  
  
 `GetActiveInternalFrames` należy następnie wywołać po raz drugi. Należy przekazać odpowiednie liczby (`pcInternalFrames`) w `cInternalFrames` parametru, i określić wskaźnik do tablicy odpowiednio rozmiarze w `ppInternalFrames`.  
  
 Użyj [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metody do zwrócenia rzeczywistego ramek na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
