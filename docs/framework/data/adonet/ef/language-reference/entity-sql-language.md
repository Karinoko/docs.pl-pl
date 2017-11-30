---
title: "Jednostki języka SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e366e8bbd9df31f367496ca5e106b876921896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-language"></a><span data-ttu-id="73c29-102">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="73c29-102">Entity SQL Language</span></span>
<span data-ttu-id="73c29-103">Jednostka SQL jest język kwerendy niezależne od magazynu, która jest podobna do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="73c29-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="73c29-104">Jednostki SQL umożliwia zapytania danych jednostki, jako obiekty lub w formie tabelarycznej.</span><span class="sxs-lookup"><span data-stu-id="73c29-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="73c29-105">Należy rozważyć użycie SQL jednostki w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="73c29-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="73c29-106">Jeśli zapytanie musi być dynamicznie skonstruowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="73c29-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="73c29-107">W takim przypadku należy również rozważyć za pomocą metody konstruktora zapytań <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="73c29-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="73c29-108">Jeśli chcesz zdefiniować zapytania jako część definicji modelu.</span><span class="sxs-lookup"><span data-stu-id="73c29-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="73c29-109">Tylko jednostki SQL jest obsługiwana w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="73c29-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="73c29-110">Aby uzyskać więcej informacji, zobacz [Element QueryView (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="73c29-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="73c29-111">W przypadku używania EntityClient do zwracanych danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="73c29-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="73c29-112">Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="73c29-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="73c29-113">Jeśli masz już eksperta w językach SQL na podstawie kwerendy, jednostki SQL może wydawać się najbardziej fizyczne do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="73c29-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="73c29-114">Przy użyciu programu SQL jednostki z dostawcą EntityClient</span><span class="sxs-lookup"><span data-stu-id="73c29-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="73c29-115">Jeśli chcesz korzystać z SQL jednostki z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="73c29-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="73c29-116">Dostawca EntityClient Entity Framework</span><span class="sxs-lookup"><span data-stu-id="73c29-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="73c29-117">Porady: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="73c29-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="73c29-118">Porady: wykonywanie zapytań, które zwraca wyniki PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="73c29-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="73c29-119">Porady: wykonywanie zapytań, które zwraca wyniki StructuralType</span><span class="sxs-lookup"><span data-stu-id="73c29-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="73c29-120">Porady: kwerenda zwraca obiekt RefType wyników</span><span class="sxs-lookup"><span data-stu-id="73c29-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="73c29-121">Porady: kwerenda zwraca typów złożonych</span><span class="sxs-lookup"><span data-stu-id="73c29-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="73c29-122">Porady: kwerenda zwraca zagnieżdżonych kolekcji</span><span class="sxs-lookup"><span data-stu-id="73c29-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="73c29-123">Porady: wykonywanie zapytań SQL sparametryzowane jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="73c29-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="73c29-124">Porady: wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="73c29-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="73c29-125">Porady: wykonywanie zapytań polimorficzne</span><span class="sxs-lookup"><span data-stu-id="73c29-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="73c29-126">Porady: nawigowanie po relacjach za pomocą Przejdź — Operator</span><span class="sxs-lookup"><span data-stu-id="73c29-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="73c29-127">Przy użyciu programu SQL jednostka z obiektu zapytań</span><span class="sxs-lookup"><span data-stu-id="73c29-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="73c29-128">Jeśli chcesz użyć SQL jednostek z obiektu zapytań, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="73c29-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="73c29-129">Porady: kwerenda zwraca obiekty typu jednostki</span><span class="sxs-lookup"><span data-stu-id="73c29-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="73c29-130">Porady: wykonanie zapytania parametrycznego</span><span class="sxs-lookup"><span data-stu-id="73c29-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="73c29-131">Porady: nawigowanie po relacjach za pomocą właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="73c29-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="73c29-132">Porady: wywoływanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="73c29-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="73c29-133">Porady: filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="73c29-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="73c29-134">Porady: sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="73c29-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="73c29-135">Porady: grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="73c29-135">How to: Group Data</span></span>](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="73c29-136">Porady: agregowanie danych</span><span class="sxs-lookup"><span data-stu-id="73c29-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="73c29-137">Porady: kwerenda zwraca obiekty typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="73c29-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="73c29-138">Porady: kwerenda zwraca kolekcję typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="73c29-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="73c29-139">Porady: zapytanie powiązane obiekty w obiekcie EntityCollection</span><span class="sxs-lookup"><span data-stu-id="73c29-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="73c29-140">Porady: kolejność złożenie dwóch zapytań</span><span class="sxs-lookup"><span data-stu-id="73c29-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="73c29-141">Porady: powoduje strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="73c29-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="73c29-142">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="73c29-142">In This Section</span></span>  
 [<span data-ttu-id="73c29-143">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="73c29-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="73c29-144">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="73c29-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="73c29-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73c29-145">See Also</span></span>  
 [<span data-ttu-id="73c29-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="73c29-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="73c29-147">Odwołanie językowe</span><span class="sxs-lookup"><span data-stu-id="73c29-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)