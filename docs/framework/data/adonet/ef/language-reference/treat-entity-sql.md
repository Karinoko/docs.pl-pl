---
title: TRAKTUJ (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa7bfd2a9fffdd0cfedced76cf83f9e01630c986
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="treat-entity-sql"></a><span data-ttu-id="40f07-102">TRAKTUJ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="40f07-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="40f07-103">Traktuje obiektu określonego typu podstawowego jako obiekt określonego typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="40f07-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40f07-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="40f07-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="40f07-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="40f07-106">Wszystkie prawidłowe zapytanie zwracające jednostki.</span><span class="sxs-lookup"><span data-stu-id="40f07-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f07-107">Typ określonego wyrażenia musi być podtypem określonego typu danych lub typ danych musi być podtypem typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40f07-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="40f07-108">Typ jednostki.</span><span class="sxs-lookup"><span data-stu-id="40f07-108">An entity type.</span></span> <span data-ttu-id="40f07-109">Typ musi być kwalifikowana przez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="40f07-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f07-110">Określone wyrażenie musi być podtypem określonego typu danych lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40f07-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40f07-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40f07-111">Return Value</span></span>  
 <span data-ttu-id="40f07-112">Wartość określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="40f07-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f07-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40f07-113">Remarks</span></span>  
 <span data-ttu-id="40f07-114">TRAKTUJ służy do wykonywania rzutowanie w górę między powiązanymi klasami.</span><span class="sxs-lookup"><span data-stu-id="40f07-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="40f07-115">Na przykład jeśli `Employee` pochodną `Person` i p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a ogólny `Person` wystąpienie do `Employee`; oznacza to, umożliwia można traktować p `Employee`.</span><span class="sxs-lookup"><span data-stu-id="40f07-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="40f07-116">TRAKTUJ jest używany w scenariuszach dziedziczenia, w którym można wykonać zapytania podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="40f07-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="40f07-117">To zapytanie upcasts `Person` jednostki do `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="40f07-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="40f07-118">Jeśli wartość p nie jest rzeczywiście typu `Employee`, wyrażenie daje w wyniku wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="40f07-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f07-119">Określone wyrażenie `Employee` musi być podtypem typu danych określonego `Person`, lub typ danych musi być podtypem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="40f07-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="40f07-120">W przeciwnym razie wartość wyrażenia spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="40f07-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="40f07-121">W poniższej tabeli przedstawiono zachowania Traktuj przez niektóre typowe wzorce i pewne mniej typowe wzorce.</span><span class="sxs-lookup"><span data-stu-id="40f07-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="40f07-122">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="40f07-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="40f07-123">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="40f07-123">Pattern</span></span>|<span data-ttu-id="40f07-124">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="40f07-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="40f07-125">Zwraca `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="40f07-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="40f07-126">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="40f07-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="40f07-127">Zgłasza wyjątek /</span><span class="sxs-lookup"><span data-stu-id="40f07-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="40f07-128">Zwraca `EntityType` lub `null`.</span><span class="sxs-lookup"><span data-stu-id="40f07-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="40f07-129">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="40f07-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="40f07-130">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="40f07-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40f07-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="40f07-131">Example</span></span>  
 <span data-ttu-id="40f07-132">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="40f07-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="40f07-133">Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="40f07-133">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="40f07-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40f07-134">See Also</span></span>  
 [<span data-ttu-id="40f07-135">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="40f07-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="40f07-136">Typy dopuszczające wartości zerowe strukturalnych</span><span class="sxs-lookup"><span data-stu-id="40f07-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)