---
title: 'Porady: drukowanie obszarów klienckich formularza (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: b2f13d1ec151a5fd1967b522a601e0e19de04cbb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45689226"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a>Porady: drukowanie obszarów klienckich formularza (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika. Poniższa procedura pokazuje jak drukować po prostu obszaru klienta formularza, bez paska tytułu, obramowania i paski przewijania.  
  
 Kontrolki pakietu PowerPack nie są już dostępne w programie Visual Studio, ale można je pobrać w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
### <a name="to-print-the-client-area-of-a-form"></a>Aby drukowanie obszarów klienckich formularza  
  
1.  W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz.   
  
     Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> jest dodawany do zasobnika składników.   
  
2.  W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.   
  
3.  Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**).   
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie może poprawnie wydrukować. W takim przypadku należy użyć kompatybilna metoda drukowania: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [Instrukcje: drukowanie formularza przewijanego](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
