---
title: RUNTIME_INFO_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09bd32172bcad298eebc2921461fdc953e9c6d6e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084500"
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS — Wyliczenie
Zawiera wartości, które wskazują, jakie informacje dotyczące środowisko uruchomieniowe języka wspólnego (CLR) ma zostać zwrócony.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Wskazuje, że informacje o katalogu nie powinny być uwzględnione.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Wskazuje, że informacje o wersji nie powinny być uwzględnione.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Wskazuje, że nie być wyświetlane okno dialogowe błędu w przypadku awarii.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Oznacza to, że efekty wywoływania [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji przy użyciu flagi SEM_FAILCRITICALERRORS powinna zostać zastąpiona. Oznacza to, że okno dialogowe Instalacja powinna być pokazywana w przypadku awarii, a nie są pomijane.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Wskazuje żądanie dotyczące informacji na temat AMD-64-compatible wersję środowiska uruchomieniowego.|  
|`RUNTIME_INFO_REQUEST_IA64`|Wskazuje żądanie dotyczące informacji na temat IA-64-compatible wersję środowiska uruchomieniowego.|  
|`RUNTIME_INFO_REQUEST_X86`|Wskazuje żądanie informacji o x86 zgodną wersję środowiska uruchomieniowego.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Wskazuje, informacje o wersji uaktualnienia należy dołączyć.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące flagi architektura platformy może być określony tylko jeden w danym momencie i nie można połączyć:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
