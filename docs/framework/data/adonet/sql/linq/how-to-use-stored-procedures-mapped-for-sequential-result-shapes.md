---
title: 'Porady: Użyj procedur składowanych mapowane do wyniku sekwencyjnych kształtów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: ade123f10e1c9ffd6d042b45599cc6e352614e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351943"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Porady: Użyj procedur składowanych mapowane do wyniku sekwencyjnych kształtów
Ten rodzaj procedury składowanej można wygenerować więcej niż jeden kształt wyniku, ale wiesz, w jakiej kolejności są zwracane. Natomiast ten scenariusz ze scenariuszem, jeżeli nie znasz sekwencji danych. Aby uzyskać więcej informacji, zobacz [porady: użycie przechowywanych procedur mapowane do wielu kształtów wynik](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Przykład  
 Oto T-SQL procedury przechowywanej, która zwraca sekwencyjnie wielu kształtów wyników:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Przykład  
 Należy użyć podobny do następującego kodu, aby wykonać tę procedurę składowaną.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury składowane](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
