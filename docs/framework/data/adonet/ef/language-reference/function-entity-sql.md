---
title: — Funkcja (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: 1c02583400f9092dcb5008239bfd1fd73c63c326
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485550"
---
# <a name="function-entity-sql"></a>— Funkcja (jednostka SQL)
Definiuje funkcję w zakresie polecenia zapytań jednostki SQL.  
  
## <a name="syntax"></a>Składnia  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Argumenty  
 `function-name`  
 Nazwa funkcji.  
  
 `parameter-name`  
 Nazwa parametru w funkcji.  
  
 `function_expression`  
 Prawidłowe wyrażenie SQL jednostki, które jest funkcją. Polecenia w funkcji może działać na `parameter_name` parametry przekazywane do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 KOLEKCJA (< type_definition`>` )  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wiersze lub odwołania.  
  
 REF **(**`data_type`**)**  
 Wyrażenie, które zwraca odwołanie do typu jednostki.  
  
 WIERSZ **(**`row_expression`**)**  
 Wyrażenie, które zwraca anonimowe, wpisanych strukturalnie rekordy z co najmniej jedną wartość. Aby uzyskać więcej informacji, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji o tej samej nazwie może być zadeklarowana w tekście, tak długo, jak sygnatury funkcji są różne. Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Funkcja śródwierszowa może zostać wywołany w polecenia SQL jednostki, tylko wtedy, gdy zdefiniowano już tego polecenia. Jednak wbudowanej funkcji można wywołać wewnątrz innego funkcja śródwierszowa, przed lub po zdefiniowaniu wywołanej funkcji. W poniższym przykładzie funkcja A wywołuje funkcję B, zanim funkcja B jest zdefiniowana:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Aby uzyskać więcej informacji, zobacz [porady: wywoływanie funkcji User-defined](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 Funkcje mogą być także zadeklarowane w samym modelu. Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane wbudowanego w poleceniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `Products` , przyjmuje wartość całkowitą do filtrowania produktów zwrócone.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `StringReturnsCollection` przyjmującej Kolekcja ciągów do filtrowania zwrócone kontaktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jednostki języka SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
