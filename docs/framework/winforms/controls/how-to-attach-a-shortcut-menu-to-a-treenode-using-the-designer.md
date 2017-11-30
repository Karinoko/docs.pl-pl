---
title: "Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ec1b0236aab0f4ac61cb58d4fe006d17594e17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="2ff8e-102">Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="2ff8e-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="2ff8e-103">Formularze systemu Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery wyświetlane w okienku po lewej stronie Eksploratora Windows funkcji w systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="2ff8e-104">Przez ustawienie <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można podać kontekstowa operacji użytkownikowi po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> formantu.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="2ff8e-105">Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika z poszczególnymi <xref:System.Windows.Forms.TreeNode> elementy, można dodać dostosowanego poziomu funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff8e-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2ff8e-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2ff8e-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2ff8e-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="2ff8e-109">Aby skojarzyć menu skrótów z elementu TreeNode w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="2ff8e-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="2ff8e-110">Dodaj <xref:System.Windows.Forms.TreeView> sterowania do formularza, a następnie dodaj węzły do <xref:System.Windows.Forms.TreeView> zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="2ff8e-111">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ff8e-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="2ff8e-112">Dodaj <xref:System.Windows.Forms.ContextMenuStrip> składnika do formularza, a następnie dodaj elementy menu do menu skrótów, które reprezentują chcesz udostępnić w czasie wykonywania operacji na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="2ff8e-113">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów Menu do paska ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="2ff8e-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="2ff8e-114">Otwórz ponownie **TreeNodeEditor** okno dialogowe <xref:System.Windows.Forms.TreeView> sterowania, wybierz węzeł, aby edytować i ustawić jej <xref:System.Windows.Forms.ContextMenuStrip> właściwości do menu skrótów, który został dodany.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="2ff8e-115">Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów po kliknięciu prawym przyciskiem myszy węzeł.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="2ff8e-116">Ponadto można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.</span><span class="sxs-lookup"><span data-stu-id="2ff8e-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff8e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff8e-117">See Also</span></span>  
 [<span data-ttu-id="2ff8e-118">TreeView — formant</span><span class="sxs-lookup"><span data-stu-id="2ff8e-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="2ff8e-119">Informacje o formancie TreeView</span><span class="sxs-lookup"><span data-stu-id="2ff8e-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2ff8e-120">ContextMenuStrip — formant</span><span class="sxs-lookup"><span data-stu-id="2ff8e-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)