---
title: 'Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 2491f4d4c40ea412ee42f8cd99c4c8682baa94a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525941"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.TreeView> formant przechowuje węzły najwyższego poziomu w jego <xref:System.Windows.Forms.TreeView.Nodes%2A> kolekcji. Każdy <xref:System.Windows.Forms.TreeNode> również ma własną <xref:System.Windows.Forms.TreeNode.Nodes%2A> kolekcji do przechowywania węzły podrzędne. Obie właściwości kolekcji są typu <xref:System.Windows.Forms.TreeNodeCollection>, który zawiera członków kolekcji standardowych, które umożliwiają dodawanie, usuwanie i rozmieszczanie węzłów w jeden poziom w hierarchii węzła.  
  
### <a name="to-add-nodes-programmatically"></a>Aby dodać węzły programowo  
  
1.  Użyj <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> metody widok drzewa <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a>Usuwanie węzłów programowo  
  
1.  Użyj <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> metody widok drzewa <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości do jednego węzła, usuń lub <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> metodę, aby wyczyścić wszystkie węzły.  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Instrukcje: określanie, który węzeł TreeView został kliknięty](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
