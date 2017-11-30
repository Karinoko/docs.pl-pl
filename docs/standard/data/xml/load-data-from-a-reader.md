---
title: "Ładowanie danych z czytnika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b899ae870fe92b31d7f4fcd088531f63694bd233
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="load-data-from-a-reader"></a><span data-ttu-id="44301-102">Ładowanie danych z czytnika</span><span class="sxs-lookup"><span data-stu-id="44301-102">Load Data from a Reader</span></span>
<span data-ttu-id="44301-103">Jeśli dokument XML został załadowany przy użyciu <xref:System.Xml.XmlDocument.Load%2A> — metoda i parametr <xref:System.Xml.XmlReader>, istnieją różnice w zachowaniu, który występuje w porównaniu do zachowania podczas ładowania danych z innych formatów.</span><span class="sxs-lookup"><span data-stu-id="44301-103">If an XML document is loaded using the <xref:System.Xml.XmlDocument.Load%2A> method and a parameter of an <xref:System.Xml.XmlReader>, there are differences in the behavior that occurs when compared to the behavior of loading data from the other formats.</span></span> <span data-ttu-id="44301-104">Jeśli czytnik jest w stanie początkowym <xref:System.Xml.XmlDocument.Load%2A> zużywa całą zawartość z czytnika i tworzy XML modelu DOM (Document Object) z wszystkich danych w czytniku.</span><span class="sxs-lookup"><span data-stu-id="44301-104">If the reader is in its initial state, <xref:System.Xml.XmlDocument.Load%2A> consumes the entire contents from the reader and builds the XML Document Object Model (DOM) from all the data in the reader.</span></span>  
  
 <span data-ttu-id="44301-105">Jeśli czytnik znajduje się już w węźle gdzieś w dokumencie i czytnik są następnie przekazywane do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> podejmuje próbę odczytania bieżącego węzła i wszystkich jego elementów równorzędnych, do tagu końcowego, który zamyka bieżący głębokość do pamięci.</span><span class="sxs-lookup"><span data-stu-id="44301-105">If the reader is already positioned on a node somewhere in the document, and the reader is then passed to the <xref:System.Xml.XmlDocument.Load%2A> method, <xref:System.Xml.XmlDocument.Load%2A> attempts to read the current node and all of its siblings, up to the end tag that closes the current depth into memory.</span></span> <span data-ttu-id="44301-106">Powodzenie próba <xref:System.Xml.XmlDocument.Load%2A> zależą od węzła, który czytnik znajduje się w próba obciążenia jako <xref:System.Xml.XmlDocument.Load%2A> weryfikuje, czy poprawnie sformułowany plik XML z czytnika.</span><span class="sxs-lookup"><span data-stu-id="44301-106">The success of the attempted <xref:System.Xml.XmlDocument.Load%2A> depends on the node that the reader is on when the load is attempted, as <xref:System.Xml.XmlDocument.Load%2A> verifies that the XML from the reader is well-formed.</span></span> <span data-ttu-id="44301-107">Jeśli nie jest poprawnie sformułowany plik XML <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="44301-107">If the XML is not well-formed, the <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span> <span data-ttu-id="44301-108">Na przykład następujący zestaw węzłów zawiera dwa elementy poziomu głównego, nie jest poprawnie sformułowany plik XML i <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="44301-108">For example, the following set of nodes contain two root-level elements, the XML is not well-formed, and <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span>  
  
-   <span data-ttu-id="44301-109">Węzłem komentarza, a następnie węzeł elementu, a następnie węzeł elementu, a następnie węzeł EndElement.</span><span class="sxs-lookup"><span data-stu-id="44301-109">Comment node, followed by an Element node, followed by an Element node, followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="44301-110">Następujący zestaw węzłów tworzy DOM niekompletne, ponieważ nie istnieje żaden element głównego poziomu.</span><span class="sxs-lookup"><span data-stu-id="44301-110">The following set of nodes creates an incomplete DOM, because there is no root-level element.</span></span>  
  
-   <span data-ttu-id="44301-111">Następuje węzła ProcessingInstruction następuje węzłem komentarza, następuje węzła EndElement węzłem komentarza.</span><span class="sxs-lookup"><span data-stu-id="44301-111">Comment node followed by a ProcessingInstruction node followed by a Comment node followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="44301-112">Nie zgłasza wyjątek, a dane zostaną załadowane.</span><span class="sxs-lookup"><span data-stu-id="44301-112">This does not throw an exception, and the data is loaded.</span></span> <span data-ttu-id="44301-113">Możesz dodać element główny na początku te węzły i utworzyć poprawnie sformułowany plik XML, który może zostać zapisany bez błędów.</span><span class="sxs-lookup"><span data-stu-id="44301-113">You can add a root element to the top of these nodes and create well-formed XML that can be saved without error.</span></span>  
  
 <span data-ttu-id="44301-114">Jeśli czytnik jest ustawiony na węzeł liścia, który jest nieprawidłowy dla poziomu głównego dokumentu (na przykład białe miejsca lub atrybut węzłem), czytnik będzie kontynuowane do odczytu, dopóki nie zostanie on ustawiony na węźle, który może służyć do katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="44301-114">If the reader is positioned on a leaf node that is invalid for the root level of a document (for example, a white space or attribute node), the reader continues to read until it is positioned on a node that can be used for the root.</span></span> <span data-ttu-id="44301-115">Dokument rozpoczyna się w tym momencie ładowania.</span><span class="sxs-lookup"><span data-stu-id="44301-115">The document begins loading at this point.</span></span>  
  
 <span data-ttu-id="44301-116">Domyślnie <xref:System.Xml.XmlDocument.Load%2A> nie sprawdza, czy kod XML jest nieprawidłowa definicja typu dokumentu (DTD) lub Sprawdzanie poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="44301-116">By default, <xref:System.Xml.XmlDocument.Load%2A> does not verify whether the XML is valid using document type definition (DTD) or schema validation.</span></span> <span data-ttu-id="44301-117">Tylko sprawdzi, czy kod XML jest poprawnie sformułowany.</span><span class="sxs-lookup"><span data-stu-id="44301-117">It only verifies whether the XML is well-formed.</span></span> <span data-ttu-id="44301-118">Aby sprawdzanie poprawności jest wykonywane, musisz utworzyć <xref:System.Xml.XmlReader> przy użyciu <xref:System.Xml.XmlReaderSettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="44301-118">In order for validation to occur, you need to create an <xref:System.Xml.XmlReader> using the <xref:System.Xml.XmlReaderSettings> class.</span></span> <span data-ttu-id="44301-119"><xref:System.Xml.XmlReader> Klasy można wymusić przy użyciu schematu języka (XSD) definicji DTD lub schemat sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="44301-119">The <xref:System.Xml.XmlReader> class can enforce validation using a DTD or Schema definition language (XSD) schema.</span></span> <span data-ttu-id="44301-120"><xref:System.Xml.ValidationType> Właściwość <xref:System.Xml.XmlReaderSettings> klasa określa, czy <xref:System.Xml.XmlReader> wystąpienia wymusza sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="44301-120">The <xref:System.Xml.ValidationType> property on the <xref:System.Xml.XmlReaderSettings> class determines whether the <xref:System.Xml.XmlReader> instance enforces validation.</span></span> <span data-ttu-id="44301-121">Aby uzyskać więcej informacji o weryfikacji danych XML, zobacz sekcję uwag <xref:System.Xml.XmlReader> strony odwołania.</span><span class="sxs-lookup"><span data-stu-id="44301-121">For more information about validating XML data, see the Remarks section of the <xref:System.Xml.XmlReader> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44301-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44301-122">See Also</span></span>  
 [<span data-ttu-id="44301-123">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="44301-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)