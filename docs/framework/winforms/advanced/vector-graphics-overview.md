---
title: "Przegląd grafiki wektorowej"
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
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bb3247f531a0dac83657e118fb53ebaf708ec9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="vector-graphics-overview"></a><span data-ttu-id="665fa-102">Przegląd grafiki wektorowej</span><span class="sxs-lookup"><span data-stu-id="665fa-102">Vector Graphics Overview</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="665fa-103">Rysuje linii, prostokątów i innych kształtów w układzie współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="665fa-103"> draws lines, rectangles, and other shapes on a coordinate system.</span></span> <span data-ttu-id="665fa-104">Można wybrać spośród różnych systemów współrzędnych, ale domyślny układ współrzędnych ma źródła w lewym górnym rogu z wskazanie osi y skierowany w dół i prawej osi x.</span><span class="sxs-lookup"><span data-stu-id="665fa-104">You can choose from a variety of coordinate systems, but the default coordinate system has the origin in the upper-left corner with the x-axis pointing to the right and the y-axis pointing down.</span></span> <span data-ttu-id="665fa-105">Jednostka miary w układzie współrzędnych domyślny jest piksela.</span><span class="sxs-lookup"><span data-stu-id="665fa-105">The unit of measure in the default coordinate system is the pixel.</span></span>  
  
## <a name="the-building-blocks-of-gdi"></a><span data-ttu-id="665fa-106">Bloki konstrukcyjne GDI +</span><span class="sxs-lookup"><span data-stu-id="665fa-106">The Building Blocks of GDI+</span></span>  
 <span data-ttu-id="665fa-107">![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span><span class="sxs-lookup"><span data-stu-id="665fa-107">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span></span>  
  
 <span data-ttu-id="665fa-108">Monitor komputera tworzy wyświetlanie na tablicy regularnej kropek nazywane elementami obrazu lub pikselach.</span><span class="sxs-lookup"><span data-stu-id="665fa-108">A computer monitor creates its display on a rectangular array of dots called picture elements or pixels.</span></span> <span data-ttu-id="665fa-109">Liczba pikseli na ekranie są wyświetlane zmienia się z jednego monitora do następnego i zwykle można skonfigurować liczbę pikseli, które są wyświetlane na poszczególnych monitora w pewnym stopniu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="665fa-109">The number of pixels that appear on the screen varies from one monitor to the next, and the number of pixels that appear on an individual monitor can usually be configured to some extent by the user.</span></span>  
  
 <span data-ttu-id="665fa-110">![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span><span class="sxs-lookup"><span data-stu-id="665fa-110">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span></span>  
  
 <span data-ttu-id="665fa-111">Jeśli używasz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do rysowania linii, prostokąta lub krzywej, podaj niektóre najważniejsze informacje na temat elementu, który ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="665fa-111">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, rectangle, or curve, you provide certain key information about the item to be drawn.</span></span> <span data-ttu-id="665fa-112">Na przykład można określić wiersz, zapewniając dwa punkty i prostokąt można określić, podając punkt, wysokości i szerokości.</span><span class="sxs-lookup"><span data-stu-id="665fa-112">For example, you can specify a line by providing two points, and you can specify a rectangle by providing a point, a height, and a width.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="665fa-113">działa w połączeniu z oprogramowaniem sterownik ekranu do określenia, które pikseli musi być włączona do wyświetlenia linii, prostokąta lub krzywej.</span><span class="sxs-lookup"><span data-stu-id="665fa-113"> works in conjunction with the display driver software to determine which pixels must be turned on to show the line, rectangle, or curve.</span></span> <span data-ttu-id="665fa-114">Na poniższej ilustracji przedstawiono pikseli, które są włączone, aby wyświetlić wiersz z punktu (4, 2) w punkcie (12, 8).</span><span class="sxs-lookup"><span data-stu-id="665fa-114">The following illustration shows the pixels that are turned on to display a line from the point (4, 2) to the point (12, 8).</span></span>  
  
 <span data-ttu-id="665fa-115">![Grafika wektorowa](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span><span class="sxs-lookup"><span data-stu-id="665fa-115">![Vector graphic](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span></span>  
  
 <span data-ttu-id="665fa-116">Wraz z upływem czasu niektóre podstawowe bloki konstrukcyjne okazały się najbardziej przydatny w przypadku tworzenia obrazów dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="665fa-116">Over time, certain basic building blocks have proven to be the most useful for creating two-dimensional pictures.</span></span> <span data-ttu-id="665fa-117">Te bloki konstrukcyjne, które są obsługiwane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], podano w poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="665fa-117">These building blocks, which are all supported by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], are given in the following list:</span></span>  
  
-   <span data-ttu-id="665fa-118">wiersze</span><span class="sxs-lookup"><span data-stu-id="665fa-118">Lines</span></span>  
  
-   <span data-ttu-id="665fa-119">Prostokątów</span><span class="sxs-lookup"><span data-stu-id="665fa-119">Rectangles</span></span>  
  
-   <span data-ttu-id="665fa-120">Wielokropek</span><span class="sxs-lookup"><span data-stu-id="665fa-120">Ellipses</span></span>  
  
-   <span data-ttu-id="665fa-121">Łuki</span><span class="sxs-lookup"><span data-stu-id="665fa-121">Arcs</span></span>  
  
-   <span data-ttu-id="665fa-122">Wielokąty</span><span class="sxs-lookup"><span data-stu-id="665fa-122">Polygons</span></span>  
  
-   <span data-ttu-id="665fa-123">Krzywe kardynalne</span><span class="sxs-lookup"><span data-stu-id="665fa-123">Cardinal splines</span></span>  
  
-   <span data-ttu-id="665fa-124">krzywe Beziera</span><span class="sxs-lookup"><span data-stu-id="665fa-124">Bezier splines</span></span>  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a><span data-ttu-id="665fa-125">Metody do rysowania obiektu grafiki</span><span class="sxs-lookup"><span data-stu-id="665fa-125">Methods For Drawing with a Graphics Object</span></span>  
 <span data-ttu-id="665fa-126"><xref:System.Drawing.Graphics> Klasy w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] udostępnia następujące metody rysowanie elementów na poprzedniej liście: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (dla kardynalne), a <xref:System.Drawing.Graphics.DrawBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="665fa-126">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for drawing the items in the previous list: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (for cardinal splines), and <xref:System.Drawing.Graphics.DrawBezier%2A>.</span></span> <span data-ttu-id="665fa-127">Każda z tych metod jest przeciążony; oznacza to, że każda metoda obsługuje kilka list innym parametrem.</span><span class="sxs-lookup"><span data-stu-id="665fa-127">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="665fa-128">Na przykład, jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> i czterech liczb całkowitych, podczas zmiany innego obiektu <xref:System.Drawing.Graphics.DrawLine%2A> odbiera — metoda <xref:System.Drawing.Pen> obiektu i dwa <xref:System.Drawing.Point> obiektów.</span><span class="sxs-lookup"><span data-stu-id="665fa-128">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers, while another variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="665fa-129">Metody na rysowanie linii, prostokątów i krzywych Beziera mają pomocnika mnogiej metody kilka elementów w pojedynczym wywołaniu: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, i <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="665fa-129">The methods for drawing lines, rectangles, and Bézier splines have plural companion methods that draw several items in a single call: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, and <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span></span> <span data-ttu-id="665fa-130">Ponadto <xref:System.Drawing.Graphics.DrawCurve%2A> metoda ma metodę Pomocnika <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, że punktu krzywej przez nawiązanie połączenia punktu końcowego krzywej początkowej zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="665fa-130">Also, the <xref:System.Drawing.Graphics.DrawCurve%2A> method has a companion method, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, that closes a curve by connecting the ending point of the curve to the starting point.</span></span>  
  
 <span data-ttu-id="665fa-131">Wszystkie metody rysowania <xref:System.Drawing.Graphics> klasy pracy w połączeniu z <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="665fa-131">All of the drawing methods of the <xref:System.Drawing.Graphics> class work in conjunction with a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="665fa-132">Aby narysować niczego, należy utworzyć co najmniej dwa obiekty: <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="665fa-132">To draw anything, you must create at least two objects: a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="665fa-133"><xref:System.Drawing.Pen> Obiekt przechowuje atrybuty, takie jak szerokość linii i kolor elementu, który ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="665fa-133">The <xref:System.Drawing.Pen> object stores attributes, such as line width and color, of the item to be drawn.</span></span> <span data-ttu-id="665fa-134"><xref:System.Drawing.Pen> Przekazano obiekt jako jeden z argumentów metody rysowania.</span><span class="sxs-lookup"><span data-stu-id="665fa-134">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the drawing method.</span></span> <span data-ttu-id="665fa-135">Na przykład, jeden odmianą <xref:System.Drawing.Graphics.DrawLine%2A> metoda <xref:System.Drawing.Pen> obiektu i czterech liczb całkowitych, jak pokazano w poniższym przykładzie rysuje prostokąt o szerokości 100, wysokości 50 i lewym górnym rogu (20, 10):</span><span class="sxs-lookup"><span data-stu-id="665fa-135">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers as shown in the following example, which draws a rectangle with a width of 100, a height of 50 and an upper-left corner of (20, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="665fa-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="665fa-136">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="665fa-137">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="665fa-137">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="665fa-138">Porady: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="665fa-138">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)