---
title: "Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa22b011b895a20cefdcc5a7c9e6c1cd0531923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows
W projekcie aplikacji może być konieczne użycie obsługą jednego zdarzenia dla wielu zdarzeń lub ma wiele zdarzeń wykonanie tej procedury. Na przykład często jest zaawansowanym oszczędność czasu do polecenia wywołaj zdarzenie sam, jak przycisk w formularzu, jeśli udostępniają te same funkcje. Aby to zrobić, za pomocą widoku zdarzeń okna właściwości w języku C# lub `Handles` — słowo kluczowe i **Nazwa klasy** i **nazwę metody** list rozwijanych w edytorze kodu języka Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Aby połączyć wiele zdarzeń do jednego zdarzenia programu obsługi w języku Visual Basic  
  
1.  Kliknij prawym przyciskiem myszy formularz, a następnie wybierz pozycję **kod widoku**.  
  
2.  Z **Nazwa klasy** pole listy rozwijanej, wybierz jedną z formantów, które chcesz, aby obsłużyć programu obsługi zdarzeń.  
  
3.  Z **nazwę metody** pole listy rozwijanej, wybierz jedną z zdarzenia, które ma być obsługi program obsługi zdarzeń.  
  
4.  Edytor kodu wstawia programu obsługi zdarzeń odpowiednie i umieszcza kursor w metodzie. W poniższym przykładzie jest <xref:System.Windows.Forms.Control.Click> zdarzenia dla <xref:System.Windows.Forms.Button> formantu.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Dołącz inne zdarzenia chcesz dla właściwości handled `Handles` klauzuli.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Dodaj odpowiedni kod do obsługi zdarzeń.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Aby połączyć wiele zdarzeń do jednego zdarzenia programu obsługi w języku C#  
  
1.  Wybierz kontrolkę, z którym chcesz się połączyć program obsługi zdarzeń.  
  
2.  Kliknij w oknie właściwości **zdarzenia** przycisk (![przycisk zdarzeń](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  Kliknij nazwę zdarzenia, które mają być obsługiwane.  
  
4.  W sekcji wartość obok nazwy zdarzenia kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń zgodnych podpis metody zdarzenia, które mają być obsługiwane.  
  
5.  Program obsługi zdarzeń odpowiednie wybierz z listy.  
  
     Kod zostanie dodany do formularza, aby powiązać zdarzenia istniejącego programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)