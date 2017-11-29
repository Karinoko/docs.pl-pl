---
title: "Porady: używanie klasy renderowania formantu"
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
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ff10cd12889750e3d32fcfce080d472f40bb9c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="a16cd-102">Porady: używanie klasy renderowania formantu</span><span class="sxs-lookup"><span data-stu-id="a16cd-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="a16cd-103">W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Forms.ComboBoxRenderer> klasy do renderowania kontrolki pola kombi strzałkę listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="a16cd-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="a16cd-104">Przykład składa się z <xref:System.Windows.Forms.Control.OnPaint%2A> metody proste kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="a16cd-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="a16cd-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Właściwość jest używana do określenia, czy style wizualne są włączone w klienckim obszarze aplikacji systemu windows.</span><span class="sxs-lookup"><span data-stu-id="a16cd-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="a16cd-106">Jeżeli style wizualne są aktywne, a następnie <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> strzałkę listy rozwijanej przy użyciu stylów wizualnych; spowoduje, że metoda w przeciwnym razie <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> spowoduje, że strzałkę listy rozwijanej w stylu klasycznym Windows metody.</span><span class="sxs-lookup"><span data-stu-id="a16cd-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a16cd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a16cd-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a16cd-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a16cd-108">Compiling the Code</span></span>  
 <span data-ttu-id="a16cd-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a16cd-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a16cd-110">Formant niestandardowy pochodną <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="a16cd-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="a16cd-111">A <xref:System.Windows.Forms.Form> obsługującego kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="a16cd-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="a16cd-112">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a16cd-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16cd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a16cd-113">See Also</span></span>  
 [<span data-ttu-id="a16cd-114">Renderowanie formantów przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="a16cd-114">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)