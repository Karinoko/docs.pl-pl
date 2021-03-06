---
title: 'Porady: określanie, który węzeł TreeView został kliknięty (Formularze systemu Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: d1e9df6a928f1ea60e4663c78d204ec2b16baf23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530630"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Porady: określanie, który węzeł TreeView został kliknięty (Formularze systemu Windows)
Podczas pracy z formularzami Windows <xref:System.Windows.Forms.TreeView> typowych zadań jest sterowanie ustalenie, który węzeł został kliknięty i reagowania.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Aby ustalić, który węzeł TreeView został kliknięty  
  
1.  Użyj <xref:System.EventArgs> obiektu zwraca odwołanie do obiektu węzła klikniętego.  
  
2.  Określanie, który węzeł został kliknięty sprawdzając <xref:System.Windows.Forms.TreeViewEventArgs> klasy, która zawiera dane powiązane ze zdarzeniem.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  Alternatywnie, można użyć <xref:System.Windows.Forms.MouseEventArgs> z <xref:System.Windows.Forms.Control.MouseDown> lub <xref:System.Windows.Forms.Control.MouseUp> zdarzeń, aby uzyskać <xref:System.Drawing.Point.X%2A> i <xref:System.Drawing.Point.Y%2A> koordynować wartości <xref:System.Drawing.Point> którym wystąpił kliknięcie. Następnie należy użyć <xref:System.Windows.Forms.TreeView> formantu <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metodę, aby określić, który węzeł został kliknięty.  
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
