---
title: 'Zarządzanie zasobami: Use — słowo kluczowe (F#)'
description: Dowiedz się więcej o F# — słowo kluczowe "use" i "using" funkcji, która może kontrolować, inicjowanie i zwolnienia zasobów.
ms.date: 05/16/2016
ms.openlocfilehash: 300fb4113019f676625f75541d117458eab3f6ab
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147635"
---
# <a name="resource-management-the-use-keyword"></a>Zarządzanie zasobami: Use — słowo kluczowe

W tym temacie opisano słowa kluczowego `use` i `using` funkcji, która może kontrolować, inicjowanie i zwolnienia zasobów.

## <a name="resources"></a>Resources

Termin *zasobów* jest używana w więcej niż jeden sposób. Tak, zasobów mogą zawierać dane, które używa aplikacji, takich jak ciągi, grafiki i podobne, ale w tym kontekście *zasobów* odwołuje się do oprogramowania lub systemu operacyjnego zasoby, takie jak konteksty urządzenia grafiki, dojścia do plików, użycia sieci bazy danych i połączenia, obiektów współbieżności, takich jak dojścia oczekiwania i tak dalej. Korzystanie z tych zasobów przez aplikacje obejmuje pozyskiwanie zasobów z system operacyjny lub inne dostawcy zasobów, a następnie w nowszej wersji zasobu, do puli, dzięki czemu można przekazać do innej aplikacji. Problemy występują, gdy aplikacje nie zwalnia wspólnej puli zasobów.

## <a name="managing-resources"></a>Zarządzanie zasobami

Do efektywnego i odpowiedzialnego zarządzania zasobami w aplikacji, należy zwolnić zasoby, szybko i w przewidywalny sposób. Program .NET Framework pomaga, możesz to zrobić, podając `System.IDisposable` interfejsu. Typ, który implementuje `System.IDisposable` ma `System.IDisposable.Dispose` metody, która poprawnie zwalnia zasoby. Dobrze napisane aplikacje Microsoft gwarantuje, że `System.IDisposable.Dispose` niezwłocznie jest wywoływana, gdy dowolnego obiektu, który posiada ograniczone zasób, który nie jest już potrzebny. Na szczęście większość języków .NET zapewniają obsługę, aby to ułatwić, i F# nie jest wyjątkiem. Istnieją dwa konstrukcji językowych użyteczne, obsługujące wzorzec usuwania: `use` powiązania i `using` funkcji.

## <a name="use-binding"></a>Użyj powiązań

`use` — Słowo kluczowe ma postać przypominający `let` powiązania:

Użyj *wartość* = *wyrażenia*

Zapewnia taką samą funkcjonalność jak `let` powiązania, ale dodaje wywołanie `Dispose` na wartości, gdy wartość wykracza poza zakres. Należy pamiętać, że kompilator wstawia sprawdzania wartości null dla wartości, tak że jeśli wartość jest `null`, wywołanie `Dispose` nie podjęto próby.

Poniższy przykład pokazuje, jak i zamknij plik automatycznie przy użyciu `use` — słowo kluczowe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Możesz użyć `use` w wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `use` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).

## <a name="using-function"></a>przy użyciu funkcji

`using` Funkcji ma następującą postać:

`using` (*wyrażenie1*) *funkcji lub lambda*

W `using` wyrażenie *wyrażenie1* tworzy obiekt, który musi zostać usunięty. Wynik *wyrażenie1* (obiekt, który musi zostać usunięty) staje się argument, *wartość*, *funkcji lub lambda*, który jest funkcja, która oczekuje pojedynczego pozostałe argumentu typu, który dopasowuje wartość utworzona przez testowany *wyrażenie1*, lub wyrażenie lambda, która oczekuje argumentu typu. Po zakończeniu wykonywania funkcji, środowisko wykonawcze wywołuje `Dispose` i zwalnia zasoby (chyba że wartość jest `null`, w którym to przypadku nie jest wykonywane wywołanie metody Dispose).

W poniższym przykładzie pokazano `using` wyrażenie za pomocą wyrażenia lambda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

W następnym przykładzie pokazano `using` wyrażenie przy użyciu funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Należy pamiętać, że funkcja może być funkcją, która ma już stosowane argumenty. Poniższy przykład kodu pokazuje to. Tworzy plik, który zawiera ciąg `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkcji i `use` powiązania są prawie równoważne sposoby osiągnąć to samo. `using` — Słowo kluczowe zapewnia większą kontrolę nad tym, kiedy `Dispose` jest wywoływana. Kiedy używasz `using`, `Dispose` jest wywoływana na końcu wyrażenia funkcji lub lambda, gdy używasz `use` — słowo kluczowe, `Dispose` nosi nazwę na końcu bloku zawierającego kod. Ogólnie rzecz biorąc, należy wolą używać `use` zamiast `using` funkcji.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
