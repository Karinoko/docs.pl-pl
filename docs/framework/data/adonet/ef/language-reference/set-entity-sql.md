---
title: ZESTAW (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e70db99157e0bc49e1548d18c8fccfa44af42356
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="set-entity-sql"></a><span data-ttu-id="8de4f-102">ZESTAW (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="8de4f-102">SET (Entity SQL)</span></span>
<span data-ttu-id="8de4f-103">Wyrażenie zestawu jest używana do konwertowania kolekcji obiektów do zestawu przez reaguje nowej kolekcji z wszystkie zduplikowane elementy usunięte.</span><span class="sxs-lookup"><span data-stu-id="8de4f-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8de4f-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8de4f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8de4f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8de4f-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="8de4f-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de4f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8de4f-107">Remarks</span></span>  
 <span data-ttu-id="8de4f-108">Wyrażenie zestawu `SET(c)` jest odpowiednikiem logicznie następującą instrukcję select:</span><span class="sxs-lookup"><span data-stu-id="8de4f-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="8de4f-109">`SET`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="8de4f-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="8de4f-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="8de4f-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="8de4f-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="8de4f-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8de4f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8de4f-112">Example</span></span>  
 <span data-ttu-id="8de4f-113">Następujące zapytanie SQL jednostki użyto wyrażenia zestawu do przekonwertowania kolekcji obiektów do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8de4f-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="8de4f-114">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8de4f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8de4f-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="8de4f-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8de4f-116">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8de4f-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="8de4f-117">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="8de4f-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="8de4f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8de4f-118">See Also</span></span>  
 [<span data-ttu-id="8de4f-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="8de4f-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)