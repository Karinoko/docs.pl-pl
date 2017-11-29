---
title: "Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b4eb1ce70b1ec4b249eb126b608c9f8578d327c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="610a2-102">Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="610a2-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="610a2-103"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> formanty mają podobne zachowania, a w niektórych przypadkach może być wymienne.</span><span class="sxs-lookup"><span data-stu-id="610a2-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="610a2-104">Brak sytuacji, gdy jednego lub drugiego jest bardziej odpowiednie do zadania.</span><span class="sxs-lookup"><span data-stu-id="610a2-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="610a2-105">Ogólnie rzecz biorąc pola kombi jest odpowiednie, gdy istnieje listę opcji sugerowane i pola listy jest odpowiednia, jeśli chcesz ograniczyć dane wejściowe, aby co znajduje się na liście.</span><span class="sxs-lookup"><span data-stu-id="610a2-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="610a2-106">Pole kombi zawiera pola tekstowego, w związku z czym wpisane opcji nie ma na liście.</span><span class="sxs-lookup"><span data-stu-id="610a2-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="610a2-107">Wyjątek stanowi kiedy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="610a2-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="610a2-108">W takim przypadku formantu wybierz element w przypadku wpisania jego pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="610a2-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="610a2-109">Ponadto pola kombi zaoszczędzić miejsce na formularzu.</span><span class="sxs-lookup"><span data-stu-id="610a2-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="610a2-110">Ponieważ Pełna lista nie jest wyświetlany, dopóki użytkownik kliknie strzałkę w dół, pole kombi można łatwo zmieścić w mała ilość miejsca, której nie mieści się pole listy.</span><span class="sxs-lookup"><span data-stu-id="610a2-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="610a2-111">Wyjątek jest gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: Pełna lista jest wyświetlana, a pole kombi zajmuje więcej miejsca niż czy pole listy.</span><span class="sxs-lookup"><span data-stu-id="610a2-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610a2-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="610a2-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="610a2-113">Porady: Dodawanie i usuwanie elementów z systemu Windows formularzy ComboBox, ListBox lub CheckedListBox — formant</span><span class="sxs-lookup"><span data-stu-id="610a2-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="610a2-114">Porady: sortowanie zawartości systemu Windows ComboBox, ListBox lub CheckedListBox formularzy</span><span class="sxs-lookup"><span data-stu-id="610a2-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="610a2-115">Formanty używane do obsługi opcji List formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="610a2-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)