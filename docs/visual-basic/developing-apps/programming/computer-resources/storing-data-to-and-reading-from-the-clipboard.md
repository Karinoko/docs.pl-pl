---
title: Zapisywanie danych i odczytywania ze Schowka (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 7964a39bb84ac6af6b6c196c053f51c30301985c
ms.sourcegitcommit: 8c6c62ba1eefa492701e264e41890ee20fae77a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2018
ms.locfileid: "42751892"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Zapisywanie danych i odczytywania ze Schowka (Visual Basic)
Schowek może służyć do przechowywania danych, takich jak tekst i obrazy. Ponieważ Schowek jest współużytkowany przez wszystkie aktywne procesy, może służyć do przesyłania danych między nimi. `My.Computer.Clipboard` Pozwala łatwo uzyskiwać dostęp do Schowka, a także odczytywanie i zapisywanie do niego.  
  
## <a name="reading-from-the-clipboard"></a>Odczytywanie ze Schowka  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metodę w celu odczytania tekstu w Schowku. Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu. Musi to być tekst są przechowywane w Schowku, na przykład by działała poprawnie.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metodę, aby pobrać obraz ze Schowka. W tym przykładzie sprawdza, czy obraz w Schowku przed ich pobraniem i przypisywanie jej do `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **aplikacji z formularzem Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Elementy umieszczane w Schowku zostanie utrzymany, nawet w przypadku, po zamknięciu aplikacji.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Określanie typu plików przechowywanych w Schowku  
 Dane w Schowku może potrwać szereg różnych formularzy, takich jak tekst, plik dźwiękowy lub obrazu. Aby ustalić, jakiego rodzaju plik znajduje się na Schowka, możesz używać metod takich jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metody można użyć, jeśli ma format niestandardowy, który chcesz sprawdzić.  
  
 Użyj `ContainsImage` funkcję, aby określić, czy dane zawarte w Schowku jest obrazem. Poniższy kod sprawdza, czy dane są obrazu, a następnie odpowiednio raporty.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Wyczyszczenie Schowka  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metoda czyści Schowka. Ponieważ Schowek jest współużytkowany przez inne procesy, czyszczenie może mieć wpływ na tych procesów.  
  
 Poniższy kod przedstawia sposób użycia `Clear` metody.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Zapisywanie do Schowka  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodę, aby wpisać tekst do Schowka. Poniższy kod zapisuje ciąg "To jest testowany ciąg" do Schowka.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` Metoda może akceptować parametr formatu, który zawiera typ <xref:System.Windows.Forms.TextDataFormat>. Poniższy kod zapisuje ciąg "To jest testowany ciąg" do Schowka jako tekst w formacie RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metodę, aby zapisywać dane do Schowka. Ten przykład Przepisuje `DataObject` `dataChunk` do Schowka w niestandardowy formacie `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metodę, aby zapisać dane audio do Schowka. Ten przykład tworzy tablicę bajtów `musicReader`, odczytuje plik `cool.wav` do niego, a następnie zapisuje je do Schowka.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Ponieważ inni użytkownicy mogą uzyskać dostępu do Schowka, nie należy używać go do przechowywania poufne informacje, takie jak hasła lub poufnych danych.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [Instrukcje: odczytywanie danych o obiektach z pliku XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Instrukcje: wpisywanie danych o obiektach do pliku XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
