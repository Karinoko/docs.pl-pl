---
title: "Zapytania w składniku LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 220416aa4e282cb342ee6080d9040f9f4818fbf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="queries-in-linq-to-entities"></a><span data-ttu-id="647b5-102">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="647b5-102">Queries in LINQ to Entities</span></span>
<span data-ttu-id="647b5-103">Zapytanie jest wyrażenie, które pobiera dane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="647b5-103">A query is an expression that retrieves data from a data source.</span></span> <span data-ttu-id="647b5-104">Zapytania są zwykle zapisywane w język kwerendy specjalnych, takich jak SQL relacyjnych baz danych i XQuery dla formatu XML.</span><span class="sxs-lookup"><span data-stu-id="647b5-104">Queries are usually expressed in a specialized query language, such as SQL for relational databases and XQuery for XML.</span></span> <span data-ttu-id="647b5-105">W związku z tym deweloperzy było nauczyć się nowy język kwerendy dla każdego typu źródła danych lub format danych są zapytania.</span><span class="sxs-lookup"><span data-stu-id="647b5-105">Therefore, developers have had to learn a new query language for each type of data source or data format that they query.</span></span> <span data-ttu-id="647b5-106">Zapytanie języku zintegrowanym (LINQ) oferuje prostszy, spójny model do pracy z danymi w różnych rodzajów źródeł danych i formaty.</span><span class="sxs-lookup"><span data-stu-id="647b5-106">Language-Integrated Query (LINQ) offers a simpler, consistent model for working with data across various kinds of data sources and formats.</span></span> <span data-ttu-id="647b5-107">Zapytania LINQ zawsze do pracy z programowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="647b5-107">In a LINQ query, you always work with programming objects.</span></span>  
  
 <span data-ttu-id="647b5-108">Operacji zapytania LINQ składa się z trzech akcji: uzyskać źródła danych lub źródła, Utwórz zapytanie i wykonać zapytanie.</span><span class="sxs-lookup"><span data-stu-id="647b5-108">A LINQ query operation consists of three actions: obtain the data source or sources, create the query, and execute the query.</span></span>  
  
 <span data-ttu-id="647b5-109">Źródła danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> ogólny interfejs lub <xref:System.Linq.IQueryable%601> ogólny interfejs można tworzyć zapytania za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="647b5-109">Data sources that implement the <xref:System.Collections.Generic.IEnumerable%601> generic interface or the <xref:System.Linq.IQueryable%601> generic interface can be queried through LINQ.</span></span> <span data-ttu-id="647b5-110">Wystąpienia ogólnych <xref:System.Data.Objects.ObjectQuery%601> klasy, która implementuje ogólnego <xref:System.Linq.IQueryable%601> interfejsu, służyć jako źródło danych dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="647b5-110">Instances of the generic <xref:System.Data.Objects.ObjectQuery%601> class, which implements the generic <xref:System.Linq.IQueryable%601> interface, serve as the data source for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span> <span data-ttu-id="647b5-111"><xref:System.Data.Objects.ObjectQuery%601> Klasa ogólna reprezentuje kwerendę, która zwraca kolekcję zero lub więcej obiektów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="647b5-111">The <xref:System.Data.Objects.ObjectQuery%601> generic class represents a query that returns a collection of zero or more typed objects.</span></span> <span data-ttu-id="647b5-112">Można także pozwolić kompilatora wnioskować o typie jednostki przy użyciu słowa kluczowego języka C# `var` (Dim w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="647b5-112">You can also let the compiler infer the type of an entity by using the C# keyword `var` (Dim in Visual Basic).</span></span>  
  
 <span data-ttu-id="647b5-113">W zapytaniu możesz określić dokładnie informacje, które mają zostać pobrane ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="647b5-113">In the query, you specify exactly the information that you want to retrieve from the data source.</span></span> <span data-ttu-id="647b5-114">Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest.</span><span class="sxs-lookup"><span data-stu-id="647b5-114">A query can also specify how that information should be sorted, grouped, and shaped before it is returned.</span></span> <span data-ttu-id="647b5-115">W składniku LINQ zapytanie jest przechowywana w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="647b5-115">In LINQ, a query is stored in a variable.</span></span> <span data-ttu-id="647b5-116">Jeśli zapytanie zwraca sekwencję wartości, samej zmiennej zapytania musi być typem zapytań.</span><span class="sxs-lookup"><span data-stu-id="647b5-116">If the query returns a sequence of values, the query variable itself must be a queryable type.</span></span> <span data-ttu-id="647b5-117">Ta zmienna zapytania Brak działania i zwraca żadnych danych; tylko przechowuje informacje o kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="647b5-117">This query variable takes no action and returns no data; it only stores the query information.</span></span> <span data-ttu-id="647b5-118">Po utworzeniu zapytania należy wykonać zapytania można pobrać żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="647b5-118">After you create a query you must execute that query to retrieve any data.</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="647b5-119">Składnia zapytania</span><span class="sxs-lookup"><span data-stu-id="647b5-119">Query Syntax</span></span>  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="647b5-120">zapytania mogą być składane w dwóch składnie: wyrażenie składnia zapytania i metody zapytań.</span><span class="sxs-lookup"><span data-stu-id="647b5-120"> queries can be composed in two different syntaxes: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="647b5-121">Składnia wyrażeń jest nowego w języku C# 3.0 i 9.0 Visual Basic i składa się z zestawu klauzule napisany w składni deklaratywnej podobny do języka Transact-SQL lub XQuery.</span><span class="sxs-lookup"><span data-stu-id="647b5-121">Query expression syntax is new in C# 3.0 and Visual Basic 9.0, and it consists of a set of clauses written in a declarative syntax similar to Transact-SQL or XQuery.</span></span> <span data-ttu-id="647b5-122">Jednak [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego (CLR) nie może odczytać sam składnia wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="647b5-122">However, the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] common language runtime (CLR) cannot read the query expression syntax itself.</span></span> <span data-ttu-id="647b5-123">W związku z tym podczas kompilacji wyrażenia zapytania są translacji obsługiwanym przez środowisko CLR: wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="647b5-123">Therefore, at compile time, query expressions are translated to something that the CLR does understand: method calls.</span></span> <span data-ttu-id="647b5-124">Te metody są określane jako *standardowych operatorów zapytań*.</span><span class="sxs-lookup"><span data-stu-id="647b5-124">These methods are known as the *standard query operators*.</span></span> <span data-ttu-id="647b5-125">Deweloper istnieje możliwość wywołania je bezpośrednio, używając składni metody zamiast za pomocą składni zapytań.</span><span class="sxs-lookup"><span data-stu-id="647b5-125">As a developer, you have the option of calling them directly by using method syntax, instead of using query syntax.</span></span> <span data-ttu-id="647b5-126">Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="647b5-126">For more information, see [Query Syntax and Method Syntax in LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
### <a name="query-expression-syntax"></a><span data-ttu-id="647b5-127">Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="647b5-127">Query Expression Syntax</span></span>  
 <span data-ttu-id="647b5-128">Wyrażenia zapytania są deklaratywne składnię.</span><span class="sxs-lookup"><span data-stu-id="647b5-128">Query expressions are a declarative query syntax.</span></span> <span data-ttu-id="647b5-129">Ta składnia umożliwia deweloperom Pisanie zapytań w języku wysokiego poziomu, który jest sformatowany podobny do języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="647b5-129">This syntax enables a developer to write queries in a high-level language that is formatted similar to Transact-SQL.</span></span> <span data-ttu-id="647b5-130">Przy użyciu składni wyrażeń zapytania, można wykonywać nawet złożone filtrowanie, kolejność i operacji grupowania na źródeł danych z minimalnym kodu.</span><span class="sxs-lookup"><span data-stu-id="647b5-130">By using query expression syntax, you can perform even complex filtering, ordering, and grouping operations on data sources with minimal code.</span></span> <span data-ttu-id="647b5-131">Aby uzyskać więcej informacji [podstawowe operacje zapytań (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="647b5-131">For more information, [Basic Query Operations (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span> <span data-ttu-id="647b5-132">Aby uzyskać przykłady pokazujące, które pokazują, jak używać składni wyrażenia zapytania zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="647b5-132">For examples that demonstrate how to use the query expression syntax, see the following topics:</span></span>  
  
-   [<span data-ttu-id="647b5-133">Przykłady składni wyrażeń zapytania: projekcji</span><span class="sxs-lookup"><span data-stu-id="647b5-133">Query Expression Syntax Examples: Projection</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="647b5-134">Przykłady składni wyrażeń zapytania: filtrowania</span><span class="sxs-lookup"><span data-stu-id="647b5-134">Query Expression Syntax Examples: Filtering</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [<span data-ttu-id="647b5-135">Przykłady składni wyrażeń zapytania: porządkowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-135">Query Expression Syntax Examples: Ordering</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [<span data-ttu-id="647b5-136">Przykłady składni wyrażeń zapytania: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="647b5-136">Query Expression Syntax Examples: Aggregate Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="647b5-137">Przykłady składni wyrażeń zapytania: partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-137">Query Expression Syntax Examples: Partitioning</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="647b5-138">Przykłady składni wyrażeń zapytania: Operatorów sprzężenia</span><span class="sxs-lookup"><span data-stu-id="647b5-138">Query Expression Syntax Examples: Join Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [<span data-ttu-id="647b5-139">Przykłady składni wyrażeń zapytania: Operatory Element</span><span class="sxs-lookup"><span data-stu-id="647b5-139">Query Expression Syntax Examples: Element Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="647b5-140">Przykłady składni wyrażeń zapytania: grupowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-140">Query Expression Syntax Examples: Grouping</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [<span data-ttu-id="647b5-141">Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="647b5-141">Query Expression Syntax Examples: Navigating Relationships</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a><span data-ttu-id="647b5-142">Składnia zapytań — metoda</span><span class="sxs-lookup"><span data-stu-id="647b5-142">Method-Based Query Syntax</span></span>  
 <span data-ttu-id="647b5-143">Innym sposobem tworzenia [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania jest za pomocą zapytań na podstawie metody.</span><span class="sxs-lookup"><span data-stu-id="647b5-143">Another way to compose [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries is by using method-based queries.</span></span> <span data-ttu-id="647b5-144">Składnia zapytania oparte na metodzie jest sekwencją metoda bezpośrednia wywołania metod operator LINQ, przekazując wyrażenia lambda jako parametry.</span><span class="sxs-lookup"><span data-stu-id="647b5-144">The method-based query syntax is a sequence of direct method calls to LINQ operator methods, passing lambda expressions as the parameters.</span></span> <span data-ttu-id="647b5-145">Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="647b5-145">For more information, see [Lambda Expressions](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span> <span data-ttu-id="647b5-146">Aby uzyskać przykłady pokazujące, które pokazują, jak używać składni oparte na metodzie zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="647b5-146">For examples that demonstrate how to use method-based syntax, see the following topics:</span></span>  
  
-   [<span data-ttu-id="647b5-147">Przykłady składni zapytania oparte na metodzie: projekcji</span><span class="sxs-lookup"><span data-stu-id="647b5-147">Method-Based Query Syntax Examples: Projection</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [<span data-ttu-id="647b5-148">Przykłady składni zapytania oparte na metodzie: filtrowania</span><span class="sxs-lookup"><span data-stu-id="647b5-148">Method-Based Query Syntax Examples: Filtering</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [<span data-ttu-id="647b5-149">Przykłady składni zapytania oparte na metodzie: porządkowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-149">Method-Based Query Syntax Examples: Ordering</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [<span data-ttu-id="647b5-150">Przykłady składni zapytania oparte na metodzie: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="647b5-150">Method-Based Query Syntax Examples: Aggregate Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [<span data-ttu-id="647b5-151">Przykłady składni zapytania oparte na metodzie: partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-151">Method-Based Query Syntax Examples: Partitioning</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [<span data-ttu-id="647b5-152">Przykłady składni zapytania oparte na metodzie: konwersja</span><span class="sxs-lookup"><span data-stu-id="647b5-152">Method-Based Query Syntax Examples: Conversion</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [<span data-ttu-id="647b5-153">Przykłady składni zapytania oparte na metodzie: Operatorów sprzężenia</span><span class="sxs-lookup"><span data-stu-id="647b5-153">Method-Based Query Syntax Examples: Join Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [<span data-ttu-id="647b5-154">Przykłady składni zapytania oparte na metodzie: Operatory Element</span><span class="sxs-lookup"><span data-stu-id="647b5-154">Method-Based Query Syntax Examples: Element Operators</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [<span data-ttu-id="647b5-155">Przykłady składni zapytania oparte na metodzie: grupowanie</span><span class="sxs-lookup"><span data-stu-id="647b5-155">Method-Based Query Syntax Examples: Grouping</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [<span data-ttu-id="647b5-156">Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="647b5-156">Method-Based Query Syntax Examples: Navigating Relationships</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a><span data-ttu-id="647b5-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="647b5-157">See Also</span></span>  
 [<span data-ttu-id="647b5-158">LINQ do jednostek</span><span class="sxs-lookup"><span data-stu-id="647b5-158">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [<span data-ttu-id="647b5-159">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="647b5-159">Getting Started with LINQ in C#</span></span>](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="647b5-160">Wprowadzenie do korzystania z LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="647b5-160">Getting Started with LINQ in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="647b5-161">Opcje scalania Entity Framework i skompilowane zapytania</span><span class="sxs-lookup"><span data-stu-id="647b5-161">Entity Framework Merge Options and Compiled Queries</span></span>](http://go.microsoft.com/fwlink/?LinkId=199591)