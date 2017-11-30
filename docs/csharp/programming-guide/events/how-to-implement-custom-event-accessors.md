---
title: "Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="c00ab-102">Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c00ab-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="c00ab-103">Zdarzenie jest specjalnym rodzajem multiemisji delegata, który można wywołać tylko z należące do klasy, która jest zadeklarowana w.</span><span class="sxs-lookup"><span data-stu-id="c00ab-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="c00ab-104">Kod klienta subskrybuje zdarzenia, podając odniesienie do metody, która powinna być wywoływana, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="c00ab-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="c00ab-105">Te metody są dodawane do listy wywołania delegata za pomocą metod dostępu zdarzeń, która jest podobna do metod dostępu do właściwości, z wyjątkiem tego, że są nazywane metod dostępu zdarzeń `add` i `remove`.</span><span class="sxs-lookup"><span data-stu-id="c00ab-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="c00ab-106">W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c00ab-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="c00ab-107">Gdy nie niestandardowych metod dostępu zdarzeń są dostarczane w kodzie, kompilator doda je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c00ab-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="c00ab-108">W niektórych przypadkach może mieć zapewniające niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c00ab-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="c00ab-109">Jeden taki przypadek przedstawiono w temacie [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span><span class="sxs-lookup"><span data-stu-id="c00ab-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c00ab-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c00ab-110">Example</span></span>  
 <span data-ttu-id="c00ab-111">Poniższy przykład przedstawia sposób implementować niestandardowe zdarzenie dostępu add i remove.</span><span class="sxs-lookup"><span data-stu-id="c00ab-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="c00ab-112">Mimo że można zastąpić wszelkiego kodu wewnątrz metody dostępu, firma Microsoft zaleca, aby zablokować zdarzeń, aby dodać lub usunąć nowa metoda obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c00ab-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="c00ab-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c00ab-113">See Also</span></span>  
 [<span data-ttu-id="c00ab-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c00ab-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="c00ab-115">zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c00ab-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)