---
title: 'Porady: znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 5d62418fe6d89c8dc5c7ddb4975404f1a7e0aa2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517096"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Porady: znajdowanie elementów podrzędnych na podstawie położenia (XPath-LINQ to XML) (C#)
Czasami trzeba znajdowanie elementów na podstawie ich pozycji. Możesz chcieć znaleźć drugiego elementu, lub możesz chcieć znaleźć trzeci za pośrednictwem piąty element.  
  
 Wyrażenie XPath jest:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Istnieją dwa podejścia do pisania to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania w taki sposób, z opóźnieniem. Możesz użyć <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> operatorów, lub użyć <xref:System.Linq.Enumerable.Where%2A> przeciążenia przyjmującego indeksu. Kiedy używasz <xref:System.Linq.Enumerable.Where%2A> przeciążenie, można użyć Wyrażenie lambda, która przyjmuje dwa argumenty. Poniższy kod przedstawia obie metody wybierania, na podstawie położenia.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje drugiego do czwartego `Test` elementu. Wynik jest kolekcją elementów.  
  
 W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to XML dla użytkowników metody XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
