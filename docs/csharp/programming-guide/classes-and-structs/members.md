---
title: Elementy członkowskie — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: e8429df6ef633f11df50ee5526496f9688f845ea
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245107"
---
# <a name="members-c-programming-guide"></a>Członkowie (Przewodnik programowania w języku C#)
Klasy i struktury mają elementów członkowskich, które reprezentują ich danych i działania. Elementy członkowskie klasy obejmują wszystkie elementy członkowskie zadeklarowana w klasie, oraz wszystkie elementy członkowskie (z wyjątkiem konstruktorów i finalizatory) zadeklarowane dla wszystkich klas w hierarchii dziedziczenia. Prywatne składowe w klasach bazowych są dziedziczone, ale nie są dostępne z klas pochodnych.  
  
 W poniższej tabeli wymieniono rodzaje elementów członkowskich, który klasa lub struktura może zawierać:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)|Pola są zmiennych zadeklarowanych w zakresie klasy. Pole może być wbudowanego typu liczbowego lub wystąpienie innej klasy. Na przykład klasa kalendarza mogą mieć pola, które zawiera bieżącą datę.|  
|[Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)|Stałe są pola lub właściwości, którego wartość jest ustawiana na czas kompilacji i nie można zmienić.|  
|[Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)|Właściwości są metody klasy, które są dostępne, tak jakby pól dla tej klasy. Właściwość może zapewnić ochronę pola klasy uniemożliwić zmianę bez wiedzy obiektu.|  
|[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)|Metody zdefiniowania akcji, które można wykonywać klasy. Metody może przyjąć parametry, które zawierają dane wejściowe i może zwrócić danych wyjściowych za pomocą parametrów. Metody może również zwracać wartość bezpośrednio, bez korzystania z parametru.|  
|[Zdarzenia](../../../csharp/programming-guide/events/index.md)|Zdarzenia udostępniają powiadomienia dotyczące zdarzenia, takie jak kliknięcia przycisków lub pomyślne zakończenie metody, do innych obiektów. Zdarzenia są zdefiniowane i wyzwalane za pomocą obiektów delegowanych.|  
|[Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Przeciążone operatory są traktowane jako elementy członkowskie klasy. Gdy operator jest przeciążenia, zdefiniuj jako publicznej metody statycznej w klasie. Wstępnie zdefiniowane operatorów (`+`, `*`, `<`i tak dalej) nie są traktowane jako elementy członkowskie. Aby uzyskać więcej informacji, zobacz [operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Indeksatory](../../../csharp/programming-guide/indexers/index.md)|Indeksatory włączyć obiekt zostać pomyślnie zindeksowane w sposób podobny do tablic.|  
|[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Konstruktory są metodami, które są wywoływane podczas tworzenia obiektu. Są często używane do zainicjowania dane obiektu.|  
|[Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Finalizatory są bardzo rzadko używane w języku C#. Są one metody, które są wywoływane przez silnika wykonania środowiska uruchomieniowego, gdy obiekt zostanie usunięty z pamięci. Zwykle służą one do upewnij się, wszystkie zasoby, które muszą zostać zwolnione, są odpowiednio obsługiwany.|  
|[Zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|Zagnieżdżone typy są typy zadeklarowane wewnątrz innego typu. Zagnieżdżone typy są często używane do opisywania obiektów, które są używane tylko przez typy zawierające je.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)  
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
- [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
- [Operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
