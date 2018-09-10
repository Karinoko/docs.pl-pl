---
title: 'Porady: bezpieczne multiemisji za pomocą dopasowywania do wzorca i jest i operatory'
description: Dowiedz się użyć metod dopasowania do wzorca można bezpieczne rzutować zmienne do innego typu. Możesz użyć dopasowywania do wzorca, jak również jest oraz jako operatorów można bezpiecznie konwersji typów.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 88289099864293b3b19da62155d58ba4797948bd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216707"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-is-and-as-operators"></a><span data-ttu-id="3715d-104">Porady: bezpieczne rzutowanie za pomocą dopasowywania do wzorca jest i operatory</span><span class="sxs-lookup"><span data-stu-id="3715d-104">How to: safely cast by using pattern matching is and as operators</span></span>

<span data-ttu-id="3715d-105">Ponieważ obiekty są polimorficznych, jest możliwe dla zmiennej typu klasy bazowej, aby pomieścić pochodnej [typu](../programming-guide/types/index.md).</span><span class="sxs-lookup"><span data-stu-id="3715d-105">Because objects are polymorphic, it's possible for a variable of a base class type to hold a derived [type](../programming-guide/types/index.md).</span></span> <span data-ttu-id="3715d-106">Aby uzyskać dostęp do składowych wystąpienia typu pochodnego, konieczne jest [rzutowania](../programming-guide/types/casting-and-type-conversions.md) wartość do typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="3715d-106">To access the derived type's instance members, it's necessary to [cast](../programming-guide/types/casting-and-type-conversions.md) the value back to the derived type.</span></span> <span data-ttu-id="3715d-107">Rzutowanie tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="3715d-107">However, a cast creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="3715d-108">C# zawiera [dopasowywania do wzorca](../pattern-matching.md) instrukcji, które wykonują rzutowania warunkowo, tylko wtedy, gdy zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3715d-108">C# provides [pattern matching](../pattern-matching.md) statements that perform a cast conditionally only when it will succeed.</span></span> <span data-ttu-id="3715d-109">C# oferuje także [jest](../language-reference/keywords/is.md) i [jako](../language-reference/keywords/as.md) operatory, aby sprawdzić, czy wartość jest określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3715d-109">C# also provides the [is](../language-reference/keywords/is.md) and [as](../language-reference/keywords/as.md) operators to test if a value is of a certain type.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="3715d-110">Poniższy przykład demonstruje wzorzec dopasowywania `is` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3715d-110">The following code demonstrates the pattern matching `is` statement.</span></span> <span data-ttu-id="3715d-111">Zawiera metody testowania argumentu metody, aby ustalić, czy jest jednym z możliwych zestawów typów pochodnych:</span><span class="sxs-lookup"><span data-stu-id="3715d-111">It contains methods that test a method argument to determine if it is one of a possible set of derived types:</span></span>

[!code-csharp-interactive[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

<span data-ttu-id="3715d-112">W poprzednim przykładzie pokazano kilka funkcji Składnia dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="3715d-112">The preceding sample demonstrates a few features of pattern matching syntax.</span></span> <span data-ttu-id="3715d-113">`if (a is Mammal m)` i `if (o is Mammal m)` instrukcje łączenia testu z przydziałem inicjowania.</span><span class="sxs-lookup"><span data-stu-id="3715d-113">The `if (a is Mammal m)` and `if (o is Mammal m)` statements combine the test with an initialization assignment.</span></span> <span data-ttu-id="3715d-114">Przypisanie tnie odbywa się tylko wtedy gdy test zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3715d-114">TThe assignment occurs only when the test succeeds.</span></span> <span data-ttu-id="3715d-115">Zmienna `m` jest tylko w zakresie osadzonego `if` instrukcji, w którym został przypisany.</span><span class="sxs-lookup"><span data-stu-id="3715d-115">The variable `m` is only in scope in the embedded `if` statement where it has been assigned.</span></span> <span data-ttu-id="3715d-116">Nie można uzyskać dostępu `m` dalej w tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="3715d-116">You cannot access `m` later in the same method.</span></span> <span data-ttu-id="3715d-117">Wypróbuj go w oknie interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="3715d-117">Try it in the interactive window.</span></span>

<span data-ttu-id="3715d-118">Można również użyć tej samej składni do badania, jeśli [typu dopuszczającego wartość null](../programming-guide/nullable-types/index.md) ma wartość, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="3715d-118">You can also use the same syntax for testing if a [nullable type](../programming-guide/nullable-types/index.md) has a value, as shown in the following sample code:</span></span>

[!code-csharp-interactive[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

<span data-ttu-id="3715d-119">Poprzedni przykład pokazuje inne funkcje za pomocą konwersji dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="3715d-119">The preceding sample demonstrates other features of pattern matching to use with conversions.</span></span> <span data-ttu-id="3715d-120">Możesz przetestować zmienną deseń zerowy, sprawdzając specjalnie pod kątem `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="3715d-120">You can test a variable for the null pattern by checking specifically for the `null` value.</span></span> <span data-ttu-id="3715d-121">Gdy wartość zmiennej środowiska uruchomieniowego jest `null`, `is` instrukcji sprawdzania dla typu zawsze zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="3715d-121">When the runtime value of the variable is `null`, an `is` statement checking for a type always returns `false`.</span></span> <span data-ttu-id="3715d-122">Dopasowanie wzorca `is` instrukcji nie dopuszcza typem wartościowym, takich jak `int?` lub `Nullable<int>`, ale możesz testować dowolny inny typ wartości.</span><span class="sxs-lookup"><span data-stu-id="3715d-122">The pattern matching `is` statement doesn't allow a nullable value type, such as `int?` or `Nullable<int>`, but you can test for any other value type.</span></span>

<span data-ttu-id="3715d-123">W poprzednim przykładzie pokazano, jak użyć dopasowania wzorca `is` wyrażenia w `switch` instrukcji, w którym zmienna może być jednym z wielu różnych typów.</span><span class="sxs-lookup"><span data-stu-id="3715d-123">The preceding sample also shows how you use the pattern matching `is` expression in a `switch` statement where the variable may be one of many different types.</span></span>

<span data-ttu-id="3715d-124">Jeśli chcesz sprawdzić, czy zmienna jest danego typu, ale nie przypisać ją do nowej zmiennej, można użyć `is` i `as` operatorów dla typów odwołań i typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="3715d-124">If you want to test if a variable is a given type, but not assign it to a new variable, you can use the `is` and `as` operators for reference types and nullable types.</span></span> <span data-ttu-id="3715d-125">Poniższy kod przedstawia sposób użycia `is` i `as` instrukcji, które były częścią języka C#, zanim dopasowywania do wzorca została wprowadzona, aby sprawdzić, czy zmienna jest danego typu:</span><span class="sxs-lookup"><span data-stu-id="3715d-125">The following code shows how to use the `is` and `as` statements that were part of the C# language before pattern matching was introduced to test if a variable is of a given type:</span></span>

[!code-csharp-interactive[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

<span data-ttu-id="3715d-126">Jak widać, porównując ten kod z kodem dopasowania wzorca Składnia dopasowania do wzorca zapewnia bardziej niezawodne funkcje, łącząc testu i przypisania w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3715d-126">As you can see by comparing this code with the pattern matching code, the pattern matching syntax provides more robust features by combining the test and the assignment in a single statement.</span></span> <span data-ttu-id="3715d-127">Użyj wzorca dopasowania składni, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="3715d-127">Use the pattern matching syntax whenever possible.</span></span>

<span data-ttu-id="3715d-128">Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast).</span><span class="sxs-lookup"><span data-stu-id="3715d-128">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast).</span></span> <span data-ttu-id="3715d-129">Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).</span><span class="sxs-lookup"><span data-stu-id="3715d-129">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).</span></span>