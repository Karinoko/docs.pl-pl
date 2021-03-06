---
title: 'Porady: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
ms.openlocfilehash: c764395b7926a131deae4109fed3a7461c45e2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519720"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Porady: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog
Można rozwiązać problemy ze współdziałaniem składnik modelu COM. wyświetlanie w formularzu systemu Windows [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, który jest tworzony przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Aby formularz działał prawidłowo, od aplikacji klienckiej COM, należy uruchomić je na pętli komunikatów formularzy systemu Windows. Aby to zrobić, użyj jednej z następujących metod:  
  
-   Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza systemu Windows;  
  
-   Wyświetlania każdego formularza systemu Windows w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Procedura  
 Przy użyciu <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda może być Najprostszym sposobem wyświetlenia formularza na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, ponieważ podejścia, wymaga co najmniej kod do implementacji.  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Metody wstrzymuje pętli komunikatów niezarządzanej aplikacji i wyświetla formularza jako okno dialogowe. Ponieważ pętli komunikatów w aplikacji hosta zostało zawieszone, <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda tworzy nowy [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów do przetwarzania komunikatów formularza.  
  
 Wadą korzystania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda to, że formularz zostanie otwarty jako modalne okno dialogowe. To zachowanie blokuje interfejs użytkownika (UI) w aplikacji wywołującej przy otwartym formularzu systemu Windows. Gdy użytkownik zamyka formularz, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] komunikatów pętla zostanie zamknięty i komunikat starsza aplikacja pętli uruchamiana ponownie.  
  
 Można utworzyć biblioteki klas w formularzach systemu Windows, który ma metodę wyświetlenie formularza i późniejszego kompilowania biblioteki klas dla modelu COM interop. Można użyć tego pliku DLL z języka Visual Basic 6.0 lub Microsoft Foundation Classes (MFC) i przy użyciu dowolnego z tych środowisk można wywołać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Aby obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularzy systemu windows przy użyciu metody ShowDialog  
  
-   Zamień wszystkie wywołania <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> metody wywołania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metody w Twojej [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] składnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Instrukcje: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [Formularze Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
