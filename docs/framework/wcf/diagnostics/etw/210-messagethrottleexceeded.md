---
title: 210 — MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460304"
---
# <a name="210---messagethrottleexceeded"></a>210 — MessageThrottleExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|210|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany, gdy dla jednego z trzech głównych usługi zostały przekroczone limity. Należy pamiętać, że to zdarzenie tylko wysyłanego początkowo przekroczenia limitu ograniczania przepustowości. Na przykład, jeśli limit przepustnicy dla jednoczesnych wywołań jest 10, 11 równoczesnych wyniki wywołania `MessageThrottleExceeded` zdarzeń. W innym przypadku nie powoduje wywołanie 12. Ponadto aby uniknąć strumienia zdarzeń zakłócenia, działanie, które znajduje się wokół limit nie powoduje inne zdarzenie. W tym przykładzie Jeśli kilka wywołania zakończone następnie jest 9 współbieżnych wywołań. Jeśli następnie dwóch kolejnych wywołań wejść, bieżąca wartość jest ponownie 11. Nie powoduje to inne zdarzenie. Gdy bieżąca wartość znajduje się do 70 procent limit przepustnicy zdarzenia jest emitowany wskazujący, że ma spowolnić działanie. Przyszłe działania, która przekracza limit wyników w innym `MessageThrottleExceeded` zdarzenia, które są emitowane. W tym przykładzie, jeśli liczba równoczesnych wywołań spadnie do 7, a następnie ponownie osiągnie 11 i innego `MessageThrottleExceeded` jest emitowany zdarzeń.  
  
## <a name="message"></a>Komunikat  
 Osiągnięto limit przepustnicy "%1" z "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa ograniczenia|`xs:string`|Nazwa ograniczenia, który został przekroczony. Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktualnie skonfigurowany limit przepustnicy.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
