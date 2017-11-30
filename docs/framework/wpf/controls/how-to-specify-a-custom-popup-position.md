---
title: "Jak określić niestandardowe położenie okna podręcznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="21f34-102">Jak określić niestandardowe położenie okna podręcznego</span><span class="sxs-lookup"><span data-stu-id="21f34-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="21f34-103">W tym przykładzie przedstawiono sposób określania pozycjonowanie niestandardowe dla <xref:System.Windows.Controls.Primitives.Popup> decyduje o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="21f34-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21f34-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="21f34-104">Example</span></span>  
 <span data-ttu-id="21f34-105">Gdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> wywołuje zdefiniowane wystąpienia <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="21f34-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="21f34-106">Ten delegat zwraca zestaw możliwych punktów, które są względem lewym górnym rogu obszar docelowy i lewym górnym rogu aplikacji <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="21f34-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="21f34-107"><xref:System.Windows.Controls.Primitives.Popup> Umieszczania występuje w momencie, który zapewnia widoczność najlepsze.</span><span class="sxs-lookup"><span data-stu-id="21f34-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="21f34-108">Poniższy przykład przedstawia sposób definiowania pozycja <xref:System.Windows.Controls.Primitives.Popup> przez ustawienie <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> właściwości <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="21f34-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="21f34-109">Przedstawiono również sposób utworzyć i przypisać <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegata w celu umieść <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="21f34-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="21f34-110">Zwraca delegata wywołania zwrotnego, dwa <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="21f34-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="21f34-111">Jeśli <xref:System.Windows.Controls.Primitives.Popup> jest ukryty przez krawędzi ekranu, na pierwszym miejscu <xref:System.Windows.Controls.Primitives.Popup> znajduje się w drugim pozycji.</span><span class="sxs-lookup"><span data-stu-id="21f34-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="21f34-112">Pełny przykład, zobacz [podręcznego umieszczania próbki](http://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="21f34-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f34-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21f34-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="21f34-114">Omówienie menu podręczne</span><span class="sxs-lookup"><span data-stu-id="21f34-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="21f34-115">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="21f34-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)