---
title: "Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7223fc47c885b7e659b9bab00c276759410d2567
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="24abe-102">Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="24abe-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="24abe-103">Formularze systemu Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać wiele kolumn dla każdej listy elementów w **szczegóły** widoku.</span><span class="sxs-lookup"><span data-stu-id="24abe-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="24abe-104">Kolumny służy do wyświetlania kilka typów informacji na temat każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="24abe-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="24abe-105">Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i datę ostatniej modyfikacji pliku.</span><span class="sxs-lookup"><span data-stu-id="24abe-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="24abe-106">Informacji o wprowadzaniu kolumny po ich utworzeniu można zobaczyć [porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="24abe-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="24abe-107">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="24abe-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="24abe-108">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="24abe-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24abe-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="24abe-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="24abe-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="24abe-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="24abe-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="24abe-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="24abe-112">Aby dodać kolumny w Projektancie</span><span class="sxs-lookup"><span data-stu-id="24abe-112">To add columns in the designer</span></span>  
  
1.  <span data-ttu-id="24abe-113">W **właściwości** okna, ustaw dla formantu <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="24abe-113">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="24abe-114">W **właściwości** okna, kliknij przycisk **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="24abe-114">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     <span data-ttu-id="24abe-115">**Edytora kolekcji ColumnHeader** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="24abe-115">The **ColumnHeader Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="24abe-116">Użyj **Dodaj** przycisk, aby dodać nowe kolumny.</span><span class="sxs-lookup"><span data-stu-id="24abe-116">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="24abe-117">Następnie można wybrać nagłówek kolumny i Ustaw tekst (podpis kolumny), wyrównanie tekstu i szerokość.</span><span class="sxs-lookup"><span data-stu-id="24abe-117">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24abe-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24abe-118">See Also</span></span>  
 [<span data-ttu-id="24abe-119">Informacje o formancie ListView</span><span class="sxs-lookup"><span data-stu-id="24abe-119">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="24abe-120">Porady: Dodawanie i usuwanie elementów za pomocą systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="24abe-120">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="24abe-121">Porady: wyświetlanie podelementów w kolumnach z systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="24abe-121">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="24abe-122">Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="24abe-122">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="24abe-123">Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="24abe-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)