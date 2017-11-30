---
title: "Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows"
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
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 811c5edd2f12794035b66260f17255283f405cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="701c6-102">Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="701c6-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="701c6-103">W poniższych procedurach pokazano kilka typowych scenariuszy, które dostosować lub połączyć dostępne opcje ustalania rozmiaru <xref:System.Windows.Forms.DataGridView> kontroli i dla określonych kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="701c6-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="701c6-104">Aby utworzyć kolumnę o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="701c6-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="701c6-105">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości `true`i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="701c6-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="701c6-106">Aby utworzyć kolumnę, które można dostosować jego rozmiaru w celu dopasowania do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="701c6-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="701c6-107">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości do trybu na podstawie zawartości zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="701c6-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="701c6-108">Aby utworzyć tryb wypełniania kolumny wartości różnych rozmiarach i ważność</span><span class="sxs-lookup"><span data-stu-id="701c6-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="701c6-109">Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> ustawiony tryb zmiany rozmiaru dla wszystkich kolumn, które nie zastępują tej wartości.</span><span class="sxs-lookup"><span data-stu-id="701c6-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="701c6-110">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości kolumn do wartości, które są proporcjonalne do jego średni zawartości szerokości.</span><span class="sxs-lookup"><span data-stu-id="701c6-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="701c6-111">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ważnych kolumnach częściowe wyświetlanie zawartości.</span><span class="sxs-lookup"><span data-stu-id="701c6-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="701c6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="701c6-112">Example</span></span>  
 <span data-ttu-id="701c6-113">W poniższym przykładzie kompletny kod zawiera aplikacji demonstracyjnej, która może ułatwić poznawanie opcje rozmiaru opisanych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="701c6-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="701c6-114">Aby używać tej aplikacji Pokaz:</span><span class="sxs-lookup"><span data-stu-id="701c6-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="701c6-115">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="701c6-115">Change the size of the form.</span></span> <span data-ttu-id="701c6-116">Sprawdź, jak tryb wypełniania kolumny zmienić ich szerokość podczas zachowywania proporcje wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="701c6-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="701c6-117">Sprawdź, jak kolumny <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> uniemożliwia zmianę, gdy formularz jest za mały.</span><span class="sxs-lookup"><span data-stu-id="701c6-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="701c6-118">Zmienianie rozmiarów kolumn sekcjami kolumny za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="701c6-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="701c6-119">Sprawdź, jak niektóre kolumny nie może być po zmianie rozmiaru i jak o zmiennym rozmiarze kolumn nie można dokonać korekty węższe niż ich minimalnej szerokości.</span><span class="sxs-lookup"><span data-stu-id="701c6-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="701c6-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="701c6-120">Compiling the Code</span></span>  
 <span data-ttu-id="701c6-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="701c6-121">This example requires:</span></span>  
  
-   <span data-ttu-id="701c6-122">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="701c6-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="701c6-123">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="701c6-123">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="701c6-124">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="701c6-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="701c6-125">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="701c6-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701c6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="701c6-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>