---
title: Nazwę członka typu anonimowego można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587472"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Nazwę członka typu anonimowego można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
Nie można wywnioskować nazwy członka typu anonimowego z wyrażenie złożone.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Aby uzyskać więcej informacji na temat źródeł, z których można typy anonimowe i nie można wywnioskować nazwy elementów członkowskich i typów, zobacz [porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **Identyfikator błędu:** BC36556  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przypisz wyrażenie na nazwę elementu członkowskiego, jak pokazano w poniższym kodzie:  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
