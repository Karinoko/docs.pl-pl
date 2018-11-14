---
title: Praca z kolekcjami — wprowadzenie do C# samouczek
description: Dowiedz się, C# eksplorując kolekcji listy, w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: eaf921be2bd50b6e346f57f42e17f151ff336821
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205285"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="8e9d2-103">Dowiedz się, jak zarządzać zbierania danych przy użyciu typu listy ogólnej</span><span class="sxs-lookup"><span data-stu-id="8e9d2-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="8e9d2-104">Ten Samouczek wprowadzający zawiera wprowadzenie do C# język oraz znasz podstawy <xref:System.Collections.Generic.List%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="8e9d2-105">W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="8e9d2-106">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="8e9d2-107">Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md), wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="8e9d2-108">Przykład podstawowa lista</span><span class="sxs-lookup"><span data-stu-id="8e9d2-108">A basic list example</span></span>

<span data-ttu-id="8e9d2-109">Utwórz katalog o nazwie **samouczek**.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-109">Create a directory named **list-tutorial**.</span></span> <span data-ttu-id="8e9d2-110">Upewnij, że bieżącego katalogu i uruchom `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-110">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="8e9d2-111">Jeśli właśnie został ukończony [Rozpocznij pracę z platformą .NET w 10 minut](https://www.microsoft.com/net), możesz nadal korzystać z aplikacji myApp, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-111">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>

<span data-ttu-id="8e9d2-112">Otwórz **Program.cs** w ulubionym edytorze i Zastąp istniejący kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="8e9d2-113">Zastąp `<name>` z Twoją nazwą.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="8e9d2-114">Zapisz **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-114">Save **Program.cs**.</span></span> <span data-ttu-id="8e9d2-115">Typ `dotnet run` w oknie konsoli do wypróbowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="8e9d2-116">Została właśnie utworzona lista ciągów, dodane trzy nazwy do tej listy i drukowane nazwy w całości wielkimi.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="8e9d2-117">Używasz pojęcia, które wyjaśniono w samouczkach wcześniej pętli na liście.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-117">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="8e9d2-118">Kod, aby wyświetlić nazwy sprawia, że użycie [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-118">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="8e9d2-119">Kiedy należy poprzedzić `string` z `$` kodu C# można osadzić w deklaracji ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="8e9d2-120">Rzeczywistego ciągu zastępuje wartość, która generuje kod C#.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="8e9d2-121">W tym przykładzie zastępuje `{name.ToUpper()}` przy użyciu nazwy, konwertowane na wielkie litery, ponieważ wywołujesz <xref:System.String.ToUpper%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="8e9d2-122">Możemy kontynuować Eksplorowanie.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-122">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="8e9d2-123">Modyfikowanie zawartości listy</span><span class="sxs-lookup"><span data-stu-id="8e9d2-123">Modify list contents</span></span>

<span data-ttu-id="8e9d2-124">Kolekcja utworzona używa <xref:System.Collections.Generic.List%601> typu.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="8e9d2-125">Tego typu przechowuje elementów.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-125">This type stores sequences of elements.</span></span> <span data-ttu-id="8e9d2-126">Należy określić typ elementów między nawiasami.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-126">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="8e9d2-127">Jednym ważnym aspektem to <xref:System.Collections.Generic.List%601> typ jest, może rosnąć lub maleć, dzięki któremu można dodawać lub usuwać elementy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="8e9d2-128">Dodaj ten kod przed tagiem zamykającym `}` w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-128">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="8e9d2-129">Dwa więcej nazw zostały dodane na końcu listy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="8e9d2-130">Został również usunięty jeden także.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-130">You've also removed one as well.</span></span> <span data-ttu-id="8e9d2-131">Zapisz plik i typ `dotnet run` do wypróbowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-131">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="8e9d2-132"><xref:System.Collections.Generic.List%601> Umożliwia odwoływać się do pojedynczych elementów przez **indeksu** także.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="8e9d2-133">Umieść indeksu między `[` i `]` po nazwie listy tokenów.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="8e9d2-134">C#używa pierwszego indeksu 0.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="8e9d2-135">Dodaj następujący kod bezpośrednio poniżej kod, który właśnie został dodany, a następnie spróbuj go:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="8e9d2-136">Nie masz dostępu do indeksu poza koniec listy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="8e9d2-137">Należy pamiętać, że indeksy rozpoczynają się od 0, dlatego największego indeksu nieprawidłowy jest jednym mniejszy niż liczba elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="8e9d2-138">Możesz sprawdzić, jak długo używa listy <xref:System.Collections.Generic.List%601.Count%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="8e9d2-139">Dodaj następujący kod na końcu metody Main:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="8e9d2-140">Zapisz plik i typ `dotnet run` ponownie, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-140">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="8e9d2-141">Wyszukiwanie i sortowanie list</span><span class="sxs-lookup"><span data-stu-id="8e9d2-141">Search and sort lists</span></span>

<span data-ttu-id="8e9d2-142">Nasze przykłady za pomocą list stosunkowo mały, ale aplikacje często może utworzyć listy o wiele więcej elementów, czasami numerowania w tysiącach.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="8e9d2-143">Aby znaleźć elementy w tych kolekcjach większe, musisz wyszukiwania na liście dla różnych elementów.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="8e9d2-144"><xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda wyszukuje element i zwraca indeks elementu.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="8e9d2-145">Dodaj następujący kod na końcu Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-145">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="8e9d2-146">Można również sortować elementy na liście.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="8e9d2-147"><xref:System.Collections.Generic.List%601.Sort%2A> Metoda sortuje wszystkie elementy na liście w kolejności ich normalne (alfabetycznie w przypadku ciągów znaków).</span><span class="sxs-lookup"><span data-stu-id="8e9d2-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="8e9d2-148">Dodaj następujący kod do dolnej części naszych `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="8e9d2-149">Zapisywanie pliku i typu `dotnet run` do wypróbowania tej najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="8e9d2-150">Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="8e9d2-151">Który sprawia, że łatwiej rozpocząć pracę z nową przykładową.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="8e9d2-152">Zmiana nazwy Twojego `Main` metodę, aby `WorkingWithStrings` i zapisywać nowy `Main` metodę, która wywołuje `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="8e9d2-153">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-153">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="8e9d2-154">Listę innych typów</span><span class="sxs-lookup"><span data-stu-id="8e9d2-154">Lists of other types</span></span>

<span data-ttu-id="8e9d2-155">Wcześniej użyto `string` typu na listach do tej pory.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="8e9d2-156">Upewnijmy się <xref:System.Collections.Generic.List%601> przy użyciu innego typu.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="8e9d2-157">Utwórzmy zbioru liczb.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="8e9d2-158">Dodaj następujący kod do dolnej części nowej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="8e9d2-159">Który tworzy listę liczb całkowitych i ustawia pierwszych dwóch liczb całkowitych na wartości 1.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="8e9d2-160">Są to dwie pierwsze wartości *sekwencji Fibonacci*, sekwencji liczb.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="8e9d2-161">Każdy kolejny numer Fibonacci zostanie znaleziony, wykonując sumie poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="8e9d2-162">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8e9d2-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="8e9d2-163">Zapisywanie pliku i typu `dotnet run` aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="8e9d2-164">Skoncentrować się na tylko w tej sekcji, możesz przekształcić w komentarz kod, który wywołuje `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="8e9d2-165">Po prostu umieść dwa `/` znaków poprzedzającymi wywołania podobnie do następującego: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="8e9d2-166">Wyzwanie</span><span class="sxs-lookup"><span data-stu-id="8e9d2-166">Challenge</span></span>

<span data-ttu-id="8e9d2-167">Zobacz, można umieścić ze sobą pewne pojęcia z tego i starszych wersji lekcje.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="8e9d2-168">Rozwiń węzeł, na jakie dołączeniu do tej pory z międzynarodowymi numerami identyfikującymi Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="8e9d2-169">Spróbuj napisać kod, aby wygenerować pierwszych 20 cyfr w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="8e9d2-170">(Wskazówka 20 numer Fibonacci jest 6765).</span><span class="sxs-lookup"><span data-stu-id="8e9d2-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="8e9d2-171">Ukończenie wyzwania</span><span class="sxs-lookup"><span data-stu-id="8e9d2-171">Complete challenge</span></span>

<span data-ttu-id="8e9d2-172">Przykładowe rozwiązanie, możesz zobaczyć [spojrzenie na Zakończono przykładowego kodu w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="8e9d2-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="8e9d2-173">Z każdą iteracją pętli tworzenia ostatnich dwóch liczb całkowitych na liście sumowanie je, a następnie dodanie wartości do listy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="8e9d2-174">Pętla powtarza się, aż 20 elementów zostały dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="8e9d2-175">Gratulacje, pomyślnie ukończono samouczek listy.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="8e9d2-176">Możesz kontynuować [wprowadzenie do klas](introduction-to-classes.md) samouczków w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="8e9d2-177">Dowiedz się więcej o pracy z `List` wpisać [.NET — przewodnik](../../../standard/index.md) tematu [kolekcje](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e9d2-177">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="8e9d2-178">Ponadto dowiesz się o innych typach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8e9d2-178">You'll also learn about many other collection types.</span></span>