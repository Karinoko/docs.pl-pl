---
title: Namespace lub typ określony w elemencie Imports poziom projektu &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawierają żadnego członka publicznego lub nie można odnaleźć
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: d6d0c931262d892ec3e65888a76f25218b23d868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595816"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace lub typ określony w elemencie Imports poziom projektu &#39; &lt;qualifiedelementname&gt; &#39; &#39;t zawierają żadnego członka publicznego lub nie można odnaleźć
Namespace lub typ określony w elemencie Imports poziom projektu\<qualifiedelementname >' nie zawierają żadnego członka publicznego lub nie można odnaleźć. Upewnij się, że przestrzeń nazw lub typ są zdefiniowane i zawierają co najmniej jednego członka publicznego. Upewnij się, że nazwa aliasu nie zawiera innych aliasów.  
  
 Właściwość importu projektu określa zawierający element, który nie może być odnaleziona albo nie definiuje `Public` elementów członkowskich.  
  
 A *zawierającego element* może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu lub wyliczenia. Element zawierający zawiera członków, takie jak zmienne, procedury i innych elementów zawierających.  
  
 Importowanie celem jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez konieczności ich kwalifikacji. Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Jeśli kompilator nie może znaleźć określonego elementu zawierającego, nie można go rozpoznać odwołań, które go używają. Jeśli znajdzie elementu, ale element nie ujawnia żadnego `Public` elementy członkowskie, a następnie odwołania nie mogą być skutecznie. W obu przypadkach jest bez znaczenia, aby zaimportować element.  
  
 Możesz użyć **projektanta projektu** do określania elementów do importowania. Użyj **importowane przestrzenie nazw** sekcji **odwołania** strony. Aby uzyskać **projektanta projektu** przez dwukrotne kliknięcie **mój projekt** ikonę w **Eksploratora rozwiązań**.  
  
 **Identyfikator błędu:** BC40057  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Otwórz **projektanta projektu** i przejdź do **odwołania** strony.  
  
2.  W **importowane przestrzenie nazw** upewnij się, że zawierającego element jest dostępny z projektu.  
  
3.  Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
