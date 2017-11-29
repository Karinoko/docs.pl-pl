---
title: "await (odwołanie w C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 69a3a575347a62b298c17af050cb925f7819b552
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="await-c-reference"></a><span data-ttu-id="3ee58-102">await (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3ee58-102">await (C# Reference)</span></span>
<span data-ttu-id="3ee58-103">`await` Operator jest stosowany do zadania w można wstawić punktu zawieszenia podczas wykonywania metody do momentu ukończenia zadania Oczekiwano metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="3ee58-103">The `await` operator is applied to a task in an asynchronous method to insert a suspension point in the execution of the method until the awaited task completes.</span></span> <span data-ttu-id="3ee58-104">Zadanie reprezentuje pracy w toku.</span><span class="sxs-lookup"><span data-stu-id="3ee58-104">The task represents ongoing work.</span></span>  
  
<span data-ttu-id="3ee58-105">`await`można użyć tylko w metodzie asynchronicznej zmodyfikowany przez [async](../../../csharp/language-reference/keywords/async.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3ee58-105">`await` can only be used in an asynchronous method modified by the [async](../../../csharp/language-reference/keywords/async.md) keyword.</span></span> <span data-ttu-id="3ee58-106">Taka metoda, zdefiniowany przy użyciu `async` modyfikator, zwykle zawiera co najmniej jeden `await` wyrażenia, jest określany jako *metody asynchronicznej*.</span><span class="sxs-lookup"><span data-stu-id="3ee58-106">Such a method, defined by using the `async` modifier and usually containing one or more `await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ee58-107">`async` i `await` wprowadzono słów kluczowych w języku C# 5.</span><span class="sxs-lookup"><span data-stu-id="3ee58-107">The `async` and `await` keywords were introduced in C# 5.</span></span> <span data-ttu-id="3ee58-108">Aby obejrzeć wprowadzenie do programowania asynchronicznego Zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="3ee58-108">For an introduction to async programming, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
<span data-ttu-id="3ee58-109">Zadania, które `await` zastosować operatora zazwyczaj zwracane przez wywołanie do metody, która implementuje [wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="3ee58-109">The task to which the `await` operator is applied typically is returned by a call to a method that implements the [Task-Based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span> <span data-ttu-id="3ee58-110">Obejmują one metody, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, i `System.Threading.Tasks.ValueType<TResult>` obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ee58-110">They include methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, and `System.Threading.Tasks.ValueType<TResult>` objects.</span></span>  

  
 <span data-ttu-id="3ee58-111">W poniższym przykładzie <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda zwraca `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="3ee58-111">In the following example, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> method returns a `Task<byte[]>`.</span></span> <span data-ttu-id="3ee58-112">Zadanie jest obietnicę w celu utworzenia tablicy bajtowej rzeczywiste po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="3ee58-112">The task is a promise to produce the actual byte array when the task is complete.</span></span> <span data-ttu-id="3ee58-113">`await` Operator wstrzymuje wykonywanie do pracy <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody została ukończona.</span><span class="sxs-lookup"><span data-stu-id="3ee58-113">The `await` operator suspends execution until the work of the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> method is complete.</span></span> <span data-ttu-id="3ee58-114">Tymczasem zwróceniem sterowania do wywołującego `GetPageSizeAsync`.</span><span class="sxs-lookup"><span data-stu-id="3ee58-114">In the meantime, control is returned to the caller of `GetPageSizeAsync`.</span></span> <span data-ttu-id="3ee58-115">Gdy zadanie kończy działanie, `await` wyrażenie na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="3ee58-115">When the task finishes execution, the `await` expression evaluates to a byte array.</span></span>  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  <span data-ttu-id="3ee58-116">Aby uzyskać pełny przykład, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="3ee58-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="3ee58-117">Możesz pobrać próbki z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkID=255191) w witrynie firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3ee58-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191) on the Microsoft website.</span></span> <span data-ttu-id="3ee58-118">Przykładem jest w projekcie AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="3ee58-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
<span data-ttu-id="3ee58-119">Jak pokazano w poprzednim przykładzie, jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task<TResult>`, następnie typ `await` wyrażenie jest `TResult`.</span><span class="sxs-lookup"><span data-stu-id="3ee58-119">As shown in the previous example, if `await` is applied to the result of a method call that returns a `Task<TResult>`, then the type of the `await` expression is `TResult`.</span></span> <span data-ttu-id="3ee58-120">Jeśli `await` jest stosowany do wyniku wywołania metody, która zwraca `Task`, następnie typ `await` wyrażenie jest `void`.</span><span class="sxs-lookup"><span data-stu-id="3ee58-120">If `await` is applied to the result of a method call that returns a `Task`, then the type of the `await` expression is `void`.</span></span> <span data-ttu-id="3ee58-121">Poniższy przykład przedstawia różnicy.</span><span class="sxs-lookup"><span data-stu-id="3ee58-121">The following example illustrates the difference.</span></span>  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
<span data-ttu-id="3ee58-122">`await` Wyrażenia nie są blokowane w wątku, na którym jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="3ee58-122">An `await` expression does not block the thread on which it is executing.</span></span> <span data-ttu-id="3ee58-123">Zamiast tego należy go powoduje, że kompilator Zarejestruj pozostałe metody asynchronicznej kontynuacji oczekiwano zadania.</span><span class="sxs-lookup"><span data-stu-id="3ee58-123">Instead, it causes the compiler to sign up the rest of the async method as a continuation on the awaited task.</span></span> <span data-ttu-id="3ee58-124">Formant zwraca do obiektu wywołującego metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="3ee58-124">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="3ee58-125">Po ukończeniu zadania wywołuje kontynuacji i wykonywania wznawia metody asynchronicznej miejsca, w którym.</span><span class="sxs-lookup"><span data-stu-id="3ee58-125">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
<span data-ttu-id="3ee58-126">`await` Wyrażenie może wystąpić tylko w otaczającej jego treści metody, wyrażenia lambda lub metody anonimowej, muszą być oznaczone `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="3ee58-126">An `await` expression can occur only in the body of its enclosing method, lambda expression, or anonymous method, which must be marked with an `async` modifier.</span></span> <span data-ttu-id="3ee58-127">Termin *await* służy jako słowo kluczowe tylko w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="3ee58-127">The term *await* serves as a keyword only in that context.</span></span> <span data-ttu-id="3ee58-128">W innym miejscu jest interpretowany jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="3ee58-128">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="3ee58-129">W ramach metody, wyrażenia lambda lub metody anonimowej `await` wyrażenia nie może wystąpić w treści funkcji synchroniczne w wyrażeniu zapytania w bloku [lock — instrukcja](../../../csharp/language-reference/keywords/lock-statement.md), lub w [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3ee58-129">Within the method, lambda expression, or anonymous method, an `await` expression cannot occur in the body of a synchronous function, in a query expression, in the block of a [lock statement](../../../csharp/language-reference/keywords/lock-statement.md), or in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="3ee58-130">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3ee58-130">Exceptions</span></span>  
<span data-ttu-id="3ee58-131">Zwraca większości metod asynchronicznych <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="3ee58-131">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="3ee58-132">Właściwości zadania zwróconego zawierać informacje o jego stan i Historia, na przykład tego, czy zadanie zostało ukończone, czy metoda asynchroniczna spowodowała wyjątek lub została anulowana i jakie wynik końcowy jest.</span><span class="sxs-lookup"><span data-stu-id="3ee58-132">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="3ee58-133">`await` Operator uzyskuje dostęp do tych właściwości przez wywołanie metody w obiekcie zwracanym przez `GetAwaiter` metody.</span><span class="sxs-lookup"><span data-stu-id="3ee58-133">The `await` operator accesses those properties by calling methods on the object returned by the `GetAwaiter` method.</span></span>  
  
<span data-ttu-id="3ee58-134">Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która powoduje zgłoszenie wyjątku `await` operator ponownie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3ee58-134">If you await a task-returning async method that causes an exception, the `await` operator rethrows the exception.</span></span>  
  
<span data-ttu-id="3ee58-135">Jeśli await umożliwiające zwracanie zadań metoda asynchroniczna, która została anulowana, `await` operator ponownie zgłasza wyjątek <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="3ee58-135">If you await a task-returning async method that's canceled, the `await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
<span data-ttu-id="3ee58-136">Pojedyncze zadanie, który jest stan można odzwierciedlać wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3ee58-136">A single task that is in a faulted state can reflect multiple exceptions.</span></span> <span data-ttu-id="3ee58-137">Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ee58-137">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ee58-138">Gdy await takie zadania, ponownie zgłasza operacji await tylko jeden z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3ee58-138">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="3ee58-139">Jednak nie można przewidzieć który wyjątki jest zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="3ee58-139">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
<span data-ttu-id="3ee58-140">Przykłady obsługi błędów w metodach asynchronicznych, zobacz [try-catch](../../../csharp/language-reference/keywords/try-catch.md).</span><span class="sxs-lookup"><span data-stu-id="3ee58-140">For examples of error handling in async methods, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ee58-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ee58-141">Example</span></span>  
<span data-ttu-id="3ee58-142">Poniższy przykład zwraca całkowita liczba znaków na stronach, których adresy URL są przekazywane do niego jako argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ee58-142">The following example returns the total number of characters in the pages whose URLs are passed to it as command line arguments.</span></span> <span data-ttu-id="3ee58-143">Przykład wywołania `GetPageLengthsAsync` metodę, która jest oznaczony atrybutem `async` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3ee58-143">The example calls the `GetPageLengthsAsync` method, which is marked with the `async` keyword.</span></span> <span data-ttu-id="3ee58-144">`GetPageLengthsAsync` Metoda z kolei używa `await` — słowo kluczowe await wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3ee58-144">The `GetPageLengthsAsync` method in turn uses the `await` keyword to await calls to the <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> method.</span></span>  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

<span data-ttu-id="3ee58-145">Ponieważ stosowania `async` i `await` we wpisie aplikacji punkt nie jest obsługiwane, nie możemy zastosować `async` atrybutu `Main` metody ani może możemy await `GetPageLengthsAsync` wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3ee58-145">Because the use of `async` and `await` in an application entry point is not supported, we cannot apply the `async` attribute to the `Main` method, nor can we await the `GetPageLengthsAsync` method call.</span></span> <span data-ttu-id="3ee58-146">Firma Microsoft może upewnij się, że `Main` metoda oczekuje na zakończenie pobierając zaletą operacji asynchronicznej <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ee58-146">We can ensure that the `Main` method waits for the async operation to complete by retrieving the value of the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3ee58-147">Dla zadań, które nie zwracają wartości, należy wywołać <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3ee58-147">For tasks that do not return a value, you can call the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method.</span></span> 

## <a name="see-also"></a><span data-ttu-id="3ee58-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ee58-148">See also</span></span>  
<span data-ttu-id="3ee58-149">[Programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="3ee58-149">[Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="3ee58-150">[Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="3ee58-150">[Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
[<span data-ttu-id="3ee58-151">asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="3ee58-151">async</span></span>](../../../csharp/language-reference/keywords/async.md)