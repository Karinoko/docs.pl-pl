---
title: "Za mało miejsca na stosie (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="2cbc9-102">Za mało miejsca na stosie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cbc9-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="2cbc9-103">Stos jest obszar roboczy pamięci, który powiększa się i zmniejsza dynamicznie z wymaganiami wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="2cbc9-104">Przekroczono limit.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2cbc9-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2cbc9-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="2cbc9-106">Sprawdź, czy procedury nie są zagnieżdżone zbyt głęboko.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="2cbc9-107">Upewnij się, że procedury rekurencyjne kończą się poprawnie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="2cbc9-108">Jeśli zmienne lokalne wymagają lokalnej zmiennej miejsca niż jest dostępne, spróbuj deklarowanie niektóre zmienne na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="2cbc9-109">Można również zadeklarować wszystkie zmienne w procedurze statycznych poprzedzając `Property`, `Sub`, lub `Function` — słowo kluczowe z `Static`.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="2cbc9-110">Możesz też użyć `Static` instrukcji, aby zadeklarować poszczególnych zmiennych statycznych w ramach procedur.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="2cbc9-111">Niektóre z ciągi o stałej długości jako ciągi o zmiennej długości przedefiniować jako ciągi o stałej długości Użyj więcej miejsca na stosie niż ciągi o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="2cbc9-112">Można również zdefiniować ciąg na poziomie modułu, których wymaga miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="2cbc9-113">Sprawdź liczbę zagnieżdżonych `DoEvents` funkcji wywołań, za pomocą `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="2cbc9-114">Upewnij się, że nie spowodowało "cascade zdarzeń" wyzwalając zdarzenie, które wywołuje procedurę zdarzenia już na stosie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="2cbc9-115">Cascade zdarzeń jest podobny do niezakończony procedur rekursja, ale jest mniej oczywista, ponieważ połączenie jest nawiązywane przez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zamiast jawnego wywołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="2cbc9-116">Użyj `Calls` okno dialogowe do widoku, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="2cbc9-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbc9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cbc9-117">See Also</span></span>  
 [<span data-ttu-id="2cbc9-118">Okno pamięci</span><span class="sxs-lookup"><span data-stu-id="2cbc9-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)