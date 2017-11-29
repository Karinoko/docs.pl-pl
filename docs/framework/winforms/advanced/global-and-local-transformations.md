---
title: "Globalne i lokalne przekształcenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 432402fefc6c958fbab0b1450a429d9b130b8239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="2255e-102">Globalne i lokalne przekształcenia</span><span class="sxs-lookup"><span data-stu-id="2255e-102">Global and Local Transformations</span></span>
<span data-ttu-id="2255e-103">Globalne przekształcenie jest transformację, która ma zastosowanie do każdego elementu narysowanymi przez dany <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2255e-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="2255e-104">Z kolei transformację lokalnego jest transformację, która ma zastosowanie do określonego elementu do narysowania.</span><span class="sxs-lookup"><span data-stu-id="2255e-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="2255e-105">Globalne przekształcenia</span><span class="sxs-lookup"><span data-stu-id="2255e-105">Global Transformations</span></span>  
 <span data-ttu-id="2255e-106">Aby utworzyć transformację globalnego, należy utworzyć <xref:System.Drawing.Graphics> obiekt, a następnie wykonywać jego <xref:System.Drawing.Graphics.Transform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2255e-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="2255e-107"><xref:System.Drawing.Graphics.Transform%2A> Jest właściwość <xref:System.Drawing.Drawing2D.Matrix> obiektu, więc może zawierać żadnych sekwencji affine — przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="2255e-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="2255e-108">Transformacja przechowywane w <xref:System.Drawing.Graphics.Transform%2A> właściwości jest wywoływana transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="2255e-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="2255e-109"><xref:System.Drawing.Graphics> Klasa udostępnia kilka metod budowania przekształcenia złożonego world: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, i <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="2255e-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="2255e-110">Poniższy przykład Rysuje elipsę dwa razy: raz w przed utworzeniem transformacja świata i jeden raz po.</span><span class="sxs-lookup"><span data-stu-id="2255e-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="2255e-111">Transformacja skaluje najpierw według współczynnika 0,5 w kierunku y, a następnie wykonuje translację 50 jednostek w kierunku x i obraca się 30 stopni.</span><span class="sxs-lookup"><span data-stu-id="2255e-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="2255e-112">Na poniższej ilustracji przedstawiono objętego przekształcenia macierzy.</span><span class="sxs-lookup"><span data-stu-id="2255e-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="2255e-113">![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="2255e-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2255e-114">W powyższym przykładzie elipsy obraca się wokół pochodzenia współrzędnych, która jest w lewym górnym rogu obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="2255e-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="2255e-115">To daje różne wyniki niż obracanie elipsy temat własnego Centrum.</span><span class="sxs-lookup"><span data-stu-id="2255e-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="2255e-116">Lokalne przekształcenia</span><span class="sxs-lookup"><span data-stu-id="2255e-116">Local Transformations</span></span>  
 <span data-ttu-id="2255e-117">Transformację lokalnego ma zastosowanie do określonego elementu do narysowania.</span><span class="sxs-lookup"><span data-stu-id="2255e-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="2255e-118">Na przykład <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt ma <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> — metoda, która pozwala na Przekształcanie punktów danych tej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2255e-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="2255e-119">Poniższy przykład rysuje prostokąt z nie transformacji i ścieżki z transformację obrotu.</span><span class="sxs-lookup"><span data-stu-id="2255e-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="2255e-120">(Przyjmowane jest nie transformacja świata).</span><span class="sxs-lookup"><span data-stu-id="2255e-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="2255e-121">Transformacja świata przekształceń lokalnego, aby uzyskać różne wyniki można łączyć.</span><span class="sxs-lookup"><span data-stu-id="2255e-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="2255e-122">Na przykład można transformacji świata korygowanie współrzędnych i lokalne przekształcenia umożliwia obracanie i skalowanie obiektów na nowy układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2255e-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="2255e-123">Załóżmy, że ma układ współrzędnych, jego pochodzenie 200 pikseli od lewej krawędzi obszaru klienckiego i 150 pikseli od góry obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="2255e-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="2255e-124">Ponadto wariantem jednostki miary być pikseli, o wskazanie osi y skierowany w górę i prawej osi x.</span><span class="sxs-lookup"><span data-stu-id="2255e-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="2255e-125">Domyślny układ współrzędnych ma osi y skierowany w dół, więc należy przeprowadzić odbicie wzdłuż osi poziomej.</span><span class="sxs-lookup"><span data-stu-id="2255e-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="2255e-126">Na poniższej ilustracji przedstawiono macierzy takie odbicia.</span><span class="sxs-lookup"><span data-stu-id="2255e-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="2255e-127">![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="2255e-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="2255e-128">Następnie przyjęto założenie, że należy przeprowadzić translacji 200 w prawo i 150 jednostek w dół.</span><span class="sxs-lookup"><span data-stu-id="2255e-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="2255e-129">Poniższy przykład ustanawia współrzędnych właśnie opisanego przez ustawienie transformacji świata <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2255e-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="2255e-130">Poniższy kod (umieszczona na końcu powyższego przykładu) tworzy ścieżki, która składa się z jednego prostokąt z jego lewym dolnym rogu źródłem nowy układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2255e-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="2255e-131">Prostokąt jest wypełniana raz nie transformację lokalnych i drugi raz z transformację lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2255e-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="2255e-132">Transformacja lokalnego składa się z skalowanie w poziomie przez współczynnik 2 następuje 30 stopni.</span><span class="sxs-lookup"><span data-stu-id="2255e-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="2255e-133">Na poniższej ilustracji przedstawiono nowe współrzędnych i prostokąty dwa.</span><span class="sxs-lookup"><span data-stu-id="2255e-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="2255e-134">![Przekształcenia](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="2255e-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2255e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2255e-135">See Also</span></span>  
 [<span data-ttu-id="2255e-136">Systemy i transformacje współrzędnych</span><span class="sxs-lookup"><span data-stu-id="2255e-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="2255e-137">Używanie przekształceń w zarządzanym GDI +</span><span class="sxs-lookup"><span data-stu-id="2255e-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)