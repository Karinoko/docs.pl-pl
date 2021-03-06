---
title: Niejawnie wpisane tablice - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 9c235b6084238917c2cb3f2cd745aef0264f82ce
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238276"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Niejawnie wpisane tablice (Przewodnik programowania w języku C#)

Można utworzyć tablicę niejawnie wpisany, w którym Typ wystąpienia tablicy jest wnioskowany z elementami określonymi w inicjatorze tablicy. Reguły dotyczące niejawnie typizowanej zmiennej dotyczą również niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Niejawnie wpisane tablice są zazwyczaj używane w wyrażeniach zapytań oraz typy anonimowe i inicjatory obiektów i kolekcji.  
  
 W poniższych przykładach pokazano, jak utworzyć tablicę niejawnie wpisany:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 W poprzednim przykładzie należy zauważyć, że z niejawnie wpisane tablice żadne nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania. Należy zauważyć, że Tablice nieregularne są inicjowane za pomocą `new []` podobnie jak w przypadku tablic jednego wymiaru.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Niejawnie wpisane tablice w inicjatorach obiektu

 Podczas tworzenia typu anonimowego, które zawiera tablicę tablicy musi być wpisana niejawnie w inicjatorze obiektu typu. W poniższym przykładzie `contacts` jest niejawnie wpisany tablicą typów anonimowych, z których każdy zawiera tablicę o nazwie `PhoneNumbers`. Należy pamiętać, że `var` — słowo kluczowe nie jest używany w inicjatorach obiektów.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Jawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
- [Tablice](../../../csharp/programming-guide/arrays/index.md)  
- [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [var](../../../csharp/language-reference/keywords/var.md)  
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
