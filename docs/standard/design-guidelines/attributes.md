---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86fa2556e6b8fb82e31a7d4753354aa2dff627ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attributes"></a><span data-ttu-id="e94bc-102">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e94bc-102">Attributes</span></span>
<span data-ttu-id="e94bc-103"><xref:System.Attribute?displayProperty=nameWithType>Klasa podstawowa służy do definiowania atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e94bc-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="e94bc-104">Atrybuty są adnotacje, które mogą być dodawane do elementów programowania, takich jak zestawy, typy elementów członkowskich i parametry.</span><span class="sxs-lookup"><span data-stu-id="e94bc-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="e94bc-105">Są przechowywane w metadanych zestawu i jest dostępny w czasie wykonywania za pomocą odbicia interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="e94bc-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="e94bc-106">Na przykład platformę definiuje <xref:System.ObsoleteAttribute>, które można zastosować do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e94bc-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="e94bc-107">Atrybuty mogą mieć co najmniej jednej właściwości zawierających dodatkowe dane powiązany z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="e94bc-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="e94bc-108">Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji w którym typ lub element członkowski został przestarzałe i opis nowych interfejsów API, zastępując przestarzałe interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="e94bc-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="e94bc-109">Niektóre właściwości atrybutu należy określić, gdy jest stosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="e94bc-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="e94bc-110">Te są określane jako wymagane właściwości lub liczbą wymaganych argumentów, ponieważ są one reprezentowane jako parametry pozycyjne konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e94bc-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="e94bc-111">Na przykład <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> właściwość <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.</span><span class="sxs-lookup"><span data-stu-id="e94bc-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="e94bc-112">Właściwości, które nie muszą być określone, gdy jest stosowany atrybut są nazywane właściwości opcjonalnych (lub argumentów opcjonalnych).</span><span class="sxs-lookup"><span data-stu-id="e94bc-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="e94bc-113">Są one reprezentowane przez można ustawić właściwości.</span><span class="sxs-lookup"><span data-stu-id="e94bc-113">They are represented by settable properties.</span></span> <span data-ttu-id="e94bc-114">Kompilatory Podaj specjalnej składni ustawić te właściwości, gdy jest stosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="e94bc-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="e94bc-115">Na przykład <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> właściwość reprezentuje opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="e94bc-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="e94bc-116">**CZY ✓** nazwy klas atrybutów niestandardowych z sufiksem "Atrybutu".</span><span class="sxs-lookup"><span data-stu-id="e94bc-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="e94bc-117">**CZY ✓** zastosować <xref:System.AttributeUsageAttribute> atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e94bc-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="e94bc-118">**CZY ✓** Podaj można ustawić właściwości dla argumentów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="e94bc-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="e94bc-119">**CZY ✓** Podaj właściwości tylko do pobrania dla wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="e94bc-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="e94bc-120">**CZY ✓** podać parametry konstruktora zainicjować właściwości odpowiadającej wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="e94bc-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="e94bc-121">Każdy parametr powinien mieć taką samą nazwę (mimo że za pomocą innej wielkości liter), jak odpowiadających im właściwości.</span><span class="sxs-lookup"><span data-stu-id="e94bc-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="e94bc-122">**X należy UNIKAĆ** podając parametrami konstruktora zainicjować właściwości odpowiadającej Argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e94bc-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="e94bc-123">Innymi słowy nie ma właściwości, które można ustawić za pomocą metody konstruktora, jak i ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="e94bc-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="e94bc-124">Niniejsze wytyczne sprawia, że bardzo jawne argumenty, które są opcjonalne i które są wymagane i pozwala uniknąć konieczności ten sam efekt na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="e94bc-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="e94bc-125">**X należy UNIKAĆ** przeładowania konstruktorów atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e94bc-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="e94bc-126">Wyraźnie mających tylko jeden konstruktor komunikuje się użytkownika, które argumentów wymaganych i opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="e94bc-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="e94bc-127">**CZY ✓** zapieczętować klas atrybutów niestandardowych, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e94bc-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="e94bc-128">Dzięki temu można szybciej wyszukiwania dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e94bc-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="e94bc-129">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e94bc-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e94bc-130">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="e94bc-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94bc-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e94bc-131">See Also</span></span>  
 [<span data-ttu-id="e94bc-132">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="e94bc-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="e94bc-133">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="e94bc-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)