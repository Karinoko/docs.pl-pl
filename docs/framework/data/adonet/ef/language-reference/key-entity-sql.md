---
title: KLUCZ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: c35cac018392aa9688866e280ff64fdf6a1453f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760560"
---
# <a name="key-entity-sql"></a>KLUCZ (jednostka SQL)
Wyodrębnia klucza referencyjnego lub wyrażenie jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 Klucz jednostki zawiera wartości klucza w odpowiedniej kolejności określonej jednostki lub odwołania do jednostki. Ponieważ wiele zestawów jednostek może opierać się na ten sam typ, ten sam klucz może wyglądać w każdym zestawu jednostek. Aby odwołać unikatowy, należy użyć `REF`. Typ zwracany operatora klucza jest typ wiersza, który zawiera jedno pole dla każdego klucza jednostki, w tej samej kolejności.  
  
 W poniższym przykładzie operator klucza jest przekazywany odwołanie do jednostki BadOrder i zwraca część klucza tego odwołania. W takim przypadku rekord wpisz dokładnie jedno pole odpowiadającego `Id` właściwości.  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora klucza można wyodrębnić klucza część wyrażenia z odwołania do typu. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
