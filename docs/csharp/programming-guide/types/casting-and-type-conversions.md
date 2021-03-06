---
title: Rzutowanie i konwersje typów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: c7200f9d99eea8364d290b54efc514217f2b2dad
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245470"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Rzutowanie i konwersje typów (Przewodnik programowania w języku C#)

Ponieważ C# to typowany statycznie w czasie kompilacji, po zadeklarowaniu zmiennej, nie można ponownie zadeklarować lub przypisaną wartością innego typu, chyba że tego typu jest niejawnie konwertowany na typ zmiennej. Na przykład `string` nie może być niejawnie konwertowane na `int`. W związku z tym, gdy Deklarujesz `i` jako `int`, nie można przypisać ciąg "Hello", co ilustruje poniższy kod:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Jednak czasami może być konieczne Kopiowanie wartości do zmiennej lub metoda parametr innego typu. Na przykład, Niewykluczone, że zmienna typu Liczba całkowita, który chcesz przekazać do metody, w której parametr jest wpisana jako `double`. Można też przypisać zmiennej klasy do zmiennej typu interfejsu. Te rodzaje operacji są nazywane *konwersje typów*. W języku C# należy wykonać następujące rodzaje konwersje:  
  
-   **Niejawne konwersje**: Nie specjalnej składni jest wymagana, ponieważ konwersja jest bezpiecznym typem, a żadne dane nie zostaną utracone. Przykłady obejmują konwersji z mniejszych na większych typów całkowitych i konwersje z klasy podstawowej w klasach pochodnych.  
  
-   **Konwersje jawne (rzutowania)**: Konwersje jawne wymaga operatora rzutowania. Rzutowanie jest wymagane, gdy informacji może zostać utracone podczas konwersji, lub gdy Konwersja może się nie powieść z innych przyczyn.  Typowe przykłady obejmują numerycznej konwersji do typu, który ma mniejszą dokładność i mniejszy zakres i konwersja wystąpienia klasy bazowej do klasy pochodnej.  
  
-   **Konwersje zdefiniowane przez użytkownika**: Konwersje zdefiniowane przez użytkownika są wykonywane przez specjalne metody, które można zdefiniować umożliwia jawne i niejawne konwersje między typami niestandardowych, które nie mają relacji — Klasa pochodna klasy bazowej. Aby uzyskać więcej informacji, zobacz [operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Konwersje z klas pomocniczych**: Do konwersji między typami niezgodnych, takich jak liczby całkowite i <xref:System.DateTime?displayProperty=nameWithType> obiektów, lub ciągów szesnastkowych i tablice typu byte, możesz użyć <xref:System.BitConverter?displayProperty=nameWithType> klasy <xref:System.Convert?displayProperty=nameWithType> klasy i `Parse` metod typu liczbowego wbudowanych typów, takich jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [jak: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), i [jak: Konwertowanie ciągów szesnastkowych, które typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Niejawne konwersje  
 Dla wbudowanych typów liczbowych można wprowadzić niejawną konwersję, gdy wartość ma być przechowywany można dopasować do zmiennej bez są obcięte lub zaokrąglony. Na przykład zmienna typu [długie](../../../csharp/language-reference/keywords/long.md) (64-bitowa liczba całkowita) można przechowywać wszystkie wartości [int](../../../csharp/language-reference/keywords/int.md) (32-bitowa liczba całkowita) można przechowywać. W poniższym przykładzie, kompilator niejawnie konwertuje wartość `num` po prawej stronie na typ `long` przed przypisaniem go do `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Aby uzyskać pełną listę wszystkich niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Dla typów odwołań istnieje niejawna konwersja zawsze z klasy do jednej z jego bezpośredniej lub pośredniej klasy bazowej lub interfejsów. Nie specjalnej składni jest konieczne, ponieważ klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy bazowej.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Konwersje jawne  
 Jednakże, jeśli konwersja nie może być nawiązywane bez ryzyka utraty informacji, kompilator wymaga jednak wykonania jawnej konwersji, która jest wywoływana *rzutowania*. Rzutowanie jest sposób jawnie informowania kompilator zamierzasz wprowadzić konwersji i że masz świadomość, może dojść do utraty danych. Aby wykonać rzutowanie, należy określić typ, który jest Rzutowanie na w nawiasach wartość lub zmienną, które ma zostać przekonwertowany. Poniższy program rzutowania [double](../../../csharp/language-reference/keywords/double.md) do [int](../../../csharp/language-reference/keywords/int.md). Program nie zostanie skompilowany bez rzutowania.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Aby uzyskać listę jawnych konwersji liczbowych, które mogą zobaczyć [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Dla typów odwołań jawnego rzutowania jest wymagany, jeśli chcesz przekonwertować typ pochodny od typu podstawowego:  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Operacji rzutowania między typami odwołań nie zmienia typu środowiska wykonawczego obiektu bazowego; zmienia tylko typ wartości, który jest używany jako odwołanie do tego obiektu. Aby uzyskać więcej informacji, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Wyjątki konwersji typu w czasie wykonywania  
 W niektórych konwersji typu odwołania kompilator nie może określić, czy rzutowania będzie nieprawidłowa. Istnieje możliwość dla operacji rzutowania, skompilowany poprawnie Niepowodzenie w czasie wykonywania. Jak pokazano w poniższym przykładzie, typ rzutowania spowoduje kończy się niepowodzeniem w czasie wykonywania <xref:System.InvalidCastException> zostanie wygenerowany.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów umożliwiających testowanie zgodności przed wykonaniem faktycznie rzutowania. Aby uzyskać więcej informacji, zobacz [jak: Bezpieczne rzutowanie za pomocą dopasowywania do wzorca, jak i operatory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Typy](../../../csharp/programming-guide/types/index.md)  
- [(), operator](../../../csharp/language-reference/operators/invocation-operator.md)  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
- [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [Konwersja uogólnionych typów](https://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
- [Konwersja typu wyeksportowanego](https://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
- [Instrukcje: Konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
