---
title: Funkcje pierwszej klasy
description: Dowiedz się więcej o najwyższej klasy funkcji i jak są one ważne w przypadku programowania funkcyjnego w F#.
ms.date: 10/29/2018
ms.openlocfilehash: 1459049c9c1c77f4eefd2a83945335b33ca22ab9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50744622"
---
# <a name="first-class-functions"></a><span data-ttu-id="d1786-103">Funkcje pierwszej klasy</span><span class="sxs-lookup"><span data-stu-id="d1786-103">First-class functions</span></span>

<span data-ttu-id="d1786-104">Definiowanie cech funkcjonalności językach programowania jest podniesienie uprawnień funkcji do pierwszej klasy stanu.</span><span class="sxs-lookup"><span data-stu-id="d1786-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="d1786-105">Można zrobić za pomocą funkcji, niezależnie od rodzaju można zrobić za pomocą wbudowanych typów wartości i można zrobić o stopniu porównywalne nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="d1786-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="d1786-106">Typowe środki najwyższej jakości stanu są następujące:</span><span class="sxs-lookup"><span data-stu-id="d1786-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="d1786-107">Można powiązać funkcji do identyfikatorów?</span><span class="sxs-lookup"><span data-stu-id="d1786-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="d1786-108">Oznacza to można nadać im nazwy?</span><span class="sxs-lookup"><span data-stu-id="d1786-108">That is, can you give them names?</span></span>

- <span data-ttu-id="d1786-109">Może przechowujesz funkcje w strukturach danych, takich jak na liście?</span><span class="sxs-lookup"><span data-stu-id="d1786-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="d1786-110">Można przekazać funkcję jako argument w wywołaniu funkcji?</span><span class="sxs-lookup"><span data-stu-id="d1786-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="d1786-111">Może zwrócić funkcję po wywołaniu funkcji?</span><span class="sxs-lookup"><span data-stu-id="d1786-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="d1786-112">Ostatnie dwie miary zdefiniować, co to są znane jako *operacje wyższego rzędu* lub *funkcji wyższego rzędu*.</span><span class="sxs-lookup"><span data-stu-id="d1786-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="d1786-113">Funkcji wyższego rzędu Zaakceptuj funkcji jako argumentów i zwracanie funkcji jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="d1786-114">Te operacje obsługi tych filarów programowania funkcjonalnego jako mapowanie funkcji i kompozycja funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="d1786-115">Nadaj nazwę wartości</span><span class="sxs-lookup"><span data-stu-id="d1786-115">Give the Value a Name</span></span>

<span data-ttu-id="d1786-116">Jeśli funkcja jest wartością pierwszej klasy, należy możliwość nadaj mu tak samo, jak możesz nazwać liczb całkowitych, ciągów i innych wbudowanych typów.</span><span class="sxs-lookup"><span data-stu-id="d1786-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="d1786-117">Jest to określane w funkcjonalności programowania literaturze dostępne jako powiązanie identyfikatora do wartości.</span><span class="sxs-lookup"><span data-stu-id="d1786-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="d1786-118">F# stosuje [ `let` powiązania](../language-reference/functions/let-bindings.md) można powiązać nazwy wartości: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="d1786-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="d1786-119">Poniższy kod pokazuje dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="d1786-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="d1786-120">Funkcja równie łatwo można nazwać.</span><span class="sxs-lookup"><span data-stu-id="d1786-120">You can name a function just as easily.</span></span> <span data-ttu-id="d1786-121">W poniższym przykładzie zdefiniowano funkcję o nazwie `squareIt` przez powiązanie identyfikatora `squareIt` do [wyrażenia lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="d1786-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="d1786-122">Funkcja `squareIt` ma jeden parametr `n`, i zwraca kwadrat tego parametru.</span><span class="sxs-lookup"><span data-stu-id="d1786-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="d1786-123">F# zawiera następujące bardziej zwięzły widok składnię, aby osiągnąć ten sam wynik w trakcie pisania mniej.</span><span class="sxs-lookup"><span data-stu-id="d1786-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="d1786-124">Przykłady, które należy wykonać przede wszystkim Użyj pierwszego stylu `let <function-name> = <lambda-expression>`, aby podkreślić podobieństwa deklaracji funkcji, jak i deklarację inne typy wartości.</span><span class="sxs-lookup"><span data-stu-id="d1786-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="d1786-125">Jednak o nazwie funkcji można również będą zapisywane przy użyciu zwięzłej składni.</span><span class="sxs-lookup"><span data-stu-id="d1786-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="d1786-126">Przykłady są napisane w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="d1786-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="d1786-127">Wartość w strukturze danych Store</span><span class="sxs-lookup"><span data-stu-id="d1786-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="d1786-128">Wartości pierwszej klasy mogą być przechowywane w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d1786-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="d1786-129">Poniższy kod przedstawia przykłady, które przechowują wartości na listach i w spójnych kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="d1786-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="d1786-130">Aby sprawdzić, czy nazwy funkcji, przechowywane w krotce w rzeczywistości oceny do funkcji, w poniższym przykładzie użyto `fst` i `snd` operatory, aby wyodrębnić elementy pierwszego i drugiego z krotki `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="d1786-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="d1786-131">Pierwszy element w spójnej kolekcji jest `squareIt` i drugi element stanowi `num`.</span><span class="sxs-lookup"><span data-stu-id="d1786-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="d1786-132">Identyfikator `num` jest powiązana w poprzednim przykładzie na liczbę całkowitą 10 prawidłowym argumentem dla `squareIt` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="d1786-133">Drugie wyrażenie dotyczy pierwszego elementu w krotce drugi element krotki: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="d1786-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="d1786-134">Podobnie, po prostu jako identyfikator `num` i liczba całkowita 10 może być używane zamiennie, więc można identyfikator `squareIt` i wyrażenia lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="d1786-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="d1786-135">Przekaż wartość jako Argument</span><span class="sxs-lookup"><span data-stu-id="d1786-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="d1786-136">Jeśli wartość ma stan najwyższej jakości w języku, możesz przekazać go jako argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="d1786-137">Na przykład jest wspólne dla przekazywania ciągów i liczby całkowite jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="d1786-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="d1786-138">Poniższy kod przedstawia liczb całkowitych i ciągi przekazywane jako argumenty w języku F#.</span><span class="sxs-lookup"><span data-stu-id="d1786-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="d1786-139">Jeśli stanem najwyższej klasy funkcji musi być przekazywane jako argumenty w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="d1786-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="d1786-140">Należy pamiętać, że jest to pierwszy charakterystyka funkcji wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="d1786-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="d1786-141">W poniższym przykładzie funkcja `applyIt` zawiera dwa parametry `op` i `arg`.</span><span class="sxs-lookup"><span data-stu-id="d1786-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="d1786-142">Jeśli wyślesz w funkcji, która ma jeden parametr dla `op` i odpowiedniego argumentu dla funkcji `arg`, funkcja zwraca wynik zastosowania `op` do `arg`.</span><span class="sxs-lookup"><span data-stu-id="d1786-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="d1786-143">W poniższym przykładzie zarówno argumentu funkcji, jak i całkowitego argumentu są wysyłane w taki sam sposób, przy użyciu ich nazw.</span><span class="sxs-lookup"><span data-stu-id="d1786-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="d1786-144">Możliwość wysyłania funkcji jako argument do innej funkcji źródłową wspólne elementy abstrakcji w funkcjonalności języków programowania, takich jak mapy lub filtr operacji.</span><span class="sxs-lookup"><span data-stu-id="d1786-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="d1786-145">Operacja mapy, na przykład jest funkcja wyższego rzędu, która przechwytuje obliczanie udostępnionych przez funkcje, które przejrzeć listę, zrobić coś do każdego elementu, a następnie wróć do listy wyników.</span><span class="sxs-lookup"><span data-stu-id="d1786-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="d1786-146">Można zwiększyć każdy element na liście liczb całkowitych, kwadratowe każdy element lub zmienić każdy element na liście ciągi na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="d1786-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="d1786-147">Podatne część obliczeń jest proces cyklicznego tej czynności za pomocą listy i tworzy listę wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d1786-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="d1786-148">Ta część jest przechwytywane w funkcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="d1786-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="d1786-149">Wszystko, trzeba napisać dla konkretnej aplikacji, to funkcja, którą chcesz zastosować do każdego elementu listy indywidualnie (Dodawanie, squaring, zmienianie wielkości liter).</span><span class="sxs-lookup"><span data-stu-id="d1786-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="d1786-150">Że funkcja jest wysyłany jako argument do funkcji mapowania, podobnie jak `squareIt` są wysyłane do `applyIt` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1786-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="d1786-151">F# zawiera metody mapy dla większości typów kolekcji, w tym [Wyświetla](../language-reference/lists.md), [tablic](../language-reference/arrays.md), i [sekwencje](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="d1786-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="d1786-152">W poniższych przykładach używane listy.</span><span class="sxs-lookup"><span data-stu-id="d1786-152">The following examples use lists.</span></span> <span data-ttu-id="d1786-153">Składnia jest `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="d1786-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="d1786-154">Aby uzyskać więcej informacji, zobacz [Wyświetla](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="d1786-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="d1786-155">Wartość zwracana z wywołania funkcji</span><span class="sxs-lookup"><span data-stu-id="d1786-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="d1786-156">Na koniec wtedy funkcja stan najwyższej jakości w języku, należy może zwrócić go jako wartość wywołania funkcji, tak samo, jak zwrócić innych typów, takich jak liczby całkowite i ciągów.</span><span class="sxs-lookup"><span data-stu-id="d1786-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="d1786-157">Następujące wywołania funkcji zwracają liczby całkowite i ich wyświetlenie.</span><span class="sxs-lookup"><span data-stu-id="d1786-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="d1786-158">Poniższe wywołanie funkcji zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="d1786-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="d1786-159">Poniższe wywołanie funkcji zadeklarowana śródwierszowo, zwraca wartość typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="d1786-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="d1786-160">Jest wyświetlana wartość `True`.</span><span class="sxs-lookup"><span data-stu-id="d1786-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="d1786-161">Aby zwrócić funkcję jako wartość wywołania funkcji jest druga cechę funkcji wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="d1786-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="d1786-162">W poniższym przykładzie `checkFor` jest definiowany jako funkcja, która przyjmuje jeden argument `item`i zwraca nową funkcję jako jego wartość.</span><span class="sxs-lookup"><span data-stu-id="d1786-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="d1786-163">Zwrócone funkcja przyjmuje listę jako jej argument `lst`i wyszukuje `item` w `lst`.</span><span class="sxs-lookup"><span data-stu-id="d1786-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="d1786-164">Jeśli `item` jest obecny, funkcja zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="d1786-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="d1786-165">Jeśli `item` nie jest obecny, funkcja zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="d1786-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="d1786-166">Tak jak w poprzedniej sekcji, w poniższym kodzie użyto funkcji dostarczonej listy [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), aby wyszukać na liście.</span><span class="sxs-lookup"><span data-stu-id="d1786-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d1786-167">Poniższy kod używa `checkFor` Aby utworzyć nową funkcję, która przyjmuje jeden argument, listy i wyszukuje 7 na liście.</span><span class="sxs-lookup"><span data-stu-id="d1786-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="d1786-168">W poniższym przykładzie użyto najwyższej jakości stanu funkcji w języku F# do deklarowania funkcji, `compose`, która zwraca złożeniem dwóch argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
<span data-ttu-id="d1786-169">Nawet krótszych wersji zapoznać się z sekcją "Curried funkcji."</span><span class="sxs-lookup"><span data-stu-id="d1786-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="d1786-170">Poniższy kod wysyła dwie funkcje jako argumenty `compose`, z którym podjąć jeden argument tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="d1786-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="d1786-171">Wartość zwracana jest nową funkcję, która jest kompozycją argumentów dwóch funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
<span data-ttu-id="d1786-172">F# zawiera dwa operatory `<<` i `>>`, które tworzą funkcje.</span><span class="sxs-lookup"><span data-stu-id="d1786-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="d1786-173">Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest odpowiednikiem `let squareAndDouble = compose doubleIt squareIt` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1786-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="d1786-174">Poniższy przykład zwraca funkcję jako wartość wywołania funkcji tworzy prostą zgadywania gier.</span><span class="sxs-lookup"><span data-stu-id="d1786-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="d1786-175">Aby utworzyć grę, wywołaj `makeGame` wartością ma inną osobę do odgadnięcia wysyłany `target`.</span><span class="sxs-lookup"><span data-stu-id="d1786-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="d1786-176">Wartość zwrócona przez funkcję `makeGame` jest funkcją, która przyjmuje jeden argument (wynik) i raporty, czy wynik jest poprawny.</span><span class="sxs-lookup"><span data-stu-id="d1786-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="d1786-177">Poniższy kod wywoła `makeGame`, wysyłania wartości `7` dla `target`.</span><span class="sxs-lookup"><span data-stu-id="d1786-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="d1786-178">Identyfikator `playGame` jest powiązany z wyrażenia lambda zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d1786-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="d1786-179">W związku z tym `playGame` jest funkcją, która przyjmuje jako argumentem jedną wartość dla `guess`.</span><span class="sxs-lookup"><span data-stu-id="d1786-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="d1786-180">Funkcje rozwinięte</span><span class="sxs-lookup"><span data-stu-id="d1786-180">Curried Functions</span></span>

<span data-ttu-id="d1786-181">Większość przykładów w poprzedniej sekcji można napisać bardziej zwięzłym, wykorzystując niejawny *currying* w deklaracjach funkcji F#.</span><span class="sxs-lookup"><span data-stu-id="d1786-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="d1786-182">Currying jest procesem, który przekształca funkcja, która ma więcej niż jeden parametr do serii osadzonych funkcji, z których każdy ma jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d1786-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="d1786-183">W języku F# natury przenoszeni się funkcji, które mają więcej niż jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d1786-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="d1786-184">Na przykład `compose` z poprzedniej sekcji, można napisać tak, jak pokazano na poniższej zwarty styl z trzema parametrami.</span><span class="sxs-lookup"><span data-stu-id="d1786-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="d1786-185">Jednakże, wynik zależy od jeden parametr, który zwraca funkcja jeden parametr, który z kolei zwraca inną funkcję jeden parametr, jak pokazano na `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="d1786-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="d1786-186">Możesz uzyskać dostęp do tej funkcji na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="d1786-186">You can access this function in several ways.</span></span> <span data-ttu-id="d1786-187">Każdy z poniższych przykładów zwraca i wyświetla 18.</span><span class="sxs-lookup"><span data-stu-id="d1786-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="d1786-188">Możesz zastąpić `compose4` z `compose4curried` w jednym z przykładów.</span><span class="sxs-lookup"><span data-stu-id="d1786-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="d1786-189">Aby sprawdzić, czy funkcja nadal działa tak jak poprzednio, spróbuj ponownie, oryginalnym przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="d1786-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
<span data-ttu-id="d1786-190">Możesz ograniczyć currying, umieszczając parametrów w spójnych kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="d1786-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="d1786-191">Aby uzyskać więcej informacji, zobacz "Parametr wzorców" w [parametrami i argumentami](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d1786-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="d1786-192">W poniższym przykładzie użyto niejawne currying do zapisania krótszą wersję `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="d1786-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="d1786-193">Szczegóły dotyczące `makeGame` tworzy i zwraca `game` funkcji są mniej jawne, w tym formacie, ale można sprawdzić za pomocą oryginalnego przypadków testowych, czy wynik jest taki sam.</span><span class="sxs-lookup"><span data-stu-id="d1786-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="d1786-194">Aby uzyskać więcej informacji na temat currying, zobacz "Częściowe stosowanie argumentów" w [funkcji](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1786-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="d1786-195">Identyfikator i definicji funkcji są wymienne</span><span class="sxs-lookup"><span data-stu-id="d1786-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="d1786-196">Nazwa zmiennej `num` w ciągu poprzednich przykładach, daje w wyniku całkowitą 10 i nie ma Nic dziwnego to, w którym `num` jest prawidłowy, 10 ma również zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="d1786-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="d1786-197">To samo dotyczy identyfikatorów funkcji i ich wartości: gdziekolwiek nazwę funkcji mogą być używane, można użyć wyrażenia lambda, z którą jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="d1786-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="d1786-198">W poniższym przykładzie zdefiniowano `Boolean` funkcję o nazwie `isNegative`, a następnie używa nazwy funkcji i definicji funkcji zamiennie.</span><span class="sxs-lookup"><span data-stu-id="d1786-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="d1786-199">Następne trzy przykłady wszystkie przywrócić i wyświetlić `False`.</span><span class="sxs-lookup"><span data-stu-id="d1786-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="d1786-200">Aby móc go jeden krok dalej, zastąp wartość która `applyIt` jest powiązany dla `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="d1786-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="d1786-201">Funkcje są wartości pierwszej klasy w F\#</span><span class="sxs-lookup"><span data-stu-id="d1786-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="d1786-202">W przykładach w poprzedniej sekcji pokazują, że funkcje w języku F# spełniają kryteria są wartości pierwszej klasy w języku F#:</span><span class="sxs-lookup"><span data-stu-id="d1786-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="d1786-203">Można powiązać identyfikatora definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="d1786-204">Funkcję można przechowywać w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d1786-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="d1786-205">Funkcję można przekazać jako argument.</span><span class="sxs-lookup"><span data-stu-id="d1786-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="d1786-206">Funkcja może zwrócić jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1786-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d1786-207">Aby uzyskać więcej informacji na temat języka F#, zobacz [dokumentacja języka F#](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1786-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="d1786-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1786-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="d1786-209">Opis</span><span class="sxs-lookup"><span data-stu-id="d1786-209">Description</span></span>

<span data-ttu-id="d1786-210">Poniższy kod zawiera wszystkie przykłady w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d1786-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="d1786-211">Kod</span><span class="sxs-lookup"><span data-stu-id="d1786-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="d1786-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1786-212">See also</span></span>

- [<span data-ttu-id="d1786-213">Listy</span><span class="sxs-lookup"><span data-stu-id="d1786-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="d1786-214">Krotki</span><span class="sxs-lookup"><span data-stu-id="d1786-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="d1786-215">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d1786-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="d1786-216">`let` Powiązania</span><span class="sxs-lookup"><span data-stu-id="d1786-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="d1786-217">Wyrażenia lambda: `fun` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="d1786-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)