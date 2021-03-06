---
title: LINQ i ciągi (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: da7a35f0fd66d1f7b8a72550c175b5428242fbc1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886503"
---
# <a name="linq-and-strings-c"></a>LINQ i ciągi (C#)

LINQ mogą służyć do wykonywania zapytań i przekształcanie ciągów i zbiorów ciągów. Może być szczególnie przydatne w przypadku danych z częściową strukturą w plikach tekstowych. Zapytania LINQ można łączyć z funkcji tradycyjnego ciągów i wyrażeń regularnych. Na przykład, można użyć <xref:System.String.Split%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metodę, aby utworzyć tablicę ciągów, które można zbadać lub zmodyfikować za pomocą LINQ. Możesz użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in Class metoda `where` klauzula zapytania LINQ. I LINQ umożliwia zapytania lub zmodyfikować <xref:System.Text.RegularExpressions.MatchCollection> wyniki zwrócone przez wyrażenie regularne.

Metod opisanych w tej sekcji służy również do przekształcania tekstu lub częściową strukturą danych do pliku XML. Aby uzyskać więcej informacji, zobacz [porady: generowanie XML z plików CSV](how-to-generate-xml-from-csv-files.md).

Przykłady w tej sekcji można podzielić na dwie kategorie:

## <a name="querying-a-block-of-text"></a>Wykonywanie zapytań w bloku tekstu

Zapytanie, analizowania i zmodyfikować bloków tekstu, dzieląc je na odpytywalny tablicę ciągów mniejszych przy użyciu <xref:System.String.Split%2A?displayProperty=nameWithType> metody lub <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody. Można podzielić tekst źródłowy słów, zdań, akapitów, stron lub innych kryteriów, a następnie wykonać dodatkowe dzieli dane, jeśli są one wymagane w kwerendzie.

- [Porady: liczenie wystąpień wyrazu w ciągu (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Pokazuje, jak używać programu LINQ do wykonywania prostych zapytań nad tekstem.

- [Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Pokazuje, jak podzielić pliki tekstowe na odgórnych ograniczeń i poznać sposoby wykonywania zapytań względem każdej części.

- [Porady: zapytanie o znaki w ciągu (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Pokazuje, czy ciąg jest typem odpytywalnym.

- [Porady: łączenie zapytań LINQ z wyrażeniami regularnymi (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Pokazuje, jak używać wyrażeń regularnych w zapytaniach LINQ dla złożonych dopasowania do wzorca w wynikach zapytania filtrowanego.

## <a name="querying-semi-structured-data-in-text-format"></a>Podczas badania częściowo ustrukturyzowanych danych w formacie tekstowym

Wiele różnych typów plików tekstowych składają się z szeregu wiersze, często z podobnego formatowania, takie jak karty lub przecinkami pliki lub wiersze o stałej długości. Po przeczytaniu pliku tekstowego do pamięci można użyć LINQ do zapytań i/lub modyfikowania wierszy. Zapytania LINQ również uprościć zadanie połączenie danych z wielu źródeł.

- [Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Pokazuje, jak znaleźć wszystkie ciągi, które znajdują się w jednej liście, ale nie drugiej.

- [Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Pokazuje sposób sortowania wierszy tekstu, w oparciu o dowolnego słowa lub pola.

- [Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Pokazuje, jak zmienianie kolejności pól w wierszu w pliku CSV.

- [Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Pokazuje, jak łączyć listy parametrów na różne sposoby.

- [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródła danych.

- [Porady: łączenie zawartości niepodobnych plików (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Pokazuje, jak połączyć dwie listy ciągów w jeden ciąg przy użyciu zgodnego klucza.

- [Porady: dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Pokazuje, jak utworzyć nowe pliki przy użyciu pojedynczego pliku jako źródło danych.

- [Porady: obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Pokazuje sposób wykonywania obliczeń matematycznych na danych tekstu w plikach CSV.

## <a name="see-also"></a>Zobacz też

- [Zapytanie o języku zintegrowanym (LINQ) (C#)](index.md)
- [Instrukcje: generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md)
