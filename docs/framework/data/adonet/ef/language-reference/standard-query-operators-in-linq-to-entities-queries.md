---
title: "Standardowe operatory zapytań w składniku LINQ to Entities zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97782834480e8acb5f66d8da2099089b1c47e093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a><span data-ttu-id="70ed4-102">Standardowe operatory zapytań w składniku LINQ to Entities zapytań</span><span class="sxs-lookup"><span data-stu-id="70ed4-102">Standard Query Operators in LINQ to Entities Queries</span></span>
<span data-ttu-id="70ed4-103">W zapytaniu możesz określić informacje, które mają zostać pobrane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-103">In a query, you specify the information that you want to retrieve from the data source.</span></span> <span data-ttu-id="70ed4-104">Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest.</span><span class="sxs-lookup"><span data-stu-id="70ed4-104">A query can also specify how that information should be sorted, grouped, and shaped before it is returned.</span></span> <span data-ttu-id="70ed4-105">LINQ udostępnia zestaw metod standardowych zapytania, które można użyć w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="70ed4-105">LINQ provides a set of standard query methods that you can use in a query.</span></span> <span data-ttu-id="70ed4-106">Większość tych metod działać na sekwencji; w tym kontekście sekwencji jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="70ed4-106">Most of these methods operate on sequences; in this context, a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="70ed4-107">Funkcja zapytania operatorów standardowej kwerendy obejmuje filtrowania, projekcji agregacji, sortowanie, grupowanie, stronicowania i więcej.</span><span class="sxs-lookup"><span data-stu-id="70ed4-107">The standard query operators query functionality includes filtering, projection, aggregation, sorting, grouping, paging, and more.</span></span> <span data-ttu-id="70ed4-108">Standardowe operatory są wyposażone w dedykowane składni słowa kluczowego, dzięki czemu można wywołać przy użyciu składni wyrażeń zapytania zapytań niektórych często używane.</span><span class="sxs-lookup"><span data-stu-id="70ed4-108">Some of the more frequently used standard query operators have dedicated keyword syntax so that they can be called by using query expression syntax.</span></span> <span data-ttu-id="70ed4-109">Wyrażenia zapytania jest inny, bardziej czytelny sposobem express zapytania niż równoważne oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="70ed4-109">A query expression is a different, more readable way to express a query than the method-based equivalent.</span></span> <span data-ttu-id="70ed4-110">Klauzule wyrażenia zapytania są przekształcane na wywołania metody zapytań w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-110">Query expression clauses are translated into calls to the query methods at compile time.</span></span> <span data-ttu-id="70ed4-111">Listę standardowych operatorów zapytań zawierających klauzule wyrażenia zapytania równoważne zawiera [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="70ed4-111">For a list of standard query operators that have equivalent query expression clauses, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="70ed4-112">Nie wszystkie standardowe operatory zapytań są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="70ed4-112">Not all of the standard query operators are supported in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span> <span data-ttu-id="70ed4-113">Aby uzyskać więcej informacji, zobacz [obsługiwane i nieobsługiwane metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="70ed4-113">For more information, see [Supported and Unsupported LINQ Methods (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).</span></span> <span data-ttu-id="70ed4-114">Ten temat zawiera informacje o standardowych operatorów zapytań, które są specyficzne dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ed4-114">This topic provides information about the standard query operators that is specific to [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span> <span data-ttu-id="70ed4-115">Aby uzyskać więcej informacji o znanych problemach w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, zobacz [znanych problemów i uwagi w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="70ed4-115">For more information about known issues in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, see [Known Issues and Considerations in LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).</span></span>  
  
## <a name="projection-and-filtering-methods"></a><span data-ttu-id="70ed4-116">Filtrowanie metod i projekcji</span><span class="sxs-lookup"><span data-stu-id="70ed4-116">Projection and Filtering Methods</span></span>  
 <span data-ttu-id="70ed4-117">*Projekcja* odwołuje się do przekształcania elementy zestawu w formie żądanego wyników.</span><span class="sxs-lookup"><span data-stu-id="70ed4-117">*Projection* refers to transforming the elements of a result set into a desired form.</span></span> <span data-ttu-id="70ed4-118">Na przykład można wyświetlać podzbiór właściwości muszą z każdego obiektu w wyniku ustawisz, możesz właściwości projektu i wykonać obliczenia matematyczne na nim lub można wyświetlać cały obiekt z zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="70ed4-118">For example, you can project a subset of the properties you need from each object in the result set, you can project a property and perform a mathematical calculation on it, or you can project the entire object from the result set.</span></span> <span data-ttu-id="70ed4-119">Metody projekcji `Select` i `SelectMany`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-119">The projection methods are `Select` and `SelectMany`.</span></span>  
  
 <span data-ttu-id="70ed4-120">*Filtrowanie* odwołuje się do operacji ograniczyć zestaw wyników do zawierać tylko elementy, spełniające określony warunek.</span><span class="sxs-lookup"><span data-stu-id="70ed4-120">*Filtering* refers to the operation of restricting the result set to contain only those elements that match a specified condition.</span></span> <span data-ttu-id="70ed4-121">Metoda filtrowania jest `Where`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-121">The filtering method is `Where`.</span></span>  
  
 <span data-ttu-id="70ed4-122">Większość przeciążeń projekcji i filtrowanie metody są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], z wyjątkiem tych, które akceptują argument pozycyjny.</span><span class="sxs-lookup"><span data-stu-id="70ed4-122">Most overloads of the projection and filtering methods are supported in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], with the exception of those that accept a positional argument.</span></span>  
  
## <a name="join-methods"></a><span data-ttu-id="70ed4-123">Dołącz do metody</span><span class="sxs-lookup"><span data-stu-id="70ed4-123">Join Methods</span></span>  
 <span data-ttu-id="70ed4-124">Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, których nie można nawigować relacje między sobą.</span><span class="sxs-lookup"><span data-stu-id="70ed4-124">Joining is an important operation in queries that target data sources that have no navigable relationships to each other.</span></span> <span data-ttu-id="70ed4-125">Sprzężenia dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami w źródle danych, które współużytkują wspólne atrybutu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="70ed4-125">A join of two data sources is the association of objects in one data source with objects in the other data source that share a common attribute or property.</span></span> <span data-ttu-id="70ed4-126">Metody sprzężenia `Join` i `GroupJoin`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-126">The join methods are `Join` and `GroupJoin`.</span></span>  
  
 <span data-ttu-id="70ed4-127">Większość przeciążenia metody sprzężenia są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IEqualityComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="70ed4-127">Most overloads of the join methods are supported, with the exception of those that use a <xref:System.Collections.Generic.IEqualityComparer%601>.</span></span> <span data-ttu-id="70ed4-128">Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-128">This is because the comparer cannot be translated to the data source.</span></span>  
  
## <a name="set-methods"></a><span data-ttu-id="70ed4-129">Ustaw metody</span><span class="sxs-lookup"><span data-stu-id="70ed4-129">Set Methods</span></span>  
 <span data-ttu-id="70ed4-130">Operacje na zestawie w składniku LINQ to operacji zapytania, które podstawą ich zestawów wyników obecności lub braku równoważne elementów w tym samym lub w innej kolekcji (lub zestawu).</span><span class="sxs-lookup"><span data-stu-id="70ed4-130">Set operations in LINQ are query operations that base their result sets on the presence or absence of equivalent elements within the same or in another collection (or set).</span></span> <span data-ttu-id="70ed4-131">Metody set `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, i `Union`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-131">The set methods are `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, and `Union`.</span></span>  
  
 <span data-ttu-id="70ed4-132">Większość przeciążenia metody set są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], ale istnieją pewne różnice w zachowaniu w porównaniu do LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="70ed4-132">Most overloads of the set methods are supported in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], though there are some differences in behavior compared to LINQ to Objects.</span></span> <span data-ttu-id="70ed4-133">Jednak ustawić metody, które używają <xref:System.Collections.Generic.IEqualityComparer%601> nie są obsługiwane, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-133">However, set methods that use an <xref:System.Collections.Generic.IEqualityComparer%601> are not supported because the comparer cannot be translated to the data source.</span></span>  
  
## <a name="ordering-methods"></a><span data-ttu-id="70ed4-134">Metody sortowania</span><span class="sxs-lookup"><span data-stu-id="70ed4-134">Ordering Methods</span></span>  
 <span data-ttu-id="70ed4-135">Porządkowanie lub sortowania, odwołuje się do kolejność elementów na podstawie atrybutów co najmniej jeden zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="70ed4-135">Ordering, or sorting, refers to the ordering the elements of a result set based on one or more attributes.</span></span> <span data-ttu-id="70ed4-136">Określając więcej niż jednego kryterium sortowania, mogą być dzielone powiązania w grupie.</span><span class="sxs-lookup"><span data-stu-id="70ed4-136">By specifying more than one sort criterion, you can break ties within a group.</span></span>  
  
 <span data-ttu-id="70ed4-137">Większość przeciążenia metody sortowania są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="70ed4-137">Most overloads of the ordering methods are supported, with the exception of those that use an <xref:System.Collections.Generic.IComparer%601>.</span></span> <span data-ttu-id="70ed4-138">Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-138">This is because the comparer cannot be translated to the data source.</span></span> <span data-ttu-id="70ed4-139">Metody sortowania są `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, i `Reverse`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-139">The ordering methods are `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, and `Reverse`.</span></span>  
  
 <span data-ttu-id="70ed4-140">Ponieważ zapytanie jest wykonywane w źródle danych, porządkowania zachowanie może różnić się od zapytania wykonywane w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="70ed4-140">Because the query is executed on the data source, the ordering behavior may differ from queries executed in the CLR.</span></span> <span data-ttu-id="70ed4-141">Jest to spowodowane porządkowania opcje, takie jak przypadku porządkowania kanji kolejności i kolejność wartości null, można ustawić w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-141">This is because ordering options, such as case ordering, kanji ordering, and null ordering, can be set in the data source.</span></span> <span data-ttu-id="70ed4-142">W zależności od źródła danych te opcje sortowania może wygenerować różne wyniki niż w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="70ed4-142">Depending on the data source, these ordering options might produce different results than in the CLR.</span></span>  
  
 <span data-ttu-id="70ed4-143">Jeśli określisz tego samego selektora kluczy w więcej niż jedną operację porządkowania zostaną utworzone zduplikowane porządkowania.</span><span class="sxs-lookup"><span data-stu-id="70ed4-143">If you specify the same key selector in more than one ordering operation, a duplicate ordering will be produced.</span></span> <span data-ttu-id="70ed4-144">To nie jest prawidłowy i zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="70ed4-144">This is not valid and an exception will be thrown.</span></span>  
  
## <a name="grouping-methods"></a><span data-ttu-id="70ed4-145">Grupowanie metody</span><span class="sxs-lookup"><span data-stu-id="70ed4-145">Grouping Methods</span></span>  
 <span data-ttu-id="70ed4-146">Grupowanie odwołuje się do umieszczenia danych w grupy tak, aby Wspólny atrybut Udostępnianie elementów w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="70ed4-146">Grouping refers to placing data into groups so that the elements in each group share a common attribute.</span></span> <span data-ttu-id="70ed4-147">Metoda grupowania jest `GroupBy`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-147">The grouping method is `GroupBy`.</span></span>  
  
 <span data-ttu-id="70ed4-148">Większość przeciążenia metody grupowania są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IEqualityComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="70ed4-148">Most overloads of the grouping methods are supported, with the exception of those that use an <xref:System.Collections.Generic.IEqualityComparer%601>.</span></span> <span data-ttu-id="70ed4-149">Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-149">This is because the comparer cannot be translated to the data source.</span></span>  
  
 <span data-ttu-id="70ed4-150">Metody grupowania są mapowane do źródła danych przy użyciu różnych podzapytania dla selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="70ed4-150">The grouping methods are mapped to the data source using a distinct sub-query for the key selector.</span></span> <span data-ttu-id="70ed4-151">Zapytanie podrzędne porównania selektora kluczy jest wykonywane przy użyciu semantyki źródła danych, w tym zagadnienia związane z porównanie `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="70ed4-151">The key selector comparison sub-query is executed by using the semantics of the data source, including issues related to comparing `null` values.</span></span>  
  
## <a name="aggregate-methods"></a><span data-ttu-id="70ed4-152">Metody agregacji</span><span class="sxs-lookup"><span data-stu-id="70ed4-152">Aggregate Methods</span></span>  
 <span data-ttu-id="70ed4-153">Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="70ed4-153">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="70ed4-154">Na przykład obliczanie średnia temperatura codzienne z miesięcznej codziennie temperatury wartości jest operacją agregacji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-154">For example, calculating the average daily temperature from a month's worth of daily temperature values is an aggregation operation.</span></span> <span data-ttu-id="70ed4-155">Metody agregacji są `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-155">The aggregate methods are `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum`.</span></span>  
  
 <span data-ttu-id="70ed4-156">Większość przeciążenia metody agregacji są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="70ed4-156">Most overloads of the aggregate methods are supported.</span></span> <span data-ttu-id="70ed4-157">Zachowania związane z wartości null metody agregacji korzysta z semantyki źródła danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-157">For behavior related to null values, the aggregate methods use the data source semantics.</span></span> <span data-ttu-id="70ed4-158">Zachowanie metody agregacji w przypadku wartości null, mogą się różnić, w zależności od używanego źródła danych zaplecza.</span><span class="sxs-lookup"><span data-stu-id="70ed4-158">The behavior of the aggregation methods when null values are involved might be different, depending on which back-end data source is being used.</span></span> <span data-ttu-id="70ed4-159">Metoda agregacji zachowanie za pomocą semantyki źródła danych może być również inny niż oczekiwano z metody CLR.</span><span class="sxs-lookup"><span data-stu-id="70ed4-159">Aggregate method behavior using the semantics of the data source might also be different from what is expected from CLR methods.</span></span> <span data-ttu-id="70ed4-160">Na przykład, domyślne zachowanie dla `Sum` metody na serwerze SQL ma ignorować wszystkie wartości null zamiast generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="70ed4-160">For example, the default behavior for the `Sum` method on SQL Server is to ignore any null values instead of throwing an exception.</span></span>  
  
 <span data-ttu-id="70ed4-161">Wszelkie wyjątki wynikających z agregacji, takie jak przepełnienie z `Sum` działać i będą zgłaszane jako źródło danych czy wyjątki Entity Framework podczas materialization wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="70ed4-161">Any exceptions that result from aggregation, such as an overflow from the `Sum` function, are thrown as data source exceptions or Entity Framework exceptions during the materialization of the query results.</span></span>  
  
 <span data-ttu-id="70ed4-162">Dla tych metod, które obejmują obliczenia w sekwencji, takich jak `Sum` lub `Average`, rzeczywiste obliczenia jest wykonywane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="70ed4-162">For those methods that involve a calculation over a sequence, such as `Sum` or `Average`, the actual calculation is performed on the server.</span></span> <span data-ttu-id="70ed4-163">W związku z tym konwersje typów na serwerze może wystąpić utrata dokładności i wyniki mogą różnić się od oczekiwanej, używając semantyki CLR.</span><span class="sxs-lookup"><span data-stu-id="70ed4-163">As a result, type conversions and loss of precision might occur on the server, and the results might differ from what is expected using CLR semantics.</span></span>  
  
 <span data-ttu-id="70ed4-164">W poniższej tabeli przedstawiono to domyślne zachowanie metody agregacji wartości null/inne niż null:</span><span class="sxs-lookup"><span data-stu-id="70ed4-164">The default behavior of the aggregate methods for null/non-null values is shown in the following table:</span></span>  
  
|<span data-ttu-id="70ed4-165">Metoda</span><span class="sxs-lookup"><span data-stu-id="70ed4-165">Method</span></span>|<span data-ttu-id="70ed4-166">Brak danych</span><span class="sxs-lookup"><span data-stu-id="70ed4-166">No data</span></span>|<span data-ttu-id="70ed4-167">Wszystkie wartości null</span><span class="sxs-lookup"><span data-stu-id="70ed4-167">All null values</span></span>|<span data-ttu-id="70ed4-168">Niektóre wartości null</span><span class="sxs-lookup"><span data-stu-id="70ed4-168">Some null values</span></span>|<span data-ttu-id="70ed4-169">Nie wartości null</span><span class="sxs-lookup"><span data-stu-id="70ed4-169">No null values</span></span>|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|<span data-ttu-id="70ed4-170">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-170">Returns null.</span></span>|<span data-ttu-id="70ed4-171">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-171">Returns null.</span></span>|<span data-ttu-id="70ed4-172">Zwraca średnią z wartości inne niż null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-172">Returns the average of the non-null values in a sequence.</span></span>|<span data-ttu-id="70ed4-173">Oblicza średnią sekwencję wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-173">Computes the average of a sequence of numeric values.</span></span>|  
|`Count`|<span data-ttu-id="70ed4-174">Zwraca wartość 0</span><span class="sxs-lookup"><span data-stu-id="70ed4-174">Returns 0</span></span>|<span data-ttu-id="70ed4-175">Zwraca liczbę wartości null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-175">Returns the number of null values in the sequence.</span></span>|<span data-ttu-id="70ed4-176">Zwraca liczbę wartości null i innych niż null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-176">Returns the number of null and non-null values in the sequence.</span></span>|<span data-ttu-id="70ed4-177">Zwraca liczbę elementów w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-177">Returns the number of elements in the sequence.</span></span>|  
|`Max`|<span data-ttu-id="70ed4-178">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-178">Returns null.</span></span>|<span data-ttu-id="70ed4-179">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-179">Returns null.</span></span>|<span data-ttu-id="70ed4-180">Zwraca maksymalną wartość inną niż null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-180">Returns the maximum non-null value in a sequence.</span></span>|<span data-ttu-id="70ed4-181">Zwraca maksymalną wartość w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-181">Returns the maximum value in a sequence.</span></span>|  
|`Min`|<span data-ttu-id="70ed4-182">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-182">Returns null.</span></span>|<span data-ttu-id="70ed4-183">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-183">Returns null.</span></span>|<span data-ttu-id="70ed4-184">Zwraca minimalną wartość inną niż null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-184">Returns the minimum non-null value in a sequence.</span></span>|<span data-ttu-id="70ed4-185">Zwraca minimalną wartość w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-185">Returns the minimum value in a sequence.</span></span>|  
|`Sum`|<span data-ttu-id="70ed4-186">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-186">Returns null.</span></span>|<span data-ttu-id="70ed4-187">Zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-187">Returns null.</span></span>|<span data-ttu-id="70ed4-188">Zwraca sumę wartości innych niż null w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-188">Returns the sum of the non-null value in a sequence.</span></span>|<span data-ttu-id="70ed4-189">Oblicza sumę sekwencję wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-189">Computes the sum of a sequence of numeric values.</span></span>|  
  
## <a name="type-methods"></a><span data-ttu-id="70ed4-190">Metody typu</span><span class="sxs-lookup"><span data-stu-id="70ed4-190">Type Methods</span></span>  
 <span data-ttu-id="70ed4-191">Te dwie metody LINQ, które zajmują się konwersji typu i testowania są obsługiwane w kontekście [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ed4-191">The two LINQ methods that deal with type conversion and testing are both supported in the context of the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="70ed4-192">Oznacza to, że tylko obsługiwane typy to typy, które mapują do odpowiedniego [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="70ed4-192">This means that the only supported types are types that map to the appropriate [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] type.</span></span> <span data-ttu-id="70ed4-193">Aby uzyskać listę tych typów, zobacz [typu modelu koncepcyjnego (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span><span class="sxs-lookup"><span data-stu-id="70ed4-193">For a list of these types, see [Conceptual Model Types (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span></span> <span data-ttu-id="70ed4-194">Metody typu są `Convert` i `OfType`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-194">The type methods are `Convert` and `OfType`.</span></span>  
  
 <span data-ttu-id="70ed4-195">`OfType`jest obsługiwana dla typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="70ed4-195">`OfType` is supported for entity types.</span></span> <span data-ttu-id="70ed4-196">`Convert`jest obsługiwana dla typów pierwotnych modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="70ed4-196">`Convert` is supported for conceptual model primitive types.</span></span>  <span data-ttu-id="70ed4-197">C# `is` i `as` metody również są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="70ed4-197">The C# `is` and `as` methods are also supported.</span></span>  
  
## <a name="paging-methods"></a><span data-ttu-id="70ed4-198">Metody stronicowania</span><span class="sxs-lookup"><span data-stu-id="70ed4-198">Paging Methods</span></span>  
 <span data-ttu-id="70ed4-199">Operacja stronicowania zwrócić element jednej, określonej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="70ed4-199">Paging operations return a single, specific element from a sequence.</span></span> <span data-ttu-id="70ed4-200">Metody elementu `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take`, `TakeWhile`.</span><span class="sxs-lookup"><span data-stu-id="70ed4-200">The element methods are `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take`, `TakeWhile`.</span></span>  
  
 <span data-ttu-id="70ed4-201">Wiele metod stronicowania nie są obsługiwane ze względu na niemożność mapowania funkcji do źródła danych lub brak niejawnego porządkowanie zestawów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="70ed4-201">A number of the paging methods are not supported, due either to the inability to map functions to the data source or to the lack of implicit ordering of sets on the data source.</span></span> <span data-ttu-id="70ed4-202">Metody, które zwracają wartości domyślne są ograniczone do modelu koncepcyjnego typy pierwotne i typy referencyjne przy użyciu ustawień domyślnych wartości null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-202">Methods that return a default value are restricted to conceptual model primitive types and reference types with null defaults.</span></span> <span data-ttu-id="70ed4-203">Metody stronicowania, które są wykonywane na pustej sekwencji zwróci wartość null.</span><span class="sxs-lookup"><span data-stu-id="70ed4-203">Paging methods that are executed on an empty sequence will return null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ed4-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70ed4-204">See Also</span></span>  
 [<span data-ttu-id="70ed4-205">Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)</span><span class="sxs-lookup"><span data-stu-id="70ed4-205">Supported and Unsupported LINQ Methods (LINQ to Entities)</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [<span data-ttu-id="70ed4-206">Operatory standardowe zapytań — omówienie</span><span class="sxs-lookup"><span data-stu-id="70ed4-206">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)