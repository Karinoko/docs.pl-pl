---
title: while — C# odwołania
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: d360db7b9b740bef997327dda9b628c1edab0f35
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242571"
---
# <a name="while-c-reference"></a>while (odwołanie w C#)

`while` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`. Ponieważ to wyrażenie jest obliczane przed każdym wykonaniu pętli, `while` pętla jest wykonywana zero lub więcej razy. To różni się od [czy](do.md) pętli, która wykonuje jeden lub więcej razy.

W dowolnym punkcie w `while` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji.

Użytkownik może przechodzić bezpośrednio do obliczania `while` wyrażenie, używając [nadal](continue.md) instrukcji. Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane po pierwszej instrukcji w pętli. W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji następującej po pętli.

Możesz również wyjść `while` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `while` instrukcji. Wybierz **Uruchom** do uruchamiania kodu przykładu. Po tym można zmodyfikować kod i uruchom go ponownie.

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [while, instrukcja](~/_csharplang/spec/statements.md#the-while-statement) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Instrukcje iteracji](iteration-statements.md)  
- [— Instrukcja](do.md)  
