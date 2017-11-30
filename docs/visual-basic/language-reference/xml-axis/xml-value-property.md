---
title: "Właściwość wartości XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c52ac09e209d6e3f0cfd877a071cbbe3ab96f18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="bd06c-102">Właściwość wartości XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd06c-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="bd06c-103">Zapewnia dostęp do wartości pierwszego elementu w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd06c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd06c-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="bd06c-105">Części</span><span class="sxs-lookup"><span data-stu-id="bd06c-105">Parts</span></span>  
  
|<span data-ttu-id="bd06c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="bd06c-106">Term</span></span>|<span data-ttu-id="bd06c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="bd06c-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="bd06c-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="bd06c-108">Required.</span></span> <span data-ttu-id="bd06c-109">Kolekcja <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="bd06c-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd06c-110">Return Value</span></span>  
 <span data-ttu-id="bd06c-111">A `String` zawierający wartość pierwszego elementu w kolekcji, lub `Nothing` Jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="bd06c-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd06c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd06c-112">Remarks</span></span>  
 <span data-ttu-id="bd06c-113"><xref:System.Xml.Linq.XElement.Value%2A> Właściwości można łatwo uzyskać dostęp do wartości pierwszego elementu w kolekcji z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bd06c-114">Ta właściwość najpierw sprawdza, czy kolekcja zawiera co najmniej jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="bd06c-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="bd06c-115">Jeśli kolekcja jest pusta, ta właściwość zwraca `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bd06c-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="bd06c-116">W przeciwnym razie ta właściwość zwraca wartość <xref:System.Xml.Linq.XElement.Value%2A> właściwości pierwszego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bd06c-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd06c-117">Jeśli dostęp do wartości atrybutu XML za pomocą "@" identyfikator, wartość atrybutu jest zwracana jako `String` i nie trzeba jawnie określać <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bd06c-117">When you access the value of an XML attribute using the '@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="bd06c-118">Aby uzyskać dostęp do innych elementów w kolekcji, służy właściwość indeksatora rozszerzenia XML.</span><span class="sxs-lookup"><span data-stu-id="bd06c-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="bd06c-119">Aby uzyskać więcej informacji, zobacz [właściwość indeksatora rozszerzenia](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="bd06c-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="bd06c-120">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="bd06c-120">Inheritance</span></span>  
 <span data-ttu-id="bd06c-121">Większość użytkowników nie będzie konieczne wdrożenie <xref:System.Collections.Generic.IEnumerable%601>i w związku z tym można zignorować w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bd06c-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="bd06c-122"><xref:System.Xml.Linq.XElement.Value%2A> Właściwość jest właściwością rozszerzenia dla typów implementujących `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="bd06c-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="bd06c-123">Powiązanie tej właściwości rozszerzenia przypomina powiązania metody rozszerzenia: Jeśli typ implementuje jednego z interfejsów i definiuje właściwość o nazwie "Wartość", że właściwość ma pierwszeństwo przed właściwość rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="bd06c-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="bd06c-124">Innymi słowy, to <xref:System.Xml.Linq.XElement.Value%2A> właściwość może zostać przesłonięta przez definiowanie nowych właściwości klasy, która implementuje `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="bd06c-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd06c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd06c-125">Example</span></span>  
 <span data-ttu-id="bd06c-126">Poniższy przykład przedstawia użycie <xref:System.Xml.Linq.XElement.Value%2A> właściwości dostępu do pierwszego węzła w kolekcji <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bd06c-127">W przykładzie użyto właściwości osi elementu podrzędnego można pobrać kolekcji wszystkie węzły podrzędne o nazwie `phone` w `contact` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bd06c-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="bd06c-128">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="bd06c-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="bd06c-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd06c-129">Example</span></span>  
 <span data-ttu-id="bd06c-130">Poniższy przykład pokazuje, jak można pobrać wartości atrybutu XML z kolekcją <xref:System.Xml.Linq.XAttribute> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="bd06c-131">W przykładzie użyto właściwości osi atrybutu, aby wyświetlić wartość `type` atrybutu dla wszystkich `phone` elementów.</span><span class="sxs-lookup"><span data-stu-id="bd06c-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="bd06c-132">Ten kod zawiera następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="bd06c-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="bd06c-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd06c-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="bd06c-134">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="bd06c-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="bd06c-135">Literały XML</span><span class="sxs-lookup"><span data-stu-id="bd06c-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="bd06c-136">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd06c-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="bd06c-137">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="bd06c-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="bd06c-138">Właściwość indeksatora rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="bd06c-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="bd06c-139">Właściwość osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="bd06c-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="bd06c-140">Właściwości osi atrybutu XML</span><span class="sxs-lookup"><span data-stu-id="bd06c-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)