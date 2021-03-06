---
title: 'Porady: otwieranie pliku dziennika i dołączanie do niego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35a7d481cf82818054a852f7c2e142f615022fcb
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848156"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Porady: otwieranie pliku dziennika i dołączanie do niego
<xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> zapisu znaków do i odczytywanie znaków ze strumieni. Poniższy kod przykładowy otwiera `log.txt` plików dla danych wejściowych i tworzy plik jeśli jeszcze nie istnieje i dołącza informacje do końca pliku. Zawartość pliku są następnie zapisywane do wyjścia standardowego do wyświetlenia. Jako alternatywę do tego przykładu, informacje mogą być przechowywane jako pojedynczy ciąg lub tablicę ciągów i <xref:System.IO.File.WriteAllText%2A> lub <xref:System.IO.File.WriteAllLines%2A> metoda może służyć do osiągnięcia taką samą funkcjonalność.  
  
> [!NOTE]
>  Użytkownicy języka Visual Basic mogą zdecydować się na metody i właściwości dostarczonych przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasa do tworzenia lub zapisywanie w plikach dziennika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
