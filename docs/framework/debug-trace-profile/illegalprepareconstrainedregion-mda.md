---
title: illegalPrepareConstrainedRegion MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dad43859e6bec288b66c6c10256a6b2cbc1bbe0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="689ff-102">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="689ff-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="689ff-103">`illegalPrepareConstrainedRegion` Zarządzany Asystent debugowania (MDA) została aktywowana po <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> wywołanie metody nie bezpośrednio poprzedza `try` instrukcji obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="689ff-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="689ff-104">To ograniczenie jest na MSIL poziomu, więc jest dozwolone ma generowanie kodu źródłowego między wywołania i `try`, takich jak komentarze.</span><span class="sxs-lookup"><span data-stu-id="689ff-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="689ff-105">Symptomy</span><span class="sxs-lookup"><span data-stu-id="689ff-105">Symptoms</span></span>  
 <span data-ttu-id="689ff-106">Region ograniczonego wykonania (CER), który nigdy nie jest traktowana tak, ale proste wyjątek obsługi bloku (`finally` lub `catch`).</span><span class="sxs-lookup"><span data-stu-id="689ff-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="689ff-107">Region nie działa w konsekwencji w przypadku przerwania wątku lub warunku braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="689ff-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="689ff-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="689ff-108">Cause</span></span>  
 <span data-ttu-id="689ff-109">Wzór przygotowania CER nie jest prawidłowo zakończony.</span><span class="sxs-lookup"><span data-stu-id="689ff-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="689ff-110">To zdarzenie błędu.</span><span class="sxs-lookup"><span data-stu-id="689ff-110">This is an error event.</span></span> <span data-ttu-id="689ff-111"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Wywołania metody, które służy do oznaczania programy obsługi wyjątków jako wprowadzenie CER w ich `catch` / `finally` / `fault` / `filter` bloki musi być używany bezpośrednio przed `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="689ff-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="689ff-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="689ff-112">Resolution</span></span>  
 <span data-ttu-id="689ff-113">Upewnij się, że wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> się stanie, bezpośrednio przed `try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="689ff-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="689ff-114">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="689ff-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="689ff-115">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="689ff-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="689ff-116">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="689ff-116">Output</span></span>  
 <span data-ttu-id="689ff-117">MDA Wyświetla nazwę wywołanie metody <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metody, przesunięcie MSIL i komunikat informujący o wywołaniu nie poprzedzają bezpośrednio na początku bloku try.</span><span class="sxs-lookup"><span data-stu-id="689ff-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="689ff-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="689ff-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="689ff-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="689ff-119">Example</span></span>  
 <span data-ttu-id="689ff-120">Poniższy przykład kodu pokazuje wzorzec, który powoduje, że to zdarzenie MDA do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="689ff-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="689ff-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="689ff-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [<span data-ttu-id="689ff-122">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="689ff-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="689ff-123">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="689ff-123">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)