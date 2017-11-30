---
title: "Jak animować w stylu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="9caf3-102">Jak animować w stylu</span><span class="sxs-lookup"><span data-stu-id="9caf3-102">How to: Animate in a Style</span></span>
<span data-ttu-id="9caf3-103">W tym przykładzie pokazano, jak można animować właściwości w stylu.</span><span class="sxs-lookup"><span data-stu-id="9caf3-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="9caf3-104">W przypadku działania animacji jest używana w stylu bezpośrednio można zastosować tylko element framework, dla którego styl jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="9caf3-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="9caf3-105">Docelowy obiekt obiektu freezable, możesz musi "dot w dół" z właściwością styl elementu.</span><span class="sxs-lookup"><span data-stu-id="9caf3-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="9caf3-106">W poniższym przykładzie kilka animacje są zdefiniowane w stylu i stosowane do <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="9caf3-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="9caf3-107">Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem, zniknie nieprzezroczyste częściowo przezroczyste i Wstecz ponownie, wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="9caf3-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="9caf3-108">Gdy użytkownik przesuwa wskaźnik myszy poza przycisk, staje się całkowicie przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="9caf3-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="9caf3-109">Po kliknięciu przycisku kolor tła zmienia pomarańczowy do białe i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="9caf3-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="9caf3-110">Ponieważ <xref:System.Windows.Media.SolidColorBrush> używana do malowania przycisku nie może być celem bezpośrednio, jest dostępny przez dotting w dół od przycisku <xref:System.Windows.Controls.Control.Background%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9caf3-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9caf3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="9caf3-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="9caf3-112">Należy pamiętać, że gdy animacji w stylu, możliwe do obiektów docelowych, które nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="9caf3-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="9caf3-113">Załóżmy na przykład, używa własnego stylu <xref:System.Windows.Media.SolidColorBrush> ustaw właściwość tło przycisku, ale w niektórych punktu styl jest zastępowany i ustawiono tło przycisku <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="9caf3-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="9caf3-114">Próby animować <xref:System.Windows.Media.SolidColorBrush> nie będzie zgłaszać wyjątek; animacji po prostu nie powiedzie się trybie dyskretnym.</span><span class="sxs-lookup"><span data-stu-id="9caf3-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="9caf3-115">Aby uzyskać więcej informacji na temat scenorysu przeznaczonych dla składni, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9caf3-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="9caf3-116">Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9caf3-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="9caf3-117">Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="9caf3-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>