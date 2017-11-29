---
title: LINQ do XML Annotations2
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ca84af7cd750529eadb9d0967f4d5570b7038a07
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="f51fc-102">LINQ do XML adnotacji</span><span class="sxs-lookup"><span data-stu-id="f51fc-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="f51fc-103">Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można skojarzyć dowolnych obiektów dowolnego typu dowolnego z dowolnym składnikiem XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="f51fc-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="f51fc-104">Dodawanie adnotacji do elementu XML, takich jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f51fc-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="f51fc-105">Możesz pobrać adnotacje według typu.</span><span class="sxs-lookup"><span data-stu-id="f51fc-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="f51fc-106">Należy pamiętać, że adnotacje nie są częścią XML typu infoset sprawdzonych; nie jest serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="f51fc-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f51fc-107">Metody</span><span class="sxs-lookup"><span data-stu-id="f51fc-107">Methods</span></span>  
 <span data-ttu-id="f51fc-108">Podczas pracy z adnotacjami, można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="f51fc-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="f51fc-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="f51fc-109">Method</span></span>|<span data-ttu-id="f51fc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f51fc-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="f51fc-111">Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f51fc-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="f51fc-112">Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f51fc-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="f51fc-113">Pobiera kolekcję adnotacje dla określonego typu <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f51fc-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="f51fc-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="f51fc-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f51fc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f51fc-115">See Also</span></span>  
 [<span data-ttu-id="f51fc-116">Zaawansowane LINQ do XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f51fc-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)