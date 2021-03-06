---
title: '&lt;Lista&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 98c3b8bd809ac550468a5d80e01e6fd16e6d96ea
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924937"
---
# <a name="ltlistgt-visual-basic"></a>&lt;Lista&gt; (Visual Basic)
Definiuje listy lub tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ listy. Musi być "bullet" na liście punktowanej we wcześniejszej, "number", dla listy numerowanej lub "table" dla tabeli dwie kolumny.  
  
 `term`  
 Używana tylko w przypadku `type` jest "table". Termin, aby zdefiniować, która jest zdefiniowana w tagu opis.  
  
 `description`  
 Gdy `type` "bullet" lub "number" `description` element na liście po `type` jest "tabeli" `description` jest definicja `term`.  
  
## <a name="remarks"></a>Uwagi  
 `<listheader>` Bloku określa nagłówek tabeli lub definicji listy. Podczas definiowania tabeli, wystarczy podać wpis dla `term` w nagłówku.  
  
 Każdy element na liście jest określony za pomocą `<item>` bloku. Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`. Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.  
  
 Masz tyle listy lub tabeli `<item>` blokuje zgodnie z potrzebami.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<list>` tag, aby zdefiniować listy punktowanej w sekcji uwag.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)
