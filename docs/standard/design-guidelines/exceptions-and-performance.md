---
title: "Wyjątki i wydajności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c2d7cfcb228c492d2adbe614d0ed88a3b02bb68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="157ad-102">Wyjątki i wydajności</span><span class="sxs-lookup"><span data-stu-id="157ad-102">Exceptions and Performance</span></span>
<span data-ttu-id="157ad-103">Jednej wspólnej problemem związanym z wyjątkami jest, że wyjątki są używane do kodu, który regularnie zakończy się niepowodzeniem, wydajność implementacji zostaną nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="157ad-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="157ad-104">Jest to prawidłowy niepożądane.</span><span class="sxs-lookup"><span data-stu-id="157ad-104">This is a valid concern.</span></span> <span data-ttu-id="157ad-105">Gdy członek zgłasza wyjątek, jego wydajność może być rzędów wolniej.</span><span class="sxs-lookup"><span data-stu-id="157ad-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="157ad-106">Jednak jest możliwe uzyskanie dobrą wydajność ściśle przestrzegając wskazówki wyjątków, które nie zezwalaj na korzystanie z kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="157ad-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="157ad-107">Dwa wzorce opisane w tej sekcji sugestie sposobów, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="157ad-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="157ad-108">**X nie** używa kody błędów ze względu na problemy, czy wyjątki może negatywnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="157ad-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="157ad-109">Aby zwiększyć wydajność, jest możliwość użycia wzorca Tester Doer lub wzorcu analizy spróbuj opisanego w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="157ad-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="157ad-110">Wzorzec Tester Doer</span><span class="sxs-lookup"><span data-stu-id="157ad-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="157ad-111">Czasami można poprawić wydajność elementu członkowskiego Zgłaszanie wyjątku przez dzielenie element członkowski na dwie części.</span><span class="sxs-lookup"><span data-stu-id="157ad-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="157ad-112">Przyjrzyjmy się <xref:System.Collections.Generic.ICollection%601.Add%2A> metody <xref:System.Collections.Generic.ICollection%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="157ad-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="157ad-113">Metoda `Add` zgłasza wyjątek, jeśli kolekcja jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="157ad-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="157ad-114">Może to być problem z wydajnością w scenariuszach, w których można oczekiwać wywołanie metody często niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="157ad-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="157ad-115">Jednym ze sposobów złagodzić problem jest aby sprawdzić, czy kolekcja jest zapisywalny, przed podjęciem próby dodania wartości.</span><span class="sxs-lookup"><span data-stu-id="157ad-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="157ad-116">Element członkowski wykorzystywane do testowania warunek, który w naszym przykładzie jest właściwość `IsReadOnly`, jest określany jako tester.</span><span class="sxs-lookup"><span data-stu-id="157ad-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="157ad-117">Element członkowski używany do wykonywania operacji potencjalnie przerzucane, `Add` metody w tym przykładzie jest określana jako doer.</span><span class="sxs-lookup"><span data-stu-id="157ad-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="157ad-118">**ROZWAŻ ✓** wzorzec Tester Doer dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="157ad-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="157ad-119">Spróbuj analizy wzorca</span><span class="sxs-lookup"><span data-stu-id="157ad-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="157ad-120">W przypadku bardzo ważnych wydajności interfejsów API należy użyć wzorzec szybszy niż wzorzec Tester Doer opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="157ad-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="157ad-121">Wzorzec wywołuje dostosowywania nazwę elementu członkowskiego, aby dobrze zdefiniowany testu przypadek część semantyki elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="157ad-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="157ad-122">Na przykład <xref:System.DateTime> definiuje <xref:System.DateTime.Parse%2A> metodę, która zgłasza wyjątek, jeśli podczas analizowania ciągu nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="157ad-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="157ad-123">Definiuje również odpowiedniego <xref:System.DateTime.TryParse%2A> metodę, która podejmuje próbę analizy, ale zwraca wartość false, jeśli podczas analizowania zakończy się niepowodzeniem i zwraca wynik w pomyślnym analizy przy użyciu `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="157ad-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="157ad-124">Podczas używania tego wzorca, jest zdefiniowanie funkcji spróbuj względem strict.</span><span class="sxs-lookup"><span data-stu-id="157ad-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="157ad-125">W przypadku niepowodzenia element członkowski przyczyn innych niż spróbuj dobrze zdefiniowany element członkowski musi nadal throw odpowiednich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="157ad-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="157ad-126">**ROZWAŻ ✓** wzorzec spróbuj analizy dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="157ad-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="157ad-127">**CZY ✓** Użyj prefiksu "Try" i wartość logiczną zwracanego typu dla metody implementacja tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="157ad-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="157ad-128">**CZY ✓** Podaj elementu członkowskiego zgłaszanie wyjątków dla każdego elementu członkowskiego przy użyciu wzorca spróbuj analizy.</span><span class="sxs-lookup"><span data-stu-id="157ad-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="157ad-129">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="157ad-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="157ad-130">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="157ad-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157ad-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="157ad-131">See Also</span></span>  
 [<span data-ttu-id="157ad-132">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="157ad-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="157ad-133">Wskazówek dotyczących wyjątków</span><span class="sxs-lookup"><span data-stu-id="157ad-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)