---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 3c7fd74a84184ddbf8cc8db90141174ed84e5774
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746660"
---
# <a name="ltpersistenceprovidergt"></a>&lt;persistenceProvider&gt;
Określa typ do użycia implementacja dostawcy trwałości, jak również limit czasu na potrzeby operacji trwałości.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<persistenceProvider >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|persistenceOperationTimeout|A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania. Wartość domyślna to "00: 00:30".|  
|— typ|Ciąg określający typ fabryki dostawców trwałości do użycia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa dostawcy trwałości, który ma być używany do serializacji stanu usługi WCF. Tej opcji należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
