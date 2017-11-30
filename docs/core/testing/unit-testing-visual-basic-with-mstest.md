---
title: "Jednostka badanie Visual Basic .NET Core za pomocą testu dotnet i MSTest"
description: "Dowiedz się koncepcje testu jednostki w .NET Core za pośrednictwem interaktywnego środowisko budowania rozwiązania Visual Basic próbki krok po kroku przy użyciu przełącznika MSTest."
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs: vb
ms.prod: .net-core
ms.openlocfilehash: b656ae4746691f2e72eaa666542e98d4abc91069
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a><span data-ttu-id="64bed-103">Biblioteki języka Visual Basic .NET Core za pomocą testu dotnet i MStest testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="64bed-103">Unit testing Visual Basic .NET Core libraries using dotnet test and MStest</span></span>

<span data-ttu-id="64bed-104">Ten samouczek przedstawia interaktywna tworzenia przykładowe rozwiązanie krok po kroku, aby dowiedzieć się pojęcia testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="64bed-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="64bed-105">Jeśli chcesz wykonać czynności opisane w samouczku za pomocą wbudowanych rozwiązania, [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-mstest/) przed rozpoczęciem.</span><span class="sxs-lookup"><span data-stu-id="64bed-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="64bed-106">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="64bed-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="64bed-107">Tworzenie projektu źródłowego</span><span class="sxs-lookup"><span data-stu-id="64bed-107">Creating the source project</span></span>

<span data-ttu-id="64bed-108">Umożliwia otwarcie okna powłoki.</span><span class="sxs-lookup"><span data-stu-id="64bed-108">Open a shell window.</span></span> <span data-ttu-id="64bed-109">Utwórz katalog o nazwie *testowania — przy użyciu dotnet testu jednostkowego* do przechowywania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64bed-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="64bed-110">Wewnątrz tego nowego katalogu Uruchom [ `dotnet new sln` ](../tools/dotnet-new.md) do tworzenia nowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64bed-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="64bed-111">Takie rozwiązanie ułatwia zarządzanie biblioteki klas i jednostkowy projekt testowy.</span><span class="sxs-lookup"><span data-stu-id="64bed-111">This practice makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="64bed-112">Utwórz katalog rozwiązania *PrimeService* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64bed-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="64bed-113">Masz dotychczasowych następującą strukturę katalogów i plików:</span><span class="sxs-lookup"><span data-stu-id="64bed-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="64bed-114">Wprowadź *PrimeService* bieżącego katalogu i uruchom [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) do tworzenia projektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="64bed-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="64bed-115">Zmień nazwę *Class1.VB* do *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="64bed-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="64bed-116">Aby użyć projektowanie oparte na testach (TDD), należy utworzyć niepowodzenie wykonania `PrimeService` klasy:</span><span class="sxs-lookup"><span data-stu-id="64bed-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="64bed-117">Zmień katalog z powrotem do *jednostki — testowanie vb — przy użyciu stest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64bed-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="64bed-118">Uruchom [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) można dodać projektu biblioteki klas do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="64bed-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="64bed-119">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="64bed-119">Creating the test project</span></span>

<span data-ttu-id="64bed-120">Następnie należy utworzyć *PrimeService.Tests* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64bed-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="64bed-121">Następujące konspektu przedstawia strukturę katalogów:</span><span class="sxs-lookup"><span data-stu-id="64bed-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="64bed-122">Wprowadź *PrimeService.Tests* katalogu bieżącego katalogu i Utwórz nowy projekt za pomocą [ `dotnet new mstest -lang VB` ](../tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="64bed-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="64bed-123">To polecenie tworzy projekt testowy używającą xUnit jako biblioteka testów.</span><span class="sxs-lookup"><span data-stu-id="64bed-123">This command creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="64bed-124">Wygenerowanego szablonu konfiguruje uruchamiający w *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="64bed-124">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
<PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
<PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
<PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="64bed-125">Projekt testowy wymaga inne pakiety do tworzenia i uruchamiania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="64bed-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="64bed-126">`dotnet new`w poprzednim kroku dodane MSTest i MSTest runner.</span><span class="sxs-lookup"><span data-stu-id="64bed-126">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="64bed-127">Teraz Dodaj `PrimeService` biblioteki klas jako zależność od innego projektu.</span><span class="sxs-lookup"><span data-stu-id="64bed-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="64bed-128">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="64bed-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="64bed-129">Widoczny cały plik w [przykłady repozytorium](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="64bed-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="64bed-130">Masz następujące układu ostatecznego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="64bed-130">You have the following final solution layout:</span></span>

```
/unit-testing-vb-using-mstest
    unit-testing-vb-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="64bed-131">Wykonanie [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) w *jednostki — testowanie vb — przy użyciu mstest* katalogu.</span><span class="sxs-lookup"><span data-stu-id="64bed-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-using-mstest* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="64bed-132">Tworzenie pierwszego testu</span><span class="sxs-lookup"><span data-stu-id="64bed-132">Creating the first test</span></span>

<span data-ttu-id="64bed-133">Podejście TDD odwołuje się do pisania niepowodzeniu jednego testu, co Przekaż, a następnie powtórzyć proces.</span><span class="sxs-lookup"><span data-stu-id="64bed-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="64bed-134">Usuń *UnitTest1.vb* z *PrimeService.Tests* katalogu i Utwórz nowy plik Visual Basic o nazwie *PrimeService_IsPrimeShould.VB*.</span><span class="sxs-lookup"><span data-stu-id="64bed-134">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="64bed-135">Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="64bed-135">Add the following code:</span></span>

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="64bed-136">`<TestClass>` Atrybut wskazuje klasę, która zawiera testy.</span><span class="sxs-lookup"><span data-stu-id="64bed-136">The `<TestClass>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="64bed-137">`<TestMethod>` Atrybut oznacza metodę, która jest uruchamiana przez moduł uruchamiający.</span><span class="sxs-lookup"><span data-stu-id="64bed-137">The `<TestMethod>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="64bed-138">Z *jednostki — testowanie vb — przy użyciu mstest*, wykonać [ `dotnet test` ](../tools/dotnet-test.md) do tworzenia testów i biblioteki klas, a następnie uruchom testy.</span><span class="sxs-lookup"><span data-stu-id="64bed-138">From the *unit-testing-vb-using-mstest*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="64bed-139">Moduł uruchamiający xUnit zawiera punkt wejścia programu do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="64bed-139">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="64bed-140">`dotnet test`Uruchamia uruchamiający przy użyciu jednostkowy projekt testowy, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="64bed-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="64bed-141">Test zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64bed-141">Your test fails.</span></span> <span data-ttu-id="64bed-142">Nie utworzono jeszcze implementacji.</span><span class="sxs-lookup"><span data-stu-id="64bed-142">You haven't created the implementation yet.</span></span> <span data-ttu-id="64bed-143">Należy ten test przez pisania kodu najprostsza w `PrimeService` klasy, która działa:</span><span class="sxs-lookup"><span data-stu-id="64bed-143">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="64bed-144">W *jednostki — testowanie vb — przy użyciu mstest* katalogu, uruchom `dotnet test` ponownie.</span><span class="sxs-lookup"><span data-stu-id="64bed-144">In the *unit-testing-vb-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="64bed-145">`dotnet test` Polecenia uruchamiane kompilacji dla `PrimeService` projektu i następnie `PrimeService.Tests` projektu.</span><span class="sxs-lookup"><span data-stu-id="64bed-145">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="64bed-146">Po utworzeniu oba projekty, jest uruchamiana ta pojedynczy test.</span><span class="sxs-lookup"><span data-stu-id="64bed-146">After building both projects, it runs this single test.</span></span> <span data-ttu-id="64bed-147">Przekazuje ono.</span><span class="sxs-lookup"><span data-stu-id="64bed-147">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="64bed-148">Dodawanie więcej funkcji.</span><span class="sxs-lookup"><span data-stu-id="64bed-148">Adding more features</span></span>

<span data-ttu-id="64bed-149">Teraz, kiedy dokonano jeden test przekazać nadszedł czas na zapis więcej.</span><span class="sxs-lookup"><span data-stu-id="64bed-149">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="64bed-150">Istnieje kilka innych przypadków proste dla liczb pierwszych: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="64bed-150">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="64bed-151">Możesz dodać tych przypadkach jako nowe testy z `<TestMethod>` atrybut, ale szybko staje się nużące.</span><span class="sxs-lookup"><span data-stu-id="64bed-151">You could add those cases as new tests with the `<TestMethod>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="64bed-152">Istnieją inne atrybuty xUnit, które pozwalają na zapis zestaw testów podobne.</span><span class="sxs-lookup"><span data-stu-id="64bed-152">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="64bed-153">A `<DataTestMethod>` atrybut reprezentuje zestaw testów, wykonanie tego samego kodu, które mają różne argumenty wejściowe.</span><span class="sxs-lookup"><span data-stu-id="64bed-153">A `<DataTestMethod>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="64bed-154">Można użyć `<DataRow>` atrybutu, aby określić wartości dla tych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="64bed-154">You can use the `<DataRow>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="64bed-155">Zamiast tworzyć nowe testy, należy zastosować te atrybuty można utworzyć jeden teorii.</span><span class="sxs-lookup"><span data-stu-id="64bed-155">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="64bed-156">Teorii jest metodę, która sprawdza kilka wartości mniejszej niż dwa, czyli o najniższej liczbie pierwsze:</span><span class="sxs-lookup"><span data-stu-id="64bed-156">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="64bed-157">Uruchom `dotnet test`, i dwa pola spośród wymienionych testów kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64bed-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="64bed-158">Aby wszystkie karty testy, należy zmienić `if` klauzuli na początku metody:</span><span class="sxs-lookup"><span data-stu-id="64bed-158">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="64bed-159">Nadal Iterowanie przez dodanie większej liczby testów, więcej teorii i więcej kodu w bibliotece głównego.</span><span class="sxs-lookup"><span data-stu-id="64bed-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="64bed-160">Masz [Zakończono wersji testów](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) i [zakończenia wdrożenia biblioteki](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="64bed-160">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-mstest/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="64bed-161">Został utworzony małych biblioteki i zestaw testów jednostkowych dla tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="64bed-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="64bed-162">Zostały strukturę rozwiązania, aby dodać nowe pakiety i testów jest częścią Normalny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="64bed-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="64bed-163">Już skoncentrowany większość czasu i uwagi na temat rozwiązywania problemów celów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64bed-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>