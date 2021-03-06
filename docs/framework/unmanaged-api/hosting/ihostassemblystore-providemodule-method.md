---
title: IHostAssemblyStore::ProvideModule — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440021"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule — Metoda
Usuwa plik zasobów modułu w ramach zestawu lub połączony (ale nie embedded).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [in] Wskaźnik do [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) wystąpienia opisujący żądany moduł <xref:System.AppDomain>, zestawu i nazwa modułu.  
  
 `pdwModuleId`  
 [out] Wskaźnik do Unikatowy identyfikator `IStream` zawierający załadować modułu.  
  
 `ppStmModuleImage`  
 [out] Wskaźnik do adresu `IStream` obiektu, który zawiera obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć modułu.  
  
 `ppStmPDB`  
 [out] Wskaźnik do adresu `IStream` obiektu, który zawiera informacje o debugowaniu (PDB) program dla żądanego modułu lub wartość null, jeśli nie można odnaleźć pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideModule` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Nie można zlokalizować żądanego zestawu lub zasobu połączonego.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` nie jest wystarczająco duży, aby zawierać identyfikator, który chce zwracać hosta.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracane wartości tożsamości dla `pdwModuleId` jest określana przez hosta. Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu. Środowisko CLR używa tej wartości jako unikatowy identyfikator dla tego strumienia skojarzone. Sprawdza każdej wartości z wartościami dla `pAssemblyId` zwrócony przez wywołania [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i wartościami dla `pdwModuleId` zwrócony przez inne wywołania `ProvideModule`. Jeśli host zwraca tej samej wartości identyfikatora dla innej `IStream`, CLR sprawdza, czy zawartość strumieniu już zostały zamapowane. Jeśli tak, CLR ładuje istniejącą kopię obrazu zamiast nowego mapowania. W związku z tym identyfikatorem musi również nie mogą się pokrywać o identyfikatorach zestaw zwrócony z `ProvideAssembly`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
