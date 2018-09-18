---
title: 'Samouczek: Pisanie Twojego pierwszego analizator i poprawkę kodu'
description: Ten samouczek zawiera instrukcje krok po kroku kompilacji analizator i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (interfejsy API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 2959fe3008bfca972d3a164ed27d05c2a8b0e69a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970269"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="11368-103">Samouczek: Pisanie Twojego pierwszego analizator i poprawkę kodu</span><span class="sxs-lookup"><span data-stu-id="11368-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="11368-104">Zestaw SDK platformy kompilatora .NET zapewnia narzędzia potrzebne do tworzenia niestandardowych ostrzeżenia tego docelowego języka C# lub kod języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11368-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="11368-105">Twoje **analizatora** zawiera kod, który rozpoznaje naruszenia reguły.</span><span class="sxs-lookup"><span data-stu-id="11368-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="11368-106">Twoje **poprawki kodu** zawiera kod, który poprawia naruszenie.</span><span class="sxs-lookup"><span data-stu-id="11368-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="11368-107">Reguły, które można zaimplementować może być cokolwiek — od struktury kodu w celu kodowania styl do konwencji nazewnictwa i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="11368-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="11368-108">Platforma kompilatora .NET zapewnia platformę na uruchamianie analizy, programistom pisania kodu i naprawianie kodu funkcji wszystkich interfejsie użytkownika Visual Studio: wyświetlanie faliste linie w edytorze podczas wypełniania Visual Studio liście błędów, tworzenia "żarówka" sugestie i wyświetlanie podglądu sugerowanej poprawki.</span><span class="sxs-lookup"><span data-stu-id="11368-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="11368-109">W tym samouczku dowiesz się o tworzenie **analizatora** i towarzyszące **poprawki kodu** przy użyciu interfejsów API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="11368-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="11368-110">Analizator jest sposób wykonaj analizę kodu źródłowego i zgłosić problem do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11368-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="11368-111">Opcjonalnie analizator oferuje również poprawki kodu, reprezentujący zmiany do kodu źródłowego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11368-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="11368-112">Ten samouczek tworzy analizatora, który umożliwia znalezienie lokalnych deklaracji zmiennych, które mogą być deklarowane przy użyciu `const` modyfikator to.</span><span class="sxs-lookup"><span data-stu-id="11368-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="11368-113">Towarzyszący poprawki kodu modyfikuje te deklaracje, aby dodać `const` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="11368-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11368-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="11368-114">Prerequisites</span></span>

* [<span data-ttu-id="11368-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="11368-115">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="11368-116">Należy zainstalować **zestawu SDK platformy kompilatora .NET**:</span><span class="sxs-lookup"><span data-stu-id="11368-116">You'll need to install the **.NET Compiler Platform SDK**:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="11368-117">Istnieje kilka kroków do tworzenia i weryfikowania Twojej analizatora:</span><span class="sxs-lookup"><span data-stu-id="11368-117">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="11368-118">Utwórz rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="11368-118">Create the solution.</span></span>
1. <span data-ttu-id="11368-119">Zarejestruj analizatora nazwę i opis.</span><span class="sxs-lookup"><span data-stu-id="11368-119">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="11368-120">Ostrzeżenia dotyczące analizatora raportu i zalecenia.</span><span class="sxs-lookup"><span data-stu-id="11368-120">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="11368-121">Implementowanie poprawki kodu, aby zaakceptować zalecenia.</span><span class="sxs-lookup"><span data-stu-id="11368-121">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="11368-122">Zwiększ analizy za pomocą testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="11368-122">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="11368-123">Zapoznaj się z szablonu analizatora</span><span class="sxs-lookup"><span data-stu-id="11368-123">Explore the analyzer template</span></span>

<span data-ttu-id="11368-124">Twoje analizatora raporty użytkownikowi lokalne deklaracje zmiennych, które mogą być konwertowane na lokalnym stałymi.</span><span class="sxs-lookup"><span data-stu-id="11368-124">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="11368-125">Na przykład rozważmy następujący kod:</span><span class="sxs-lookup"><span data-stu-id="11368-125">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="11368-126">W powyższym kodzie `x` jest przypisywana wartość stała i nie jest nigdy modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="11368-126">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="11368-127">Mogą być deklarowane przy użyciu `const` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="11368-127">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="11368-128">Analizy, aby ustalić, czy zmienna jest możliwe stałej jest zaangażowana wymagających analizy składni, wyrażenia inicjatora stałej analizy i analizy przepływu danych, aby upewnić się, że zmienna nigdy nie są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="11368-128">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="11368-129">Platforma kompilatora .NET zawiera interfejsy API, które ułatwiają wykonywanie tej analizy.</span><span class="sxs-lookup"><span data-stu-id="11368-129">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="11368-130">Pierwszym krokiem jest utworzenie nowego języka C# **Analyzer przy użyciu poprawki kodu** projektu.</span><span class="sxs-lookup"><span data-stu-id="11368-130">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

* <span data-ttu-id="11368-131">W programie Visual Studio, wybierz **Plik > Nowy > Projekt...**  Aby wyświetlić okno dialogowe Nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="11368-131">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
* <span data-ttu-id="11368-132">W obszarze **Visual C# > rozszerzalności**, wybierz **Analyzer przy użyciu poprawki kodu (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="11368-132">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
* <span data-ttu-id="11368-133">Nazwij swój projekt "**MakeConst**" i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="11368-133">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="11368-134">Analizator za pomocą szablonu poprawki kodu tworzy trzy projekty: jedna z nich zawiera analizator i poprawki kodu, druga jest projekt testów jednostkowych, a trzeci jest projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="11368-134">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="11368-135">Domyślny projekt startowy jest projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="11368-135">The default startup project is the VSIX project.</span></span> <span data-ttu-id="11368-136">Naciśnij klawisz **F5** można uruchomić projekt VSIX.</span><span class="sxs-lookup"><span data-stu-id="11368-136">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="11368-137">Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, który został załadowany z nowego analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-137">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="11368-138">Po uruchomieniu analizatora sieci, możesz uruchomić drugą kopię programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-138">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="11368-139">Ta druga kopia używa gałęzi rejestru różnych do przechowywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="11368-139">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="11368-140">To pozwala odróżnić visual ustawienia w dwóch kopii programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-140">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="11368-141">Możesz wybrać inny motyw eksperymentalne uruchomieniu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-141">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="11368-142">Ponadto nie są przenoszone ustawień lub zaloguj się do programu Visual Studio konta przy użyciu eksperymentalnym uruchamiania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-142">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="11368-143">Które utrzymuje ustawienia są różne.</span><span class="sxs-lookup"><span data-stu-id="11368-143">That keeps the settings different.</span></span>

<span data-ttu-id="11368-144">W drugim wystąpieniu programu Visual Studio został uruchomiony Utwórz nowy projekt aplikacji Konsolowej C# (.NET Core lub .NET Framework projekt będzie praca — praca analizatory na poziomie źródła.) Umieść kursor nad token z linią falistą i pojawia się tekst ostrzeżenia, dostarczone przez analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-144">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="11368-145">Ten szablon tworzy analizatora, który zgłosi ostrzeżenie w każdej deklaracji typu, których nazwa typu zawiera małe litery, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="11368-145">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Analizator raportowania ostrzeżenie](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="11368-147">Szablon zawiera także poprawki kodu, który zmienia wszelkie nazwy typu zawierającego małe litery na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="11368-147">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="11368-148">Kliknięcie żarówki wyświetlane z ostrzeżeniem, aby wyświetlić sugerowane zmiany.</span><span class="sxs-lookup"><span data-stu-id="11368-148">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="11368-149">Akceptuje aktualizacje sugerowane zmiany nazwy typu i wszystkie odwołania do tego typu w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="11368-149">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="11368-150">Teraz, gdy wiesz początkowej analizator w działaniu, zamknij drugie wystąpienie programu Visual Studio i powrócić do projektu analizator.</span><span class="sxs-lookup"><span data-stu-id="11368-150">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="11368-151">Nie trzeba uruchomić drugą kopię programu Visual Studio i Utwórz nowy kod, aby przetestować każda zmiana w analizatorze usługi.</span><span class="sxs-lookup"><span data-stu-id="11368-151">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="11368-152">Ten szablon tworzy również projekt testów jednostkowych dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="11368-152">The template also creates a unit test project for you.</span></span> <span data-ttu-id="11368-153">Ten projekt zawiera dwie próby.</span><span class="sxs-lookup"><span data-stu-id="11368-153">That project contains two tests.</span></span> <span data-ttu-id="11368-154">`TestMethod1` przedstawia typowy format test, który analizuje kod bez powodowania diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="11368-154">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="11368-155">`TestMethod2` Pokazuje format test, który wyzwala Diagnostyka, a następnie stosuje poprawki sugerowane kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-155">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="11368-156">Podczas tworzenia usługi analizator i poprawki kodu, piszesz testy dla struktur inny kod, aby sprawdzić swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="11368-156">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="11368-157">Testy jednostkowe dla analizatory są znacznie szybciej niż w przypadku testowania ich interaktywnie przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-157">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="11368-158">Analizatora testów jednostkowych są doskonałym narzędziem, gdy wiesz, jaki kod konstrukcje powinien i nie powinny wyzwalać swoje analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-158">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="11368-159">Podczas ładowania analizatora użytkownika w innej kopii programu Visual Studio jest doskonałym narzędziem eksplorować i Znajdź konstrukcji, które mogą nie mieć wiesz jeszcze.</span><span class="sxs-lookup"><span data-stu-id="11368-159">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="11368-160">Tworzenie analizatora rejestracji</span><span class="sxs-lookup"><span data-stu-id="11368-160">Create analyzer registrations</span></span>

<span data-ttu-id="11368-161">Ten szablon tworzy wstępne `DiagnosticAnalyzer` klasy w **MakeConstAnalyzer.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="11368-161">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="11368-162">Ta początkowa analizatora pokazuje dwie ważne właściwości każdego analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-162">This initial analyzer shows two important properties of every analyzer.</span></span>

* <span data-ttu-id="11368-163">Należy podać co analizatora diagnostycznego `[DiagnosticAnalyzer]` atrybut, który opisuje język działa na.</span><span class="sxs-lookup"><span data-stu-id="11368-163">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
* <span data-ttu-id="11368-164">Każdy analizatora diagnostycznego musi pochodzić od klasy <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> klasy.</span><span class="sxs-lookup"><span data-stu-id="11368-164">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="11368-165">Szablon zawiera również podstawowe funkcje, które są częścią dowolnego analizatora:</span><span class="sxs-lookup"><span data-stu-id="11368-165">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="11368-166">Rejestrowanie akcji.</span><span class="sxs-lookup"><span data-stu-id="11368-166">Register actions.</span></span> <span data-ttu-id="11368-167">Działania reprezentują zmiany kodu, które powinny wyzwalać swoje analizator badanie kodu za naruszenia.</span><span class="sxs-lookup"><span data-stu-id="11368-167">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="11368-168">Gdy program Visual Studio wykryje edycji kodu, zgodne zarejestrowanych akcji, wywołuje zarejestrowanej metody swoje analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-168">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="11368-169">Utwórz diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="11368-169">Create diagnostics.</span></span> <span data-ttu-id="11368-170">Gdy Twoja analizatora wykryje naruszenie, tworzy diagnostycznych obiekt, który używa programu Visual Studio w celu powiadamia użytkownika o naruszenie.</span><span class="sxs-lookup"><span data-stu-id="11368-170">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="11368-171">Rejestrowanie akcji w zastąpienie metody <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="11368-171">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="11368-172">W tym samouczku będziesz odwiedź **węzłów składni** szuka deklaracji lokalnego i zobaczyć, który z tych wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="11368-172">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="11368-173">Jeśli deklaracja może być stała, Twoje analizatora utworzysz i zgłaszać diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="11368-173">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="11368-174">Pierwszym krokiem jest zaktualizowanie stałe rejestracji i `Initialize` metody, dzięki czemu te stałe wskazują swoje analizatora "Wprowadzić Const".</span><span class="sxs-lookup"><span data-stu-id="11368-174">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="11368-175">Większość stałych ciągów są definiowane w pliku zasobów ciągu.</span><span class="sxs-lookup"><span data-stu-id="11368-175">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="11368-176">Należy przestrzegać tej praktyki dla lokalizacji łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="11368-176">You should follow that practice for easier localization.</span></span> <span data-ttu-id="11368-177">Otwórz **Resources.resx** plik **MakeConst** projektu analizator.</span><span class="sxs-lookup"><span data-stu-id="11368-177">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="11368-178">Spowoduje to wyświetlenie edytora zasobów.</span><span class="sxs-lookup"><span data-stu-id="11368-178">This displays the resource editor.</span></span> <span data-ttu-id="11368-179">Zaktualizuj zasoby w postaci ciągów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="11368-179">Update the string resources as follows:</span></span>

* <span data-ttu-id="11368-180">Zmiana `AnalyzerTitle` "Zmiennej może być przeprowadzone stałej".</span><span class="sxs-lookup"><span data-stu-id="11368-180">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
* <span data-ttu-id="11368-181">Zmiana `AnalyzerMessageFormat` "Może być przeprowadzone stałej".</span><span class="sxs-lookup"><span data-stu-id="11368-181">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
* <span data-ttu-id="11368-182">Zmiana `AnalyzerDescription` się "stałe".</span><span class="sxs-lookup"><span data-stu-id="11368-182">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="11368-183">Ponadto zmienić **modyfikator dostępu** menu rozwijane `public`.</span><span class="sxs-lookup"><span data-stu-id="11368-183">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="11368-184">Które ułatwia korzystanie z tych stałych w testach jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="11368-184">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="11368-185">Po zakończeniu, Edytor zasobów powinna być taka jak wykonaj ilustracji pokazano:</span><span class="sxs-lookup"><span data-stu-id="11368-185">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Aktualizują zasoby z ciągów](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="11368-187">Pozostałe zmiany znajdują się w pliku analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-187">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="11368-188">Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-188">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="11368-189">Zmień zarejestrowanych akcji z jednego, który działa na symboli na taki, który działa na składni.</span><span class="sxs-lookup"><span data-stu-id="11368-189">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="11368-190">W `MakeConstAnalyzerAnalyzer.Initialize` metody Znajdź wiersz, który rejestruje działanie symboli:</span><span class="sxs-lookup"><span data-stu-id="11368-190">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="11368-191">Zastąp go następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="11368-191">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="11368-192">Po tej zmianie, można usunąć `AnalyzeSymbol` metody.</span><span class="sxs-lookup"><span data-stu-id="11368-192">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="11368-193">Sprawdza, czy ten analizatora <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, a nie <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> instrukcji.</span><span class="sxs-lookup"><span data-stu-id="11368-193">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="11368-194">Należy zauważyć, że `AnalyzeNode` ma czerwone faliste linie w nim.</span><span class="sxs-lookup"><span data-stu-id="11368-194">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="11368-195">Kod został właśnie dodany odwołania `AnalyzeNode` metody, która nie została zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="11368-195">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="11368-196">Należy zadeklarować tej metody, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="11368-196">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="11368-197">Zmiana `Category` do "Obciążenie" w **MakeConstAnalyzer.cs** jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="11368-197">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="11368-198">Znajdź lokalne deklaracje, które może być wartością stałą</span><span class="sxs-lookup"><span data-stu-id="11368-198">Find local declarations that could be const</span></span>

<span data-ttu-id="11368-199">Nadszedł czas na zapis pierwszą wersję `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="11368-199">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="11368-200">Powinno to wyglądać dla jednej deklaracji lokalnej, która może być `const` , ale nie jest dostępna, podobnie do poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="11368-200">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="11368-201">Pierwszym krokiem jest aby znaleźć lokalne deklaracje.</span><span class="sxs-lookup"><span data-stu-id="11368-201">The first step is to find local declarations.</span></span> <span data-ttu-id="11368-202">Dodaj następujący kod do `AnalyzeNode` w **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="11368-202">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="11368-203">To rzutowanie zawsze powiedzie się, ponieważ Twoje analizatora zarejestrowane zmiany lokalne deklaracje i jedynie lokalne deklaracje.</span><span class="sxs-lookup"><span data-stu-id="11368-203">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="11368-204">Żaden inny typ węzła wyzwala wywołanie usługi `AnalyzeNode` metody.</span><span class="sxs-lookup"><span data-stu-id="11368-204">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="11368-205">Następnie sprawdź deklaracji pod kątem dowolnego `const` modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="11368-205">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="11368-206">Jeśli okaże się ich, zwracać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="11368-206">If you find them, return immediately.</span></span> <span data-ttu-id="11368-207">Poniższy kod wyszukuje dowolny `const` modyfikatorów na lokalnej deklaracji:</span><span class="sxs-lookup"><span data-stu-id="11368-207">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="11368-208">Na koniec należy sprawdzić, czy zmienna może być `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-208">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="11368-209">Oznacza to, że właściwe nigdy nie została przypisana po inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="11368-209">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="11368-210">Możesz wykonać niektóre przy użyciu analizy semantycznej <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="11368-210">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="11368-211">Możesz użyć `context` argumentu, aby ustalić, czy mogą być tworzone deklaracji zmiennej lokalnej `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-211">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="11368-212">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="11368-212">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="11368-213">Dowiedz się więcej z tego artykułu, który obejmuje [modeli semantycznych](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="11368-213">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="11368-214">Użyjesz <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> przeprowadzić analizę przepływu danych w instrukcji deklaracji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="11368-214">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="11368-215">Następnie przy użyciu wyniki analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywane z nową wartością miejscach.</span><span class="sxs-lookup"><span data-stu-id="11368-215">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="11368-216">Wywołaj <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodę rozszerzenia, aby pobrać <xref:Microsoft.CodeAnalysis.ILocalSymbol> dla zmiennej i upewnij się, że nie jest zawarte <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> zbierania danych przepływ analizy.</span><span class="sxs-lookup"><span data-stu-id="11368-216">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="11368-217">Dodaj następujący kod na końcu `AnalyzeNode` metody:</span><span class="sxs-lookup"><span data-stu-id="11368-217">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="11368-218">Kod, właśnie został dodany zapewnia nie jest modyfikowana zmienna, a może być przeprowadzana `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-218">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="11368-219">Nadszedł czas, aby zgłosić diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="11368-219">It's time to raise the diagnostic.</span></span> <span data-ttu-id="11368-220">Dodaj następujący kod w ostatnim wierszu w `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="11368-220">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="11368-221">Można sprawdzić postęp, naciskając klawisz **F5** do uruchamiania analizatora sieci.</span><span class="sxs-lookup"><span data-stu-id="11368-221">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="11368-222">Możesz załadować aplikację konsolową, która została utworzona wcześniej, a następnie dodaj następujący kod testu:</span><span class="sxs-lookup"><span data-stu-id="11368-222">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="11368-223">Żarówki, powinien zostać wyświetlony, a Twoje analizatora powinien wysyłać raporty diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="11368-223">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="11368-224">Jednak żarówki nadal używa poprawki kodu wygenerowanego szablonu i informuje, że może on wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="11368-224">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="11368-225">W następnej sekcji objaśniono sposób pisania poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-225">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="11368-226">Zapis poprawki kodu</span><span class="sxs-lookup"><span data-stu-id="11368-226">Write the code fix</span></span>

<span data-ttu-id="11368-227">Analizator może zapewnić jedną lub więcej poprawek kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-227">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="11368-228">Poprawki kodu definiuje edycji, odnoszący się do zgłoszonego problemu.</span><span class="sxs-lookup"><span data-stu-id="11368-228">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="11368-229">Dla analizatora, który został utworzony można podać poprawki kodu, który wstawia const — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="11368-229">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="11368-230">Użytkownik wybiera z żarówki interfejsu użytkownika w edytorze i programu Visual Studio zmian kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-230">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="11368-231">Otwórz **MakeConstCodeFixProvider.cs** pliku dodawane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="11368-231">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="11368-232">Ta poprawka kodu jest już powiązaną Identyfikator diagnostyczny generowane przez użytkownika analizatora diagnostycznego, ale nie implementuje on jeszcze przekształcenie prawo kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-232">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="11368-233">Najpierw należy usunąć niektóre kod szablonu.</span><span class="sxs-lookup"><span data-stu-id="11368-233">First you should remove some of the template code.</span></span> <span data-ttu-id="11368-234">Zmień ciąg tytułu "Marka stała":</span><span class="sxs-lookup"><span data-stu-id="11368-234">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="11368-235">Następnie należy usunąć `MakeUppercaseAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="11368-235">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="11368-236">Nie ma już zastosowania.</span><span class="sxs-lookup"><span data-stu-id="11368-236">It no longer applies.</span></span>

<span data-ttu-id="11368-237">Wszystkie poprawki kodu pochodzić od <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="11368-237">All code fixes derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="11368-238">Zastępują one wszystkie <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> do zgłaszania poprawki dostępne kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-238">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="11368-239">W `RegisterCodeFixesAsync`, Zmień typ węzła nadrzędnego szukasz do <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> do dopasowania diagnostyczne:</span><span class="sxs-lookup"><span data-stu-id="11368-239">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="11368-240">Następnie należy zmienić ostatni wiersz, aby zarejestrować poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-240">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="11368-241">Rozwiązanie problemu spowoduje utworzenie nowego dokumentu, który jest wynikiem dodawania `const` modyfikator do istniejącej deklaracji:</span><span class="sxs-lookup"><span data-stu-id="11368-241">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>  

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="11368-242">Można zauważyć czerwone faliste linie w kodzie, który właśnie został dodany na symbol `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="11368-242">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="11368-243">Dodaj deklarację dla `MakeConstAsync` jak poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="11368-243">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="11368-244">Nowy `MakeConstAsync` przekształci metoda <xref:Microsoft.CodeAnalysis.Document> reprezentujący użytkownika pliku źródłowego do nowego <xref:Microsoft.CodeAnalysis.Document> że teraz zawiera `const` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="11368-244">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="11368-245">Możesz utworzyć nową `const` — słowo kluczowe token wstawiony na początku instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="11368-245">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="11368-246">Uważaj najpierw usunąć wszystkie wiodące elementy towarzyszące składni z pierwszy token instrukcji deklaracji i dołączyć go do `const` tokenu.</span><span class="sxs-lookup"><span data-stu-id="11368-246">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="11368-247">Dodaj następujący kod do `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="11368-247">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="11368-248">Następnie dodaj `const` tokenu z deklaracją przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="11368-248">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="11368-249">Następnie sformatuj nowe oświadczenie do dopasowania reguły formatowania języka C#.</span><span class="sxs-lookup"><span data-stu-id="11368-249">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="11368-250">Formatowanie zmiany, aby dopasować istniejący kod tworzy lepsze środowisko.</span><span class="sxs-lookup"><span data-stu-id="11368-250">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="11368-251">Dodaj następującą instrukcję, natychmiast po istniejącym kodzie:</span><span class="sxs-lookup"><span data-stu-id="11368-251">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="11368-252">Nowy obszar nazw jest wymagana dla tego kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-252">A new namespace is required for this code.</span></span> <span data-ttu-id="11368-253">Dodaj następujący kod `using` instrukcji na górze pliku:</span><span class="sxs-lookup"><span data-stu-id="11368-253">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="11368-254">Ostatnim krokiem jest zapewnienie edycji.</span><span class="sxs-lookup"><span data-stu-id="11368-254">The final step is to make your edit.</span></span> <span data-ttu-id="11368-255">Istnieją trzy kroki, aby ten proces:</span><span class="sxs-lookup"><span data-stu-id="11368-255">There are three steps to this process:</span></span>

1. <span data-ttu-id="11368-256">Uzyskaj dojście do istniejącego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11368-256">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="11368-257">Utwórz nowy dokument przez zastąpienie istniejącej deklaracji nowe oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="11368-257">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="11368-258">Zwraca nowy dokument.</span><span class="sxs-lookup"><span data-stu-id="11368-258">Return the new document.</span></span>

<span data-ttu-id="11368-259">Dodaj następujący kod na końcu `MakeConstAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="11368-259">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="11368-260">Poprawkę kod jest gotowy do wypróbowania.</span><span class="sxs-lookup"><span data-stu-id="11368-260">Your code fix is ready to try.</span></span>  <span data-ttu-id="11368-261">Naciśnij klawisz F5, aby uruchomić projekt analizator w drugim wystąpieniu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-261">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="11368-262">W drugim wystąpieniu programu Visual Studio Utwórz nowy projekt aplikacji Konsolowej C# i dodaj kilka deklaracji zmiennych lokalnych zainicjować przy użyciu stałych wartości do metody Main.</span><span class="sxs-lookup"><span data-stu-id="11368-262">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="11368-263">Zobaczysz, że są one raportowane jako ostrzeżenia, tak jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="11368-263">You'll see that they are reported as warnings as below.</span></span>

![Można wprowadzić const ostrzeżenia](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="11368-265">Wprowadzono wiele postępu.</span><span class="sxs-lookup"><span data-stu-id="11368-265">You've made a lot of progress.</span></span> <span data-ttu-id="11368-266">Istnieją faliste linie w deklaracjach, które mogą być wykonane `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-266">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="11368-267">Jednak nadal zadania do wykonania.</span><span class="sxs-lookup"><span data-stu-id="11368-267">But there is still work to do.</span></span> <span data-ttu-id="11368-268">To działa prawidłowo, jeśli dodasz `const` do deklaracji, począwszy od `i`, następnie `j` a na koniec `k`.</span><span class="sxs-lookup"><span data-stu-id="11368-268">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="11368-269">Jednak jeśli dodasz `const` modyfikator i inną kolejność, począwszy od `k`, Twoje analizatora tworzy błędy: `k` nie można zadeklarować `const`, chyba że `i` i `j` są już `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-269">But, if you add the `const` modifier i a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="11368-270">Masz w celu dalszej analizy w celu zapewnienia obsługi różnych sposobów zmienne mogą być deklarowane i inicjowane.</span><span class="sxs-lookup"><span data-stu-id="11368-270">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="11368-271">Tworzenie testów opartych na danych</span><span class="sxs-lookup"><span data-stu-id="11368-271">Build data driven tests</span></span>

<span data-ttu-id="11368-272">Twoje analizator i kod napraw pracy w prostym przypadku jednej deklaracji, które mogą być wykonane const.</span><span class="sxs-lookup"><span data-stu-id="11368-272">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="11368-273">Istnieje wiele instrukcje deklaracji możliwe, w którym tej implementacji sprawia, że błędy.</span><span class="sxs-lookup"><span data-stu-id="11368-273">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="11368-274">Te przypadki zaspokoić poprzez współdziałanie z Biblioteka testów jednostkowych, które są zapisywane przez szablon.</span><span class="sxs-lookup"><span data-stu-id="11368-274">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="11368-275">Jest znacznie szybszy niż wielokrotnie otwieranie drugą kopię programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11368-275">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="11368-276">Otwórz **MakeConstUnitTests.cs** pliku w projekcie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="11368-276">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="11368-277">Szablon utworzony dwóch testów, które należy wykonać dwie typowe wzorce dla analizatora oraz test jednostkowy poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-277">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="11368-278">`TestMethod1` Pokazuje, że wzorzec dla testów, które gwarantuje, że analizator nie zgłaszaj diagnostyki, gdy nie należy go.</span><span class="sxs-lookup"><span data-stu-id="11368-278">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="11368-279">`TestMethod2` przedstawia wzorzec do raportowania diagnostyki i uruchamiania poprawki kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-279">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="11368-280">Kod dla niemal każdego testu, Twoje analizatora następuje jeden z tych dwóch wzorców.</span><span class="sxs-lookup"><span data-stu-id="11368-280">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="11368-281">W pierwszym kroku możesz przerabiać te testy jako testów opartych na danych.</span><span class="sxs-lookup"><span data-stu-id="11368-281">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="11368-282">Następnie będzie można łatwo utworzyć nowe testy, dodając nowe stałych ciągów do reprezentowania danych wejściowych z różnych testów.</span><span class="sxs-lookup"><span data-stu-id="11368-282">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="11368-283">W celu zwiększenia wydajności pierwszym krokiem jest Refaktoryzacja dwóch testów do testów opartych na danych.</span><span class="sxs-lookup"><span data-stu-id="11368-283">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="11368-284">Następnie wystarczy zdefiniować kilka stałych ciągów dla każdego nowego testu.</span><span class="sxs-lookup"><span data-stu-id="11368-284">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="11368-285">Podczas refaktoryzacji, Zmień nazwę obu metod lepszych nazw.</span><span class="sxs-lookup"><span data-stu-id="11368-285">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="11368-286">Zastąp `TestMethod1` jest wywoływane z tym testem, które gwarantuje, że nie diagnostyczne:</span><span class="sxs-lookup"><span data-stu-id="11368-286">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="11368-287">Można utworzyć nowego wiersza danych dla tego testu, definiując dowolnego fragmentu kodu, które nie powinny powodować usługi diagnostyczne do wyzwalania ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="11368-287">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="11368-288">To przeciążenie `VerifyCSharpDiagnostic` zostają spełnione, gdy nie ma żadnych diagnostyki wyzwolone dla fragmentu kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="11368-288">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>  

<span data-ttu-id="11368-289">Następnie zastąp `TestMethod2` za pomocą tego testu, które gwarantuje, że Diagnostyka jest wywoływane i poprawki kodu, stosowane dla tego fragmentu kodu źródłowego:</span><span class="sxs-lookup"><span data-stu-id="11368-289">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="11368-290">Powyższy kod również kilka zmian do kodu, który kompiluje oczekiwane wyniki diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="11368-290">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="11368-291">Używa ona publiczne stałe zarejestrowane w `MakeConst` analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-291">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="11368-292">Ponadto używa dwóch stałych ciągów dla źródła danych wejściowych i stały.</span><span class="sxs-lookup"><span data-stu-id="11368-292">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="11368-293">Dodaj następujące stałe ciągu do `UnitTest` klasy:</span><span class="sxs-lookup"><span data-stu-id="11368-293">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="11368-294">Te dwa testy, aby upewnić się, że przechodzą uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="11368-294">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="11368-295">W programie Visual Studio, otwórz **Eksplorator testów** , wybierając **testu** > **Windows** > **Eksplorator testów**.</span><span class="sxs-lookup"><span data-stu-id="11368-295">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="11368-296">Następnie naciśnij klawisz **Uruchom wszystkie** łącza.</span><span class="sxs-lookup"><span data-stu-id="11368-296">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="11368-297">Tworzenie testów dla deklaracji na prawidłową</span><span class="sxs-lookup"><span data-stu-id="11368-297">Create tests for valid declarations</span></span>

<span data-ttu-id="11368-298">Zgodnie z ogólną zasadą analizatory powinno powodować wyjście tak szybko, jak to możliwe, minimalnym nakładzie pracy.</span><span class="sxs-lookup"><span data-stu-id="11368-298">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="11368-299">Visual Studio wywołania zarejestrowany analizatory jako kod zmiany użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11368-299">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="11368-300">Czas odpowiedzi jest decydujące znaczenie.</span><span class="sxs-lookup"><span data-stu-id="11368-300">Responsiveness is a key requirement.</span></span> <span data-ttu-id="11368-301">Istnieje kilka przypadków testowych dla kodu, który nie powinna podnieść swoje diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="11368-301">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="11368-302">Analizator swoje już obsługuje jeden z tych testów, w przypadku, gdy zmienna jest przypisywana zostały już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="11368-302">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="11368-303">Dodaj następującą stałą ciągu do testów do reprezentowania tego przypadku:</span><span class="sxs-lookup"><span data-stu-id="11368-303">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="11368-304">Następnie dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="11368-304">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="11368-305">Ten test zakończy się pomyślnie także.</span><span class="sxs-lookup"><span data-stu-id="11368-305">This test passes as well.</span></span> <span data-ttu-id="11368-306">Następnie dodaj stałe do warunków, które nie są jeszcze obsługiwane:</span><span class="sxs-lookup"><span data-stu-id="11368-306">Next, add constants for conditions you haven't handled yet:</span></span>

* <span data-ttu-id="11368-307">Deklaracje, które zostały już `const`, ponieważ są one już const:</span><span class="sxs-lookup"><span data-stu-id="11368-307">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* <span data-ttu-id="11368-308">Deklaracje, które mają żadnego inicjatora, ponieważ nie ma wartości do użycia:</span><span class="sxs-lookup"><span data-stu-id="11368-308">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* <span data-ttu-id="11368-309">Deklaracje, gdy inicjator nie jest stałą, ponieważ nie mogą być stałe w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="11368-309">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="11368-310">Można go jeszcze bardziej skomplikowane, ponieważ C# umożliwia wielu deklaracjach jako jedną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="11368-310">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="11368-311">Należy wziąć pod uwagę następujące stała typu string przypadek testowy:</span><span class="sxs-lookup"><span data-stu-id="11368-311">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="11368-312">Zmienna `i` zyski, stała, natomiast zmienna `j` nie.</span><span class="sxs-lookup"><span data-stu-id="11368-312">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="11368-313">W związku z tym ta instrukcja nie można dokonać const deklaracji.</span><span class="sxs-lookup"><span data-stu-id="11368-313">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="11368-314">Dodaj `DataRow` deklaracje dla tych testów:</span><span class="sxs-lookup"><span data-stu-id="11368-314">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="11368-315">Uruchom testy ponownie, a zobaczysz te nowe przypadki testowe, który się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="11368-315">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="11368-316">Zaktualizuj swoje analizatora do ignorowania poprawiania deklaracji</span><span class="sxs-lookup"><span data-stu-id="11368-316">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="11368-317">Musisz wprowadzić ulepszenia usługi analizatora `AnalyzeNode` metodę, aby odfiltrować kod, który pasuje do tych warunków.</span><span class="sxs-lookup"><span data-stu-id="11368-317">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="11368-318">Są one wszystkie powiązane warunki, więc podobne zmiany naprawi wszystkie te warunki.</span><span class="sxs-lookup"><span data-stu-id="11368-318">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="11368-319">Wprowadź następujące zmiany do `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="11368-319">Make the following changes to `AnalyzeNode`:</span></span>

* <span data-ttu-id="11368-320">Usługi analizy semantycznej zbadane Pojedyncza deklaracja zmiennej.</span><span class="sxs-lookup"><span data-stu-id="11368-320">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="11368-321">Ten kod musi być zapisana w `foreach` pętli, która sprawdza, czy wszystkie zmienne zadeklarowane w tej samej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="11368-321">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
* <span data-ttu-id="11368-322">Każdy zadeklarowana zmienna musi mieć inicjatora.</span><span class="sxs-lookup"><span data-stu-id="11368-322">Each declared variable needs to have an initializer.</span></span>
* <span data-ttu-id="11368-323">Inicjator każdej zadeklarowanej zmiennej musi być stałą czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="11368-323">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="11368-324">W swojej `AnalyzeNode` metody zastąpić oryginalnej analizy semantycznej:</span><span class="sxs-lookup"><span data-stu-id="11368-324">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="11368-325">następującym fragmentem kodu:</span><span class="sxs-lookup"><span data-stu-id="11368-325">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="11368-326">Pierwszy `foreach` pętli sprawdza, czy każdy deklaracja zmiennej za pomocą analizy składni.</span><span class="sxs-lookup"><span data-stu-id="11368-326">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="11368-327">Sprawdź najpierw gwarantuje, że zmienna ma inicjatora.</span><span class="sxs-lookup"><span data-stu-id="11368-327">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="11368-328">Drugi wyboru gwarantuje, że inicjator jest stałą.</span><span class="sxs-lookup"><span data-stu-id="11368-328">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="11368-329">Drugi pętli ma oryginalnej analizy semantycznej.</span><span class="sxs-lookup"><span data-stu-id="11368-329">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="11368-330">Semantyczne kontroli znajdują się w oddzielnych pętli, ponieważ ma on większy wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="11368-330">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="11368-331">Ponownie uruchom testy i powinny one przekazywania.</span><span class="sxs-lookup"><span data-stu-id="11368-331">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="11368-332">Dodaj końcowego Polski</span><span class="sxs-lookup"><span data-stu-id="11368-332">Add the final polish</span></span>

<span data-ttu-id="11368-333">Prawie gotowe.</span><span class="sxs-lookup"><span data-stu-id="11368-333">You're almost done.</span></span> <span data-ttu-id="11368-334">Istnieje kilka więcej warunków dla Twojego analizatora do obsługi.</span><span class="sxs-lookup"><span data-stu-id="11368-334">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="11368-335">Program Visual Studio wywołuje analizatory podczas pisania kodu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11368-335">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="11368-336">Często jest przypadek, który będzie analizatora użytkownika o nazwie do kodu, który nie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="11368-336">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="11368-337">Analizatora diagnostycznego `AnalyzeNode` metoda nie sprawdza, czy wartość stała jest konwertowany na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="11368-337">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="11368-338">Tak, bieżąca implementacja parametru trafem korzysta przekonwertuje nieprawidłową deklarację, takie jak int i = "abc" ' ze stałą lokalnego.</span><span class="sxs-lookup"><span data-stu-id="11368-338">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="11368-339">Dodaj stałą typu string źródła dla tego warunku:</span><span class="sxs-lookup"><span data-stu-id="11368-339">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="11368-340">Ponadto typy odwołań nie są obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="11368-340">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="11368-341">Tylko stała wartość dozwolona jest typem referencyjnym `null`, z wyjątkiem w tym przypadku <xref:System.String?displayPropert=nameWIthType>, co umożliwia literały ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="11368-341">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayPropert=nameWIthType>, which allows string literals.</span></span> <span data-ttu-id="11368-342">Innymi słowy `const string s = "abc"` jest dozwolony, ale `const object s = "abc"` nie jest.</span><span class="sxs-lookup"><span data-stu-id="11368-342">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="11368-343">Ten fragment kodu sprawdza tego warunku:</span><span class="sxs-lookup"><span data-stu-id="11368-343">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="11368-344">Aby zapewnić dokładne, należy dodać kolejny test, aby upewnić się, który można utworzyć w deklaracji stałej ciągu.</span><span class="sxs-lookup"><span data-stu-id="11368-344">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="11368-345">Poniższy fragment kodu definiuje kod, który wywołuje diagnostyczne i kod, po zastosowaniu poprawki:</span><span class="sxs-lookup"><span data-stu-id="11368-345">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="11368-346">Ponadto jeśli zmienna jest zadeklarowana za pomocą `var` — słowo kluczowe, nie nic złego poprawki kodu i generuje `const var` deklaracji, który nie jest obsługiwany przez język C#.</span><span class="sxs-lookup"><span data-stu-id="11368-346">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="11368-347">Aby rozwiązać ten problem, należy zastąpić poprawki kodu `var` — słowo kluczowe o nazwie wnioskowany typ:</span><span class="sxs-lookup"><span data-stu-id="11368-347">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="11368-348">Te zmiany, zaktualizuj deklaracji wiersza danych w obu.</span><span class="sxs-lookup"><span data-stu-id="11368-348">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="11368-349">Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersz danych:</span><span class="sxs-lookup"><span data-stu-id="11368-349">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="11368-350">Na szczęście wszystkie powyższe błędy można reagować, wykonując te same techniki, które właśnie zaprezentowano.</span><span class="sxs-lookup"><span data-stu-id="11368-350">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="11368-351">Aby naprawić błąd pierwszy, należy najpierw otworzyć **DiagnosticAnalyzer.cs** i Znajdź pętli foreach, gdzie każda inicjatory deklaracji lokalnej sprawdzany w celu zapewnienia, są przypisani za pomocą wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="11368-351">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="11368-352">Od razu _przed_ pierwszy pętli foreach, wywołanie `context.SemanicModel.GetTypeInfo()` można pobrać szczegółowe informacje na temat zadeklarowanym typem deklaracji lokalnej:</span><span class="sxs-lookup"><span data-stu-id="11368-352">Immediately _before_ the first foreach loop, call `context.SemanicModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="11368-353">Następnie wewnątrz swojej `foreach` pętli, należy sprawdzić każdego inicjatora, aby upewnić się, jest konwertowany na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="11368-353">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="11368-354">Dodaj następujące wyboru po upewnieniu się, że inicjator jest stałą:</span><span class="sxs-lookup"><span data-stu-id="11368-354">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="11368-355">Następna zmiana opiera się na ostatni z nich.</span><span class="sxs-lookup"><span data-stu-id="11368-355">The next change builds upon the last one.</span></span> <span data-ttu-id="11368-356">Przed zamykający nawias klamrowy pierwszej instrukcji foreach pętli, należy dodać następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciąg lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="11368-356">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="11368-357">Należy napisać kod bardziej w dostawcą poprawki kodu, aby zastąpić var' — słowo kluczowe o nazwie poprawnego typu.</span><span class="sxs-lookup"><span data-stu-id="11368-357">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="11368-358">Wróć do **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="11368-358">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="11368-359">Kod, który dodasz wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="11368-359">The code you'll add does the following steps:</span></span>

* <span data-ttu-id="11368-360">Sprawdź, czy deklaracja jest `var` deklaracji, jeśli jest:</span><span class="sxs-lookup"><span data-stu-id="11368-360">Check if the declaration is a `var` declaration, and if it is:</span></span>
* <span data-ttu-id="11368-361">Tworzenie nowego typu dla typu wywnioskowanego.</span><span class="sxs-lookup"><span data-stu-id="11368-361">Create a new type for the inferred type.</span></span>
* <span data-ttu-id="11368-362">Upewnij się, że Deklaracja typu nie jest aliasem.</span><span class="sxs-lookup"><span data-stu-id="11368-362">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="11368-363">Jeśli tak, jest legalne, aby zadeklarować `const var`.</span><span class="sxs-lookup"><span data-stu-id="11368-363">If so, it is legal to declare `const var`.</span></span>
* <span data-ttu-id="11368-364">Upewnij się, że `var` nie jest nazwą typu, w tym programie.</span><span class="sxs-lookup"><span data-stu-id="11368-364">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="11368-365">(Jeśli tak, `const var` jest legalna).</span><span class="sxs-lookup"><span data-stu-id="11368-365">(If so, `const var` is legal).</span></span>
* <span data-ttu-id="11368-366">Uprość Pełna nazwa typu</span><span class="sxs-lookup"><span data-stu-id="11368-366">Simplify the full type name</span></span>

<span data-ttu-id="11368-367">Czy wygląda na to duże ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-367">That sounds like a lot of code.</span></span> <span data-ttu-id="11368-368">Nie jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="11368-368">It's not.</span></span> <span data-ttu-id="11368-369">Zastąp wiersz, który deklaruje i inicjuje `newLocal` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="11368-369">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="11368-370">Przechodzi ona od razu po zainicjowaniu `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="11368-370">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="11368-371">Musisz dodać jeden `using` instrukcję, aby użyć <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> typu:</span><span class="sxs-lookup"><span data-stu-id="11368-371">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="11368-372">Uruchom testy i one wszystkich przejść.</span><span class="sxs-lookup"><span data-stu-id="11368-372">Run your tests, and they should all pass.</span></span> <span data-ttu-id="11368-373">Pogratulować samodzielnie, uruchamiając usługi Zakończono analizatora.</span><span class="sxs-lookup"><span data-stu-id="11368-373">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="11368-374">Naciśnij klawisze Ctrl + F5, aby uruchomić projekt analizator w drugim wystąpieniu programu Visual Studio z rozszerzeniem Roslyn w wersji zapoznawczej załadowane.</span><span class="sxs-lookup"><span data-stu-id="11368-374">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

* <span data-ttu-id="11368-375">Drugie wystąpienie programu Visual Studio Utwórz nowy projekt aplikacji Konsolowej C# i dodawać `int x = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="11368-375">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="11368-376">Dzięki rozłożeniu w pierwszym poprawki bez ostrzeżenia powinny być raportowane dla tej deklaracji zmiennej lokalnej (chociaż zgodnie z oczekiwaniami, występuje błąd kompilatora).</span><span class="sxs-lookup"><span data-stu-id="11368-376">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
* <span data-ttu-id="11368-377">Następnie dodaj `object s = "abc";` do metody Main.</span><span class="sxs-lookup"><span data-stu-id="11368-377">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="11368-378">Ze względu na drugim naprawienie usterki bez ostrzeżenia powinny być raportowane.</span><span class="sxs-lookup"><span data-stu-id="11368-378">Because of the second bug fix, no warning should be reported.</span></span>
* <span data-ttu-id="11368-379">Na koniec należy dodać inny zmiennej lokalnej, która używa `var` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="11368-379">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="11368-380">Zobaczysz, że ostrzeżenie jest zgłaszane i jest wyświetlany pod po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="11368-380">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
* <span data-ttu-id="11368-381">Przesuń karetkę edytora za pośrednictwem falistą, a następnie naciśnij klawisze Ctrl +.</span><span class="sxs-lookup"><span data-stu-id="11368-381">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="11368-382">Aby wyświetlić poprawki sugerowane kodu.</span><span class="sxs-lookup"><span data-stu-id="11368-382">to display the suggested code fix.</span></span> <span data-ttu-id="11368-383">Po wybraniu poprawkę kodu, należy pamiętać, że var' — słowo kluczowe jest teraz obsługiwana prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="11368-383">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="11368-384">Na koniec Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="11368-384">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="11368-385">Po wprowadzeniu tych zmian możesz uzyskać czerwone symbole tylko na pierwszych dwóch zmiennych.</span><span class="sxs-lookup"><span data-stu-id="11368-385">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="11368-386">Dodaj `const` zarówno `i` i `j`, i uzyskuj nowe ostrzeżenie na `k` ponieważ mogą być teraz `const`.</span><span class="sxs-lookup"><span data-stu-id="11368-386">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="11368-387">Gratulacje!</span><span class="sxs-lookup"><span data-stu-id="11368-387">Congratulations!</span></span> <span data-ttu-id="11368-388">Utworzono pierwszego rozszerzenia platformy kompilatora .NET wykonuje analizę kodu na bieżąco, aby wykryć problem i zapewnia szybkiej poprawki, aby go rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="11368-388">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="11368-389">Po drodze kiedy znasz już wiele interfejsów API, które są częścią zestawu SDK platformy kompilatora .NET (interfejsy API Roslyn) kod.</span><span class="sxs-lookup"><span data-stu-id="11368-389">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="11368-390">Możesz sprawdzić swoją pracę, względem [ukończone przykładowe](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w repozytorium przykładów GitHub.</span><span class="sxs-lookup"><span data-stu-id="11368-390">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span> <span data-ttu-id="11368-391">Możesz też pobrać [pliku zip projektu ukończona](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span><span class="sxs-lookup"><span data-stu-id="11368-391">Or you can download [zip file of the completed project](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span></span>

## <a name="other-resources"></a><span data-ttu-id="11368-392">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="11368-392">Other resources</span></span>

- [<span data-ttu-id="11368-393">Rozpoczynanie pracy z usługą analiza składni</span><span class="sxs-lookup"><span data-stu-id="11368-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="11368-394">Rozpoczynanie pracy z usługą analiza semantyki</span><span class="sxs-lookup"><span data-stu-id="11368-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)