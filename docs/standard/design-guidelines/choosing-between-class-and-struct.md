---
title: "Wybór między klasy i struktury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6659853e9c410ece3233cfa630c9066303a871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="059ba-102">Wybór między klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="059ba-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="059ba-103">Jednym z podstawowych decyzji projektowych który skierowany framework designer na co jest czy zaprojektować typu jako klasy (Typ referencyjny) lub struct (typ wartości).</span><span class="sxs-lookup"><span data-stu-id="059ba-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="059ba-104">Dobrą znajomością różnice w zachowaniu typy wartości i typy referencyjne odgrywa kluczową rolę w podejmowaniu ten wybór.</span><span class="sxs-lookup"><span data-stu-id="059ba-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="059ba-105">Pierwszy różnica między typy referencyjne i typów wartości, które firma Microsoft będzie uwzględniać typy referencyjne są przydzielone na stercie i odzyskiwanie zbierane typów wartości są przydzielane na stosie lub tekście zawierający typów, a kiedy alokację stosu cofa lub po ich typ zawierający pobiera alokację.</span><span class="sxs-lookup"><span data-stu-id="059ba-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="059ba-106">W związku z tym alokacji i dezalokacji typów wartości są zwykle tańsze niż alokacji i dezalokacji typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="059ba-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="059ba-107">Następnie tablice odwołania, których typy są przydzielone poza zewnętrznych, co oznacza tablicy, która elementy są tylko odwołania do wystąpienia typu referencyjnego znajdującej się na stosie.</span><span class="sxs-lookup"><span data-stu-id="059ba-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="059ba-108">Tablice typu wartości są przydzielane wbudowane, co oznacza, że elementy tablicy są bieżące wystąpienia typu wartości.</span><span class="sxs-lookup"><span data-stu-id="059ba-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="059ba-109">W związku z tym alokacji i dezalokacji tablic typu wartości są znacznie tańszy niż alokacji i dezalokacji tablic typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="059ba-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="059ba-110">Ponadto w większości przypadków tablic typu wartości wykazują znacznie lepszą miejscowości odwołania.</span><span class="sxs-lookup"><span data-stu-id="059ba-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="059ba-111">Różnica dalej jest powiązany z użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="059ba-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="059ba-112">Typy wartości get opakowany po Rzutowanie na typ referencyjny lub jednego z interfejsów, które wdrażają.</span><span class="sxs-lookup"><span data-stu-id="059ba-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="059ba-113">Następnie otrzymują oni rozpakowany podczas rzutowania do typu wartości.</span><span class="sxs-lookup"><span data-stu-id="059ba-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="059ba-114">Ponieważ pola są obiekty, które są przydzielone na stercie i są zbierane w pamięci, zbyt dużo konwersja boxing i Rozpakowywanie może mieć negatywny wpływ na stercie modułu zbierającego elementy bezużyteczne i ostatecznie wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="059ba-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="059ba-115">Z kolei nie takie opakowanie występuje jako typów referencyjnych są rzutowania.</span><span class="sxs-lookup"><span data-stu-id="059ba-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="059ba-116">Następnie przypisania typu odwołanie skopiuj odwołanie, natomiast wartość typu przypisania skopiować całą wartość.</span><span class="sxs-lookup"><span data-stu-id="059ba-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="059ba-117">W związku z tym przypisania typów dużych odwołania są tańsze niż przypisania duża wartość.</span><span class="sxs-lookup"><span data-stu-id="059ba-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="059ba-118">Na koniec typy referencyjne są przekazywane przez odwołanie, podczas gdy typy wartości są przekazywane przez wartość.</span><span class="sxs-lookup"><span data-stu-id="059ba-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="059ba-119">Zmiany do wystąpienia typu referencyjnego wpływają na wszystkie odwołania wskazujące wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="059ba-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="059ba-120">Wystąpienia typu wartości są kopiowane, gdy są one przekazywane przez wartość.</span><span class="sxs-lookup"><span data-stu-id="059ba-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="059ba-121">Po zmianie wystąpienia typu wartości on oczywiście nie wpływa na jej kopii.</span><span class="sxs-lookup"><span data-stu-id="059ba-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="059ba-122">Ponieważ kopie nie są jawnie tworzone przez użytkownika, ale niejawnie są tworzone, gdy argumenty są przekazywane lub zwracać wartości są zwracane typy wartości, które można zmienić może być trudne dla wielu użytkowników.</span><span class="sxs-lookup"><span data-stu-id="059ba-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="059ba-123">W związku z tym typów wartości powinno być niezmienialne.</span><span class="sxs-lookup"><span data-stu-id="059ba-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="059ba-124">Zasadą większość typów w ramach powinny być klasy.</span><span class="sxs-lookup"><span data-stu-id="059ba-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="059ba-125">Istnieje jednak kilka sytuacji, w których typ wartości właściwości stał się bardziej odpowiednie do użycia w strukturach.</span><span class="sxs-lookup"><span data-stu-id="059ba-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="059ba-126">**ROZWAŻ ✓** definiowania struktury zamiast klasy, jeśli wystąpienia typu małych i często krótkim okresie lub często są osadzone w innych obiektach.</span><span class="sxs-lookup"><span data-stu-id="059ba-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="059ba-127">**X należy UNIKAĆ** definiowania struktury, chyba że typ ma wszystkie następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="059ba-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="059ba-128">Logicznie reprezentuje pojedynczą wartość, podobnie jak typy pierwotne (`int`, `double`itp.).</span><span class="sxs-lookup"><span data-stu-id="059ba-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="059ba-129">Ma rozmiar wystąpienia w obszarze 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="059ba-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="059ba-130">Jest niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="059ba-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="059ba-131">Nie będzie miał zostać opakowany często.</span><span class="sxs-lookup"><span data-stu-id="059ba-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="059ba-132">We wszystkich innych przypadkach należy zdefiniować typy użytkownika jako klasy.</span><span class="sxs-lookup"><span data-stu-id="059ba-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="059ba-133">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="059ba-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="059ba-134">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="059ba-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059ba-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="059ba-135">See Also</span></span>  
 [<span data-ttu-id="059ba-136">Wytyczne dotyczące projektowania typu</span><span class="sxs-lookup"><span data-stu-id="059ba-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="059ba-137">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="059ba-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)