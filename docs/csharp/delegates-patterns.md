---
title: "Wspólne wzorce dla delegatów"
description: "Więcej informacji na temat wspólne wzorce dla używanie delegatów w kodzie, aby uniknąć silne sprzężenia między elementami."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="common-patterns-for-delegates"></a><span data-ttu-id="fb659-104">Wspólne wzorce dla delegatów</span><span class="sxs-lookup"><span data-stu-id="fb659-104">Common Patterns for Delegates</span></span>

[<span data-ttu-id="fb659-105">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="fb659-105">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="fb659-106">Obiekty delegowane udostępniają mechanizm umożliwiający projektów oprogramowania obejmujące minimalny sprzężenia między składnikami.</span><span class="sxs-lookup"><span data-stu-id="fb659-106">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="fb659-107">Przykładem doskonała dla tego projektu jest LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb659-107">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="fb659-108">Wzorzec wyrażenia zapytań LINQ zależy od delegatów dla wszystkich funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb659-108">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="fb659-109">Należy wziąć pod uwagę to prosty przykład:</span><span class="sxs-lookup"><span data-stu-id="fb659-109">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="fb659-110">To filtruje sekwencji liczb tylko te mniejsza niż wartość 10.</span><span class="sxs-lookup"><span data-stu-id="fb659-110">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="fb659-111">`Where` Metoda używa delegata, który określa, które elementy sekwencji przekazać filtr.</span><span class="sxs-lookup"><span data-stu-id="fb659-111">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="fb659-112">Podczas tworzenia zapytania LINQ podanych w tym celu określonych implementacji obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="fb659-112">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="fb659-113">Prototyp w którym metoda jest:</span><span class="sxs-lookup"><span data-stu-id="fb659-113">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="fb659-114">W tym przykładzie jest powtarzany z metod, które są częścią LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb659-114">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="fb659-115">Wszystkie opierają się na delegatów dla kodu zarządzanego określonej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="fb659-115">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="fb659-116">Ten wzorzec projektowy interfejsu API jest bardzo przydatna do nauczenia i zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="fb659-116">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="fb659-117">Ten prosty przykład ilustruje sposób delegatów wymaga bardzo małego sprzężenia między składnikami.</span><span class="sxs-lookup"><span data-stu-id="fb659-117">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="fb659-118">Nie trzeba utworzyć klasę pochodną konkretnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="fb659-118">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="fb659-119">Nie należy do implementacji określonego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fb659-119">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="fb659-120">Jedynym wymaganiem jest zapewnienie stosowania jedną metodę, która jest niezbędne, aby wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="fb659-120">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="fb659-121">Tworzenie własnych składników z delegatów</span><span class="sxs-lookup"><span data-stu-id="fb659-121">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="fb659-122">Utworzymy w tym na przykład przez tworzenie składnika przy użyciu projektu, który korzysta z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="fb659-122">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="fb659-123">Umożliwia zdefiniowanie składnik, który może posłużyć komunikatów dziennika w systemie duży.</span><span class="sxs-lookup"><span data-stu-id="fb659-123">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="fb659-124">Składniki biblioteki można używać w wielu różnych środowiskach, na wielu różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="fb659-124">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="fb659-125">Istnieje wiele typowych funkcji w składniku, która zarządza dzienniki.</span><span class="sxs-lookup"><span data-stu-id="fb659-125">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="fb659-126">Trzeba będzie akceptować komunikaty z dowolnego składnika w systemie.</span><span class="sxs-lookup"><span data-stu-id="fb659-126">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="fb659-127">Te komunikaty będą mieć różnych priorytetów, które mogą zarządzać podstawowy składnik.</span><span class="sxs-lookup"><span data-stu-id="fb659-127">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="fb659-128">Komunikaty powinien mieć sygnatur czasowych końcowego postać archiwizowane.</span><span class="sxs-lookup"><span data-stu-id="fb659-128">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="fb659-129">Aby uzyskać bardziej zaawansowanych scenariuszy można filtrować wiadomości przez składnik źródłowy.</span><span class="sxs-lookup"><span data-stu-id="fb659-129">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="fb659-130">Istnieje jeden aspekt funkcję, która zmieni się często: gdzie komunikaty są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="fb659-130">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="fb659-131">W niektórych środowiskach może zostać wyświetlony w konsoli błędu.</span><span class="sxs-lookup"><span data-stu-id="fb659-131">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="fb659-132">W innych osób, w pliku.</span><span class="sxs-lookup"><span data-stu-id="fb659-132">In others, a file.</span></span> <span data-ttu-id="fb659-133">Inne możliwości obejmują magazyn baz danych, dzienników zdarzeń systemu operacyjnego lub innych magazynów dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fb659-133">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="fb659-134">Dostępne są także kombinacji danych wyjściowych, które mogą być używane w różnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="fb659-134">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="fb659-135">Możesz zapisać wiadomości do konsoli i w pliku.</span><span class="sxs-lookup"><span data-stu-id="fb659-135">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="fb659-136">Projekt na podstawie delegatów zapewniają dużą elastyczność i ułatwiają mechanizmów magazynu pomocy technicznej, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="fb659-136">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="fb659-137">W tym projekcie składnika dziennika podstawowego można Niewirtualny, nawet zapieczętowane klasy.</span><span class="sxs-lookup"><span data-stu-id="fb659-137">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="fb659-138">Można podłączyć do każdego zestawu obiektów delegowanych do zapisywania wiadomości do innego magazynu nośnika.</span><span class="sxs-lookup"><span data-stu-id="fb659-138">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="fb659-139">Obsługa wbudowanej obiekty delegowane multiemisji ułatwia scenariusze pomocy technicznej, w którym wiadomości musi być napisana w wielu lokalizacjach (pliku i konsoli).</span><span class="sxs-lookup"><span data-stu-id="fb659-139">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="fb659-140">Pierwszy implementacji</span><span class="sxs-lookup"><span data-stu-id="fb659-140">A First Implementation</span></span>

<span data-ttu-id="fb659-141">Zacznijmy małych: implementacja początkowej będzie akceptować nowych komunikatów i zapisze je przy użyciu dowolnego dołączonego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="fb659-141">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="fb659-142">Można uruchomić z jednego delegata, który zapisuje komunikaty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="fb659-142">You can start with one delegate that writes messages to the console.</span></span>

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

<span data-ttu-id="fb659-143">Klasa statyczna powyżej jest najprostsza rzecz, którą można pracować.</span><span class="sxs-lookup"><span data-stu-id="fb659-143">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="fb659-144">Należy zapisać pojedynczej implementacji metody, która zapisuje komunikaty do konsoli:</span><span class="sxs-lookup"><span data-stu-id="fb659-144">We need to write the single implementation for the method that writes messages to the console:</span></span> 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

<span data-ttu-id="fb659-145">Na koniec należy Podłączanie delegata przy dołączeniu go do WriteMessage, delegowanie zadeklarowany w rejestratora:</span><span class="sxs-lookup"><span data-stu-id="fb659-145">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="fb659-146">Rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb659-146">Practices</span></span>

<span data-ttu-id="fb659-147">Do tej pory naszej próbki jest dość proste, ale pokazuje nadal niektóre ważne wskazówki dla projektów obejmujących delegatów.</span><span class="sxs-lookup"><span data-stu-id="fb659-147">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="fb659-148">Przy użyciu zdefiniowanych w ramach podstawowych typów delegata ułatwia użytkownikom pracę z delegatów.</span><span class="sxs-lookup"><span data-stu-id="fb659-148">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="fb659-149">Nie trzeba definiować nowych typów i deweloperów korzystających z biblioteki nie trzeba informacje typach nowe, wyspecjalizowany delegata.</span><span class="sxs-lookup"><span data-stu-id="fb659-149">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="fb659-150">Interfejsy używane są jako minimalna i jak najbardziej elastyczne: Aby utworzyć nowe rejestrowania danych wyjściowych, należy utworzyć jedną metodę.</span><span class="sxs-lookup"><span data-stu-id="fb659-150">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="fb659-151">Ta metoda może być metodą statyczną lub metodą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fb659-151">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="fb659-152">Może mieć dostęp.</span><span class="sxs-lookup"><span data-stu-id="fb659-152">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="fb659-153">Formatowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="fb659-153">Formatting Output</span></span>

<span data-ttu-id="fb659-154">Bit bardziej niezawodne i ponownie uruchomić tworzenie innych mechanizmów rejestrowania można wprowadzić tej pierwszej wersji.</span><span class="sxs-lookup"><span data-stu-id="fb659-154">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="fb659-155">Następnie Dodajmy mało argumentów dla `LogMessage()` metody, aby klasy dziennika tworzy więcej strukturalnych wiadomości:</span><span class="sxs-lookup"><span data-stu-id="fb659-155">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

<span data-ttu-id="fb659-156">Następnie można wprowadzić Użyj tego `Severity` wyjściowy argument do filtrowania wiadomości, które są wysyłane do dziennika.</span><span class="sxs-lookup"><span data-stu-id="fb659-156">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a><span data-ttu-id="fb659-157">Rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb659-157">Practices</span></span>

<span data-ttu-id="fb659-158">Nowe funkcje dodane do infrastruktury rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="fb659-158">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="fb659-159">Ponieważ składnik rejestratora jest bardzo luźno powiązane z mechanizmem żadnych danych wyjściowych, można dodać te nowe funkcje bez wpływu na żadnego kodu Implementowanie delegata rejestratora.</span><span class="sxs-lookup"><span data-stu-id="fb659-159">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="fb659-160">Jak zachować kompilowanie to, zobaczysz więcej przykładów jak tym luźne powiązanie zapewnia większą elastyczność podczas aktualizowania części witryny bez wprowadzania żadnych zmian do innych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fb659-160">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="fb659-161">W rzeczywistości w większej aplikacji klasy wyjściowe rejestratora może znajdować się w innym zestawie, a nawet należy ponownie utworzyć.</span><span class="sxs-lookup"><span data-stu-id="fb659-161">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="fb659-162">Tworzenie drugiego aparat danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="fb659-162">Building a Second Output Engine</span></span>

<span data-ttu-id="fb659-163">Składnik dziennika pochodzi wzdłuż źródło.</span><span class="sxs-lookup"><span data-stu-id="fb659-163">The Log component is coming along well.</span></span> <span data-ttu-id="fb659-164">Dodajmy jeden więcej aparat wyjściowy, który rejestruje komunikaty do pliku.</span><span class="sxs-lookup"><span data-stu-id="fb659-164">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="fb659-165">Są to wymaga nieco więcej wysiłku aparat danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb659-165">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="fb659-166">Będzie ona klasę, która hermetyzuje operacji na plikach i zapewnia, że plik jest zawsze zamknięte po wykonaniu każdego zapisu.</span><span class="sxs-lookup"><span data-stu-id="fb659-166">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="fb659-167">Który zapewnia, że wszystkie dane jest opróżniany na dysku po wygenerowaniu każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fb659-167">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="fb659-168">Oto tego rejestratora plików na podstawie:</span><span class="sxs-lookup"><span data-stu-id="fb659-168">Here is that file based logger:</span></span>

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

<span data-ttu-id="fb659-169">Po utworzeniu tej klasy można utworzyć i jego LogMessage — metoda dołącza do rejestratora składników:</span><span class="sxs-lookup"><span data-stu-id="fb659-169">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

```csharp
var file = new FileLogger("log.txt");
```

<span data-ttu-id="fb659-170">Te dwa nie wykluczają.</span><span class="sxs-lookup"><span data-stu-id="fb659-170">These two are not mutually exclusive.</span></span> <span data-ttu-id="fb659-171">Można dołączyć obu metod dziennika i generują komunikaty do konsoli i plik:</span><span class="sxs-lookup"><span data-stu-id="fb659-171">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="fb659-172">Później nawet w tej samej aplikacji, można usunąć jeden z obiektów delegowanych bez żadnych innych problemów w systemie:</span><span class="sxs-lookup"><span data-stu-id="fb659-172">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="fb659-173">Rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb659-173">Practices</span></span>

<span data-ttu-id="fb659-174">Teraz dodano dodatkowy program obsługi danych wyjściowych dla podsystem rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="fb659-174">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="fb659-175">Ten zestaw wymaga nieco więcej infrastruktury do obsługi poprawnie systemu plików.</span><span class="sxs-lookup"><span data-stu-id="fb659-175">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="fb659-176">Delegat jest metodą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fb659-176">The delegate is an instance method.</span></span> <span data-ttu-id="fb659-177">Istnieje również Metoda prywatna.</span><span class="sxs-lookup"><span data-stu-id="fb659-177">It's also a private method.</span></span>
<span data-ttu-id="fb659-178">Ponieważ infrastruktura delegata można się połączyć delegatów nie istnieje potrzeba większa ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="fb659-178">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="fb659-179">Po drugie projekt na podstawie delegata umożliwia wielu danych wyjściowych metody bez żadnych dodatkowych kodu.</span><span class="sxs-lookup"><span data-stu-id="fb659-179">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="fb659-180">Nie jest potrzebne do tworzenia żadnych dodatkowych infrastruktury do obsługi wielu metod danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fb659-180">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="fb659-181">Po prostu stają się one inna metoda na liście wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb659-181">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="fb659-182">Należy zwrócić szczególną uwagę na kod w pliku rejestrowania danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="fb659-182">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="fb659-183">Zakodowanej aby upewnić się, że nie generują żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fb659-183">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="fb659-184">Gdy to nie zawsze jest to niezbędne, często jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="fb659-184">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="fb659-185">Jeśli jednej z metod delegata zgłasza wyjątek, nie można wywołać pozostałych obiektów delegowanych, które są w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="fb659-185">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="fb659-186">Jako ostatni Uwaga rejestratora plików muszą zarządzać jego zasobów przez otwieranie i zamykanie plików na wszystkich komunikatach dziennika.</span><span class="sxs-lookup"><span data-stu-id="fb659-186">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="fb659-187">Użytkownik może zachować otwarty plik i zaimplementuj interfejs IDisposable, aby zamknąć plik, gdy zostały zakończone.</span><span class="sxs-lookup"><span data-stu-id="fb659-187">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="fb659-188">Każda metoda ma jego zalety i wady.</span><span class="sxs-lookup"><span data-stu-id="fb659-188">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="fb659-189">Zarówno należy tworzyć bardziej sprzężenia między klasami.</span><span class="sxs-lookup"><span data-stu-id="fb659-189">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="fb659-190">Brak kodu w klasie rejestratora musi zostać zaktualizowany w celu wprowadzenia albo scenariusza.</span><span class="sxs-lookup"><span data-stu-id="fb659-190">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="fb659-191">Obsługa delegatów wartości Null</span><span class="sxs-lookup"><span data-stu-id="fb659-191">Handling Null Delegates</span></span>

<span data-ttu-id="fb659-192">Na koniec Przyjrzyjmy aktualizacji LogMessage — metoda, aby był niezawodny dla tych przypadków, gdy żaden mechanizm danych wyjściowych jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fb659-192">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="fb659-193">Bieżąca implementacja zgłosi `NullReferenceException` podczas `WriteMessage` delegat ma listę wywołań dołączony.</span><span class="sxs-lookup"><span data-stu-id="fb659-193">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="fb659-194">Możesz wybrać projekt, który dyskretnie będzie kontynuowane po nie zostały dołączone żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fb659-194">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="fb659-195">Jest to łatwe przy użyciu operatora warunkowego wartości null, połączeniu z `Delegate.Invoke()` metody:</span><span class="sxs-lookup"><span data-stu-id="fb659-195">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="fb659-196">Operator warunkowy wartości null (`?.`) short-circuits, kiedy Lewy argument operacji (`WriteMessage` w takim przypadku) ma wartość null, co oznacza, nie są podejmowane próby logowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fb659-196">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="fb659-197">Nie możesz znaleźć `Invoke()` metody wymienione w dokumentacji dotyczącej `System.Delegate` lub `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="fb659-197">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="fb659-198">Kompilator generuje bezpieczne typu `Invoke` metody dla każdego delegować deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="fb659-198">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="fb659-199">W tym przykładzie, oznacza to `Invoke` przyjmuje jeden `string` argumentu, i został zwrócony typ void.</span><span class="sxs-lookup"><span data-stu-id="fb659-199">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="fb659-200">Podsumowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fb659-200">Summary of Practices</span></span>

<span data-ttu-id="fb659-201">Przedstawiono początku składnik dziennika, który może zostać rozszerzony o innych użytkowników i innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb659-201">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="fb659-202">Przy użyciu delegatów w projekcie tych różnych składników są bardzo luźno powiązane.</span><span class="sxs-lookup"><span data-stu-id="fb659-202">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="fb659-203">Zapewnia kilka korzyści.</span><span class="sxs-lookup"><span data-stu-id="fb659-203">This provides several advantages.</span></span> <span data-ttu-id="fb659-204">Jest bardzo proste tworzenie nowych mechanizmów danych wyjściowych i dołącz je do systemu.</span><span class="sxs-lookup"><span data-stu-id="fb659-204">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="fb659-205">Mechanizmy te wymagane jest tylko jedna metoda: metodę, która zapisuje komunikat w dzienniku.</span><span class="sxs-lookup"><span data-stu-id="fb659-205">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="fb659-206">Jest to projekt, który jest bardzo elastyczne, gdy zostaną dodane nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="fb659-206">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="fb659-207">Kontrakt wymagane dla dowolnego edytora jest wdrożenie jednej metody.</span><span class="sxs-lookup"><span data-stu-id="fb659-207">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="fb659-208">Ta metoda może być statycznymi lub metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fb659-208">That method could be a static or instance method.</span></span> <span data-ttu-id="fb659-209">Może to być public, private lub innych prawne dostęp.</span><span class="sxs-lookup"><span data-stu-id="fb659-209">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="fb659-210">Klasa rejestratora wprowadzić dowolną liczbę ulepszenia lub zmiany bez wprowadzania zmian, które psuły.</span><span class="sxs-lookup"><span data-stu-id="fb659-210">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="fb659-211">Podobnie jak wszystkie klasy nie można zmodyfikować publiczny interfejs API bez ryzyka fundamentalne zmiany.</span><span class="sxs-lookup"><span data-stu-id="fb659-211">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="fb659-212">Jednak ponieważ sprzężenia między rejestratora i wszelkie aparatami danych wyjściowych jest tylko za pośrednictwem pełnomocnika, są związane z żadnych innych typów (na przykład interfejsów lub klas podstawowych).</span><span class="sxs-lookup"><span data-stu-id="fb659-212">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="fb659-213">Sprzężenia jest możliwie jak najmniejszy.</span><span class="sxs-lookup"><span data-stu-id="fb659-213">The coupling is as small as possible.</span></span>

[<span data-ttu-id="fb659-214">Dalej</span><span class="sxs-lookup"><span data-stu-id="fb659-214">Next</span></span>](events-overview.md)