---
title: "Przykłady składni zapytania oparte na metodzie: porządkowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de1b610bbc0462c4712c4dec397757ab5c3c9dc1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="2fe48-102">Przykłady składni zapytania oparte na metodzie: porządkowanie</span><span class="sxs-lookup"><span data-stu-id="2fe48-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="2fe48-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.ThenBy%2A> metody query [AdventureWorks sprzedaży modelu](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="2fe48-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="2fe48-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2fe48-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2fe48-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="2fe48-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="2fe48-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="2fe48-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2fe48-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fe48-107">Example</span></span>  
 <span data-ttu-id="2fe48-108">W poniższym przykładzie w składni zapytania oparte na metodzie <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenBy%2A> aby powrócić do listy kontaktów uporządkowanych według nazwisko, a następnie według imienia.</span><span class="sxs-lookup"><span data-stu-id="2fe48-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="2fe48-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="2fe48-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="2fe48-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2fe48-110">Example</span></span>  
 <span data-ttu-id="2fe48-111">W poniższym przykładzie użyto <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenByDescending%2A> metody pierwszy sortować cennika, a następnie wykonaj, malejąco sortowania nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="2fe48-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2fe48-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fe48-112">See Also</span></span>  
 [<span data-ttu-id="2fe48-113">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2fe48-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)