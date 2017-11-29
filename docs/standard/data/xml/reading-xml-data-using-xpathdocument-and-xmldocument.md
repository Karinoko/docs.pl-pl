---
title: "Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 607d9d3616db0d0bd431fa2ca0b6aee03a85f896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="d99da-102">Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d99da-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="d99da-103">Istnieją dwa sposoby przeczytaj dokument XML w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d99da-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d99da-104">Jeden jest przeznaczony do odczytu dokumentu XML przy użyciu tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, a druga jest do odczytu dokumentu XML przy użyciu edytowalne <xref:System.Xml.XmlDocument> klasy w <xref:System.Xml?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d99da-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="d99da-105">Odczytywanie dokumentów XML za pomocą klasy XPathDocument</span><span class="sxs-lookup"><span data-stu-id="d99da-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="d99da-106"><xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML za pomocą wyrażenia XPath modelu danych, szybka i tylko do odczytu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d99da-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="d99da-107">Wystąpienia <xref:System.Xml.XPath.XPathDocument> klasy są tworzone przy użyciu jednej z jego sześciu konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d99da-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="d99da-108">Konstruktory te umożliwiają odczytać dokument XML przy użyciu <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżka do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="d99da-109">Poniższy przykład przedstawia przy użyciu <xref:System.Xml.XPath.XPathDocument> klasy `string` konstruktora, aby odczytać dokument XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="d99da-110">Odczytywanie dokumentów XML za pomocą klasy XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d99da-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="d99da-111"><xref:System.Xml.XmlDocument> Klasa jest edytowalny reprezentacji w pamięci dokumentu XML wykonania W3C modelu DOM (Document Object) poziom 1 Core i Core DOM poziom 2.</span><span class="sxs-lookup"><span data-stu-id="d99da-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="d99da-112">Wystąpienia <xref:System.Xml.XmlDocument> klasy są tworzone przy użyciu jednej z jego trzy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d99da-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="d99da-113">Możesz utworzyć nowy, pusty <xref:System.Xml.XmlDocument> obiektu przez wywołanie metody <xref:System.Xml.XmlDocument> klasy konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="d99da-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="d99da-114">Po wywołaniu metody konstruktora, użyj <xref:System.Xml.XmlDocument.Load%2A> metody do ładowania danych XML do nowej <xref:System.Xml.XmlDocument> obiekt z <xref:System.IO.Stream>, <xref:System.IO.TextReader>, lub <xref:System.Xml.XmlReader> obiektu, jak również `string` ścieżka do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="d99da-115">Poniższy przykład przedstawia przy użyciu <xref:System.Xml.XmlDocument> klasy konstruktor bez parametrów i <xref:System.Xml.XmlDocument.Load%2A> metody do odczytu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="d99da-116">Określanie kodowania dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="d99da-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="d99da-117"><xref:System.Xml.XmlReader> Obiekt może służyć do odczytu dokumentu XML i utworzyć <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> obiektów, jak pokazano w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d99da-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="d99da-118">Jednak <xref:System.Xml.XmlReader> obiektu może odczytać dane, które nie jest zaszyfrowana i w związku z tym nie zapewnia żadnych informacji kodowania.</span><span class="sxs-lookup"><span data-stu-id="d99da-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="d99da-119"><xref:System.Xml.XmlTextReader> Klasa dziedziczy <xref:System.Xml.XmlReader> klasy, oferuje kodowania informacji za pomocą jego <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości i może służyć do tworzenia <xref:System.Xml.XPath.XPathDocument> obiektu lub <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d99da-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="d99da-120">Aby uzyskać więcej informacji na temat kodowania informacji dostarczonych przez <xref:System.Xml.XmlTextReader> , zobacz <xref:System.Xml.XmlTextReader.Encoding%2A> właściwości w <xref:System.Xml.XmlTextReader> klasy dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="d99da-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="d99da-121">Tworzenie obiektów parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d99da-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="d99da-122">Po przeczytaniu dokument XML do albo <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu, można utworzyć <xref:System.Xml.XPath.XPathNavigator> obiektu, wybierz ocenę, przejdź i w niektórych przypadkach edytowanie danych XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="d99da-123">Zarówno <xref:System.Xml.XPath.XPathDocument> i <xref:System.Xml.XmlDocument> klasy dodatkowo do <xref:System.Xml.XmlNode> klasy, implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d99da-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d99da-124">W związku z tym podać wszystkie trzy klasy <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> metodę zwracającą <xref:System.Xml.XPath.XPathNavigator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d99da-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="d99da-125">Edytowanie dokumentów XML za pomocą klasy parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d99da-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="d99da-126">Oprócz zaznaczenie, oceny i nawigowanie po danych XML <xref:System.Xml.XPath.XPathNavigator> klasa może być używana do edycji dokumentu XML w niektórych przypadkach oparte na obiekcie, który go utworzył.</span><span class="sxs-lookup"><span data-stu-id="d99da-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="d99da-127"><xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu podczas <xref:System.Xml.XmlDocument> klasy jest edytowalny, a w rezultacie <xref:System.Xml.XPath.XPathNavigator> obiekty utworzone na podstawie <xref:System.Xml.XPath.XPathDocument> obiektu nie można edytować dokument XML, a te utworzone na podstawie <xref:System.Xml.XmlDocument> obiekt.</span><span class="sxs-lookup"><span data-stu-id="d99da-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="d99da-128"><xref:System.Xml.XPath.XPathDocument> Klasy powinny być używane do dokumentu XML są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d99da-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="d99da-129">W przypadkach, w których należy edytować dokument XML lub wymagają dostępu do dodatkowe funkcje udostępniane przez <xref:System.Xml.XmlDocument> klasy, takie jak obsługa zdarzeń <xref:System.Xml.XmlDocument> klasa powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d99da-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="d99da-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> klasy określa, czy <xref:System.Xml.XPath.XPathNavigator> obiektu mogą edytować dane XML.</span><span class="sxs-lookup"><span data-stu-id="d99da-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="d99da-131">W poniższej tabeli opisano wartość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwości dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="d99da-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="d99da-132"><xref:System.Xml.XPath.IXPathNavigable>Implementacja</span><span class="sxs-lookup"><span data-stu-id="d99da-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="d99da-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A>Wartość</span><span class="sxs-lookup"><span data-stu-id="d99da-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="d99da-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d99da-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="d99da-135">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="d99da-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="d99da-136">Uzyskiwanie dostępu do danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d99da-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="d99da-137">Edytowanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d99da-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="d99da-138">Weryfikacja schematu za pomocą parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d99da-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)