---
title: "Współdziałanie z innymi wzorcami asynchronicznymi i typami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e30b562b4795717df526c143df96607686a7582
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="f39bb-102">Współdziałanie z innymi wzorcami asynchronicznymi i typami</span><span class="sxs-lookup"><span data-stu-id="f39bb-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="f39bb-103">.NET Framework 1.0 wprowadzone <xref:System.IAsyncResult> wzorzec, znanej także jako [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), lub `Begin/End` wzorzec.</span><span class="sxs-lookup"><span data-stu-id="f39bb-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="f39bb-104">.NET Framework 2.0, dodać [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="f39bb-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="f39bb-105">Począwszy od programu .NET Framework 4, [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) zastępuje zarówno APM, jak i EAP, ale umożliwia łatwe tworzenie procedury migracji z wcześniejszych wzorce.</span><span class="sxs-lookup"><span data-stu-id="f39bb-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="f39bb-106">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="f39bb-106">In this topic:</span></span>  
  
-   <span data-ttu-id="f39bb-107">[Zadania i APM](#APM) ([z APM wybranie](#ApmToTap) lub [z NACIŚNIJ, aby APM](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="f39bb-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="f39bb-108">Zadania i EAP</span><span class="sxs-lookup"><span data-stu-id="f39bb-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="f39bb-109">[Zadania i uchwyty oczekiwania](#WaitHandles) ([z uchwyty oczekiwania na wybranie](#WHToTap) lub [z NACIŚNIJ, aby uchwyty oczekiwania](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="f39bb-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="f39bb-110">Zadania i Model programowania asynchronicznego (APM)</span><span class="sxs-lookup"><span data-stu-id="f39bb-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="f39bb-111">Z APM wybranie</span><span class="sxs-lookup"><span data-stu-id="f39bb-111">From APM to TAP</span></span>  
 <span data-ttu-id="f39bb-112">Ponieważ [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) wzorzec jest bardzo strukturalnych, jest dość łatwe tworzenie otoki do udostępnienia implementacji APM jako implementację NACIŚNIJ.</span><span class="sxs-lookup"><span data-stu-id="f39bb-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="f39bb-113">W rzeczywistości programu .NET Framework, począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], obejmuje procedury pomocnika w formie <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> przeciążenia metody w celu zapewnienia tłumaczenie.</span><span class="sxs-lookup"><span data-stu-id="f39bb-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="f39bb-114">Należy wziąć pod uwagę <xref:System.IO.Stream> klasy i jej <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A> metody, które reprezentują odpowiednikiem APM synchroniczne <xref:System.IO.Stream.Read%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="f39bb-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="f39bb-115">Można użyć <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> metody do zaimplementowania otoka wybierz dla tej operacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f39bb-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="f39bb-116">Ta implementacja jest podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="f39bb-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="f39bb-117">Z NACIŚNIJ, aby APM</span><span class="sxs-lookup"><span data-stu-id="f39bb-117">From TAP to APM</span></span>  
 <span data-ttu-id="f39bb-118">Jeśli istniejącej infrastruktury oczekuje wzorzec APM, również należy podjąć implementacji NACIŚNIJ i użyć go, których można oczekiwać implementację APM.</span><span class="sxs-lookup"><span data-stu-id="f39bb-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="f39bb-119">Ponieważ zadania mogą być składane i <xref:System.Threading.Tasks.Task> klasa implementuje <xref:System.IAsyncResult>, funkcja prosta pomocnika służy w tym celu.</span><span class="sxs-lookup"><span data-stu-id="f39bb-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="f39bb-120">W poniższym kodzie użyto rozszerzenie <xref:System.Threading.Tasks.Task%601> klasy, ale funkcja niemal identyczny nierodzajową zadań.</span><span class="sxs-lookup"><span data-stu-id="f39bb-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="f39bb-121">Rozważmy przypadek, w którym znajduje się następująca implementacja NACIŚNIJ:</span><span class="sxs-lookup"><span data-stu-id="f39bb-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="f39bb-122">i chcesz zapewnić tej implementacji APM:</span><span class="sxs-lookup"><span data-stu-id="f39bb-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="f39bb-123">W poniższym przykładzie pokazano jedną migrację do APM:</span><span class="sxs-lookup"><span data-stu-id="f39bb-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="f39bb-124">Zadania i oparty na zdarzeniach wzorca asynchronicznego (EAP)</span><span class="sxs-lookup"><span data-stu-id="f39bb-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="f39bb-125">Zawijanie [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementacja jest bardziej skomplikowane niż zawijania wzorzec APM, ponieważ wzorzec EAP ma więcej odmiany i struktura mniej niż wzorzec APM.</span><span class="sxs-lookup"><span data-stu-id="f39bb-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="f39bb-126">Aby zademonstrować, opakowuje następujący kod `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="f39bb-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="f39bb-127">`DownloadStringAsync`akceptuje identyfikator URI, zgłasza `DownloadProgressChanged` zdarzeń podczas pobierania w celu raportowania statystyk wiele w toku i zgłasza `DownloadStringCompleted` zdarzeń po jej zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f39bb-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="f39bb-128">Wynik końcowy jest ciąg znaków zawierający zawartość strony o określonym identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="f39bb-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="f39bb-129">Zadania i uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="f39bb-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="f39bb-130">Z uchwyty oczekiwania na wybranie</span><span class="sxs-lookup"><span data-stu-id="f39bb-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="f39bb-131">Mimo że uchwyty oczekiwania nie implementacji klienta wzorca asynchronicznego, zaawansowane deweloperzy mogą używać <xref:System.Threading.WaitHandle> klasy i <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> metodę asynchroniczną powiadomienia, gdy ustawiono dojścia oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f39bb-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="f39bb-132">Można zawijać <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> metodę umożliwiającą włączenie opartego na zadaniach zamiast żadnych synchroniczne oczekiwanie na dojście oczekiwania:</span><span class="sxs-lookup"><span data-stu-id="f39bb-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="f39bb-133">Przy użyciu tej metody można użyć istniejącego <xref:System.Threading.WaitHandle> implementacje metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f39bb-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="f39bb-134">Na przykład, jeśli chcesz ograniczyć liczbę operacji asynchronicznych, które są wykonywane w dowolnym momencie w szczególności, możesz użyć semafora ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> obiektu).</span><span class="sxs-lookup"><span data-stu-id="f39bb-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="f39bb-135">Można ograniczyć do *N* liczby operacji, które są uruchamiane jednocześnie przez inicjowanie Licznik semafora do *N*, oczekiwanie na semafora dowolnej chwili, aby wykonać operację i zwalnianie Semafor po zakończeniu operacji:</span><span class="sxs-lookup"><span data-stu-id="f39bb-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="f39bb-136">Można również tworzyć asynchroniczne semafora nie bazuje na uchwyty oczekiwania, który działa całkowicie z zadaniami.</span><span class="sxs-lookup"><span data-stu-id="f39bb-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="f39bb-137">Aby to zrobić, można użyć technik, takich jak omawiany w [wykorzystywanie wzorca asynchronicznego opartego na zadaniach](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) do tworzenia struktury danych, nad <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f39bb-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="f39bb-138">Z NACIŚNIJ, aby uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="f39bb-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="f39bb-139">Jak wcześniej wspomniano, <xref:System.Threading.Tasks.Task> klasa implementuje <xref:System.IAsyncResult>, i udostępnia tę implementację <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> właściwości, która zwraca dojście oczekiwania, który będzie można ustawić podczas <xref:System.Threading.Tasks.Task> zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f39bb-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="f39bb-140">Możesz uzyskać <xref:System.Threading.WaitHandle> dla <xref:System.Threading.Tasks.Task> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f39bb-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="f39bb-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f39bb-141">See Also</span></span>  
 [<span data-ttu-id="f39bb-142">Asynchroniczny wzorzec oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="f39bb-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="f39bb-143">Implementacja wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="f39bb-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="f39bb-144">Wykorzystywanie wzorca asynchronicznego opartego na zadaniach</span><span class="sxs-lookup"><span data-stu-id="f39bb-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)