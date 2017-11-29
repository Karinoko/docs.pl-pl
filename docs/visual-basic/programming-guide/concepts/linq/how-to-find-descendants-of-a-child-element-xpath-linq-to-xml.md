---
title: "Porady: znajdowanie elementów podrzędnych elementu podrzędnego (XPath-LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e315735dc3d8e224fa620ab7b314ca8da886419
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="c5378-102">Porady: znajdowanie elementów podrzędnych elementu podrzędnego (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5378-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c5378-103">W tym temacie pokazano, jak można uzyskać elementów podrzędnych elementu podrzędnego o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c5378-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="c5378-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="c5378-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="c5378-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5378-105">Example</span></span>  
 <span data-ttu-id="c5378-106">W tym przykładzie symuluje problemów wyodrębnianie tekstu z reprezentację XML dokumentu tekstów.</span><span class="sxs-lookup"><span data-stu-id="c5378-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="c5378-107">Wybiera pierwszy wszystkie `Paragraph` elementy, a następnie wybranie wszystkich `Text` elementów podrzędnych każdego `Paragraph` elementu.</span><span class="sxs-lookup"><span data-stu-id="c5378-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="c5378-108">To nie wybierz obiekt podrzędny `Text` elementy `Comment` elementu.</span><span class="sxs-lookup"><span data-stu-id="c5378-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Paragraph>  
            <Text>This is the start of</Text>  
        </Paragraph>  
        <Comment>  
            <Text>This comment is not part of the paragraph text.</Text>  
        </Comment>  
        <Paragraph>  
            <Annotation Emphasis='true'>  
                <Text> a sentence.</Text>  
            </Annotation>  
        </Paragraph>  
        <Paragraph>  
            <Text>  This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 <span data-ttu-id="c5378-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c5378-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5378-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5378-110">See Also</span></span>  
 [<span data-ttu-id="c5378-111">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5378-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)