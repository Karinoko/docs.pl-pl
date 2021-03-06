---
title: '&lt;requestCaching —&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: fecb3c71e0686a557b8a4b0c85b7d91a9846204f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194972"
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching —&gt; — Element (ustawienia sieci)
Określa mechanizm buforowania żądań sieci.  
  
 \<Konfiguracja >  
\<system.net>  
\<requestCaching — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`isPrivateCache`|Określa, czy pamięć podręczna zapewnia izolację między informacji o różnych użytkowników. Wartość domyślna to `true`. Ta wartość powinna być `false` dla aplikacji warstwy środkowej.|  
|`disableAllCaching`|Określa, że buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie może być zastąpiona programowo.|  
|`defaultPolicyLevel`|Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia. Wartość domyślna to `BypassCache`.|  
|`unspecifiedMaximumAge`|Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.|  
  
## <a name="policylevel-attribute"></a>policyLevel atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`Default`|Zwraca buforowane zasobu, jeśli zasób jest świeże, długość zawartości jest dokładne i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.|  
|`BypassCache`|Zwraca zasobu z serwera.|  
|`CacheOnly`|Zwraca buforowane zasobu, jeśli długość zawartości jest obecna, a także odpowiada rozmiarowi wpisu.|  
|`CacheIfAvailable`|Zwraca buforowane zasobu, jeśli długość zawartości jest dostarczany i odpowiada rozmiarowi wejścia; w przeciwnym razie zasób zostanie pobrana z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Zwraca buforowane zasobu, jeśli sygnatury czasowej zasobów pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.|  
|`Reload`|Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.|  
|`NoCacheNoStore`|Jeśli istnieje zasób pamięci podręcznej, został usunięty. Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.|  
|`Revalidate`|Spełnia żądanie przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przedstawione do obiektu wywołującego i jest przechowywany w pamięci podręcznej|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[defaulthttpcachepolicy —](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie HTTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.|  
|[\<defaultftpcachepolicy — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|Element opcjonalny.<br /><br /> Opisuje, czy buforowanie FTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[przestrzeni nazw System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć buforowaniu.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Net.Cache?displayProperty=nameWithType>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
