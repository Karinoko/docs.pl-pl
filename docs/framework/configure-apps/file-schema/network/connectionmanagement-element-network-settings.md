---
title: '&lt;connectionManagement&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 7cc5f2a37c0520ee48a10afeb4b9bc83ffd61033
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201546"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a>&lt;connectionManagement&gt; — Element (ustawienia sieci)
Określa maksymalną liczbę połączeń z hostem sieci.  
  
 \<Konfiguracja >  
\<system.net>  
\<connectionManagement >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|Dodaje adres IP lub nazwę DNS na liście zarządzania połączenia.|  
|[Usuń zaznaczenie](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|Czyści listę zarządzania połączenia.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|Usuwa adres IP lub nazwę DNS na liście zarządzania połączenia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[przestrzeni nazw System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 `connectionManagement` Element definiuje maksymalną liczbę połączeń do serwera lub grupy serwerów.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia skonfigurowanie aplikacji na używanie cztery połączenia z serwerem `www.contoso.com` i dwóch połączeń na inne serwery.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
