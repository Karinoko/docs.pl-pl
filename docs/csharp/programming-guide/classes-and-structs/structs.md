---
title: Struktury - C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 3f19d0485939e1923c479c1c9fdeb06572a11e14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240388"
---
# <a name="structs-c-programming-guide"></a>Struktury (Przewodnik programowania w języku C#)

Struktury są zdefiniowane przy użyciu [struktury](../../language-reference/keywords/struct.md) — słowo kluczowe, na przykład:  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
Struktury współużytkując większość tej samej składni jako klasy. Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md). Struktury są bardziej ograniczone niż klas w następujący sposób:  
  
- W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.  
- Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.  
- Struktury są kopiowane w przydziale. Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii. Ważne jest, aby pamiętać podczas pracy z kolekcjami wartość typy takie jak `Dictionary<string, myStruct>`.  
- Struktury są typami wartości, w przeciwieństwie do klasy, które są typami odwołań.  
- W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.  
- Struktury można zadeklarować konstruktorów, które mają parametry. 
- Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy. Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.  
- Struktura może zaimplementować interfejsów.  
- Struktura może służyć jako typ dopuszczający wartość null i można przypisać wartości null.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

Informacje dodatkowe:  
  
- [Używanie struktur](using-structs.md)
- [Konstruktory](constructors.md)
- [Typy dopuszczające wartości null](../nullable-types/index.md)
- [Instrukcje: Różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](index.md)
- [Klasy](classes.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
