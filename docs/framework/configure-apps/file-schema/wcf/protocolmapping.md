---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: c50ca451052c9ad9d7ab6a0cb5387e644196191e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525009"
---
# <a name="ltprotocolmappinggt"></a>&lt;protocolMapping&gt;
Reprezentuje sekcję konfiguracji definiujących zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF. Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, Windows Communication Foundation (WCF) analizuje skonfigurowanego mapowania i decyduje o tym, na które powiązania do użycia dla określonego na podstawie adresu.  
  
[**\<system.serviceModel >**](system-servicemodel.md)  
&nbsp;&nbsp;**\<protocolMapping >**  
  
## <a name="syntax"></a>Składnia  
  
```xml
<protocolMapping>
   <add binding="String" bindingConfiguration="String" scheme="http/net.msmq/net.pipe/net.tcp"/>
</protocolMapping>  
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtry >](filters-of-routing.md)|Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązania usługi WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Element główny wszystkich elementów konfiguracji programu WCF.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config. Możesz przesłonić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config. Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracyjnym aplikacji i zmienić mapowanie schematów pojedynczy protokół.  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
