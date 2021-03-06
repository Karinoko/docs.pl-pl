---
title: 'Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 777c6e1aa057bd0abe81adc63bed1d947f11b837
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240596"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika (C# Programming Guide)
Do uzyskania dostępu do członka struktury, która jest zadeklarowana w niebezpiecznym kontekście, można używać operatora dostępu do elementu członkowskiego, jak pokazano w poniższym przykładzie, w którym `p` jest wskaźnikiem do [struktury](../../../csharp/language-reference/keywords/struct.md) zawierający element członkowski `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [struktury](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, zawierający dwie współrzędne `x` i `y` jest zadeklarowana i uruchomiony. Za pomocą operatora dostępu do elementu członkowskiego `->` i wskaźnik do wystąpienia `home`, `x` i `y` mają przypisane wartości.  
  
> [!NOTE]
>  Należy zauważyć, że wyrażenie `p->x` jest równoważne wyrażeniu `(*p).x`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
