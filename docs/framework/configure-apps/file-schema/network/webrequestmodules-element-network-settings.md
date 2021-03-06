---
title: '&lt;webRequestModules&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 1d421009e8b2e0d4074679939092180c6037a0c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200447"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;webRequestModules&gt; — Element (ustawienia sieci)
Określa moduły do użycia na żądanie informacji z hostów w sieci.  
  
 \<Konfiguracja >  
\<system.net>  
\<webRequestModules>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Dodaje niestandardowy moduł żądania sieci Web do aplikacji.|  
|[Usuń zaznaczenie](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Usuwa niestandardowego modułu żądania sieci Web z aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[przestrzeni nazw System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 `webRequestModules` Element rejestruje podrzędne <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów w sieci. Moduły żądania sieci Web musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.  
  
 Program .NET Framework zawiera moduły żądania sieci Web dla identyfikatorów URI, które zaczynają się od `http://`, `https://`, i `file://`. Można zastąpić domyślne moduły tylko poprzez zarejestrowanie niestandardowego modułu w pliku konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje domyślny moduł HTTP. Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Net.WebRequest>  
- <xref:System.Net.IWebRequestCreate>  
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
