---
title: "Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows"
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
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c6f28ac69e2799a25f75c3093d9c8f1ef01bc48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5290d-102">Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5290d-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5290d-103"><xref:System.Windows.Forms.DataGridView> Formant zawiera <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlania komórki z interfejsem użytkownika (UI), jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="5290d-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="5290d-104">Jednak <xref:System.Windows.Forms.DataGridViewButtonCell> nie zapewnia możliwość wyłączenia wygląd przycisku wyświetlany przez komórki.</span><span class="sxs-lookup"><span data-stu-id="5290d-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="5290d-105">Poniższy przykład kodu pokazuje sposób dostosowywania <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlenia przycisków, które mogą być wyświetlane wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5290d-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="5290d-106">W przykładzie zdefiniowano nowy typ komórki `DataGridViewDisableButtonCell`, która jest pochodną <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="5290d-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="5290d-107">Ten typ komórki zapewnia nowy `Enabled` właściwość, która może być ustawiony na `false` do rysowania wyłączony przycisk w komórce.</span><span class="sxs-lookup"><span data-stu-id="5290d-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="5290d-108">W przykładzie zdefiniowano także nowy typ kolumny, `DataGridViewDisableButtonColumn`, który wyświetla `DataGridViewDisableButtonCell` obiektów.</span><span class="sxs-lookup"><span data-stu-id="5290d-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="5290d-109">Aby zademonstrować tego nowych komórek i kolumn typ, bieżąca wartość <xref:System.Windows.Forms.DataGridViewCheckBoxCell> w obiekcie nadrzędnym <xref:System.Windows.Forms.DataGridView> Określa, czy `Enabled` właściwość `DataGridViewDisableButtonCell` w tym samym wierszu jest `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="5290d-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5290d-110">Jeśli pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, należy zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania.</span><span class="sxs-lookup"><span data-stu-id="5290d-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="5290d-111">Należy także wywołać klasy podstawowej `Clone` metody, aby właściwości klasy podstawowej są kopiowane do nowej komórki lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="5290d-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5290d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5290d-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5290d-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5290d-113">Compiling the Code</span></span>  
 <span data-ttu-id="5290d-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5290d-114">This example requires:</span></span>  
  
-   <span data-ttu-id="5290d-115">Odwołania do zestawów systemu, System.Drawing, System.Windows.Forms i System.Windows.Forms.VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="5290d-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
 <span data-ttu-id="5290d-116">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5290d-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5290d-117">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5290d-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5290d-118">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5290d-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5290d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5290d-119">See Also</span></span>  
 [<span data-ttu-id="5290d-120">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5290d-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5290d-121">DataGridView — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="5290d-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="5290d-122">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5290d-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)