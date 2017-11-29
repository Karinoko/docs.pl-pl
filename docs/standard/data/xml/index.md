---
title: Dokumenty XML i dane
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 38382609fb21069fd69a84eb8b9de4701efeaf2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="d72b5-102">Dokumenty XML i dane</span><span class="sxs-lookup"><span data-stu-id="d72b5-102">XML Documents and Data</span></span>
<span data-ttu-id="d72b5-103">.NET Framework zapewnia kompleksowy, zintegrowany zestaw klas, które umożliwiają łatwe tworzenie aplikacji obsługującym kod XML.</span><span class="sxs-lookup"><span data-stu-id="d72b5-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="d72b5-104">Klasy w następujących przestrzeni nazw obsługuje analizowania i zapisywanie edytowania plików XML, dane XML w pamięci, sprawdzanie poprawności danych i przekształcenie XSLT.</span><span class="sxs-lookup"><span data-stu-id="d72b5-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="d72b5-105">Aby uzyskać pełną listę, zobacz [przestrzenie nazw System.Xml](http://msdn.microsoft.com/library/gg145036.aspx) strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d72b5-105">For a full list, see the [System.Xml Namespaces](http://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="d72b5-106">Klasy w tych obszarach nazw obsługuje zalecenia konsorcjum World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="d72b5-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="d72b5-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d72b5-107">For example:</span></span>  
  
-   <span data-ttu-id="d72b5-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> Klasa implementuje [W3C modelu DOM (Document Object) poziom 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) i [DOM poziom 2 rdzenie](http://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.</span><span class="sxs-lookup"><span data-stu-id="d72b5-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="d72b5-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> i <xref:System.Xml.XmlWriter?displayProperty=nameWithType> klas pomocy technicznej [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) i [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) zalecenia.</span><span class="sxs-lookup"><span data-stu-id="d72b5-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="d72b5-110">Schematów w <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> klas pomocy technicznej [W3C XML schematu część 1: struktury](http://www.w3.org/TR/xmlschema-1/) i [XML schematu część 2: typy danych](http://www.w3.org/TR/xmlschema-2/) zalecenia.</span><span class="sxs-lookup"><span data-stu-id="d72b5-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="d72b5-111">Klasy w <xref:System.Xml.Xsl?displayProperty=nameWithType> przekształcenia XSLT pomocy technicznej przestrzeni nazw, które są zgodne z [W3C XSLT 1.0](http://www.w3.org/TR/xslt) zalecenia.</span><span class="sxs-lookup"><span data-stu-id="d72b5-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="d72b5-112">Klasy XML w programie .NET Framework zapewniają następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="d72b5-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="d72b5-113">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="d72b5-113">**Productivity.**</span></span> <span data-ttu-id="d72b5-114">[LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) ułatwia program za pomocą XML i zapewnia obsługę zapytania podobne do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="d72b5-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="d72b5-115">**Rozszerzalność.**</span><span class="sxs-lookup"><span data-stu-id="d72b5-115">**Extensibility.**</span></span> <span data-ttu-id="d72b5-116">Klasy XML w programie .NET Framework są rozszerzalne abstrakcyjnych klas podstawowych i metodach wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="d72b5-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="d72b5-117">Na przykład można utworzyć klasy pochodnej z <xref:System.Xml.XmlUrlResolver> klasy, która przechowuje strumienia pamięci podręcznej na dysk lokalny.</span><span class="sxs-lookup"><span data-stu-id="d72b5-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="d72b5-118">**Architektura obsługująca dodatki.**</span><span class="sxs-lookup"><span data-stu-id="d72b5-118">**Pluggable architecture.**</span></span> <span data-ttu-id="d72b5-119">.NET Framework zapewnia architekturę, w którym składniki mogą korzystać z sobą i danych mogą być przesyłane strumieniowo między składnikami.</span><span class="sxs-lookup"><span data-stu-id="d72b5-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="d72b5-120">Na przykład magazyn danych, takich jak <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektów, można je przekształcać z <xref:System.Xml.Xsl.XslCompiledTransform> klasy i dane wyjściowe następnie mogą być przesyłane strumieniowo albo do innego magazynu lub zwrócony jako strumienia z usługą sieci web.</span><span class="sxs-lookup"><span data-stu-id="d72b5-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="d72b5-121">**Wydajność.**</span><span class="sxs-lookup"><span data-stu-id="d72b5-121">**Performance.**</span></span> <span data-ttu-id="d72b5-122">W celu poprawy wydajności aplikacji niektóre klasy XML w programie .NET Framework obsługuje model na podstawie przesyłania strumieniowego o następującej charakterystyce:</span><span class="sxs-lookup"><span data-stu-id="d72b5-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="d72b5-123">Minimalny buforowanie tylko do przodu, model ściągania analizy (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="d72b5-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="d72b5-124">Sprawdzanie poprawności tylko do przodu (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="d72b5-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="d72b5-125">Kursor styl nawigacji, który minimalizuje tworzenia węzła do jednego wirtualnego węzła zapewniając dostępie do dokumentu (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="d72b5-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="d72b5-126">W celu poprawy wydajności przy każdym przetwarzania XSLT jest wymagany, korzystając z <xref:System.Xml.XPath.XPathDocument> klasy, która jest zoptymalizowana, jako tylko do odczytu magazynu dla zapytania XPath umożliwia wydajną pracę z <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d72b5-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="d72b5-127">**Integracja z ADO.NET.**</span><span class="sxs-lookup"><span data-stu-id="d72b5-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="d72b5-128">Klasy XML i [ADO.NET](../../../../docs/framework/data/adonet/index.md) są ściśle powiązane ze sobą danych relacyjnych i XML.</span><span class="sxs-lookup"><span data-stu-id="d72b5-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="d72b5-129"><xref:System.Data.DataSet> Klasa znajduje się w pamięci podręcznej dane pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d72b5-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="d72b5-130"><xref:System.Data.DataSet> Klasa ma możliwość odczytywania i zapisywania XML przy użyciu <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> klasy, aby utrwalić jego struktury wewnętrznej schemat relacyjny jako schematów XML (XSD) i na potrzeby wnioskowania dotyczącego schematu strukturę dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d72b5-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d72b5-131">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d72b5-131">In This Section</span></span>  
 [<span data-ttu-id="d72b5-132">Opcje przetwarzania XML</span><span class="sxs-lookup"><span data-stu-id="d72b5-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="d72b5-133">W tym artykule omówiono opcje przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="d72b5-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="d72b5-134">Przetwarzanie danych XML w pamięci</span><span class="sxs-lookup"><span data-stu-id="d72b5-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="d72b5-135">W tym artykule omówiono trzy modele przetwarzania XML danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d72b5-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="d72b5-136">[LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> (oparte na modelu obiektu dokumentu W3C), klasy i <xref:System.Xml.XPath.XPathDocument> klasy (oparte na modelu danych XPath).</span><span class="sxs-lookup"><span data-stu-id="d72b5-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="d72b5-137">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="d72b5-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="d72b5-138">W tym artykule opisano sposób użycia procesora XSLT.</span><span class="sxs-lookup"><span data-stu-id="d72b5-138">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="d72b5-139">Model obiektu schematu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="d72b5-139">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="d72b5-140">W tym artykule opisano klasy, służące do tworzenia i operowanie nimi schematów XML (XSD), zapewniając <xref:System.Xml.Schema.XmlSchema> klasy obciążenia i Edytuj schematu.</span><span class="sxs-lookup"><span data-stu-id="d72b5-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="d72b5-141">Integracja XML z danych relacyjnych i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d72b5-141">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="d72b5-142">W tym artykule opisano, jak programu .NET Framework udostępnia w czasie rzeczywistym, synchronicznej relacyjnych i hierarchicznych reprezentacje danych za pośrednictwem <xref:System.Data.DataSet> obiektu i <xref:System.Xml.XmlDataDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d72b5-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="d72b5-143">Zarządzanie przestrzeni nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="d72b5-143">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="d72b5-144">Opisuje sposób <xref:System.Xml.XmlNamespaceManager> klasa jest używana do przechowywania i obsługi informacji dotyczących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d72b5-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="d72b5-145">Obsługa typu do zestawów System.Xml klas</span><span class="sxs-lookup"><span data-stu-id="d72b5-145">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="d72b5-146">W tym artykule opisano, jak typy mapowania typów danych XML do środowiska CLR, jak przekonwertować typów danych XML i innymi funkcjami pomocy technicznej typu <xref:System.Xml> klasy.</span><span class="sxs-lookup"><span data-stu-id="d72b5-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d72b5-147">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d72b5-147">Related Sections</span></span>  
 [<span data-ttu-id="d72b5-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d72b5-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="d72b5-149">Zawiera informacje na temat dostępu do danych za pomocą ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d72b5-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="d72b5-150">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d72b5-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="d72b5-151">Omówienie systemu zabezpieczeń .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d72b5-151">Provides an overview of the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="d72b5-152">Centrum deweloperów języka XML</span><span class="sxs-lookup"><span data-stu-id="d72b5-152">XML Developer Center</span></span>](http://go.microsoft.com/fwlink/?linkid=42458)  
 <span data-ttu-id="d72b5-153">Zawiera dodatkowe informacje techniczne, pliki do pobrania, grupy dyskusyjne i inne zasoby dla deweloperów XML.</span><span class="sxs-lookup"><span data-stu-id="d72b5-153">Provides additional technical information, downloads, newsgroups, and other resources for XML developers.</span></span>