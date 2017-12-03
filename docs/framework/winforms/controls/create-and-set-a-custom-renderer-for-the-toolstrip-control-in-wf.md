---
title: "Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows"
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
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f63ff0a7336ae80ce5652cf3e4c6c7dd409882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Porady: tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows
<xref:System.Windows.Forms.ToolStrip>Formanty zapewniają obsługę łatwe do kompozycje i style. Można osiągnąć całkowicie niestandardowych wygląd i zachowanie (wygląd i działanie), albo ustawiając <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości niestandardowego modułu renderowania.  
  
 Moduły renderowania można przypisać do poszczególnych <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, lub <xref:System.Windows.Forms.StatusStrip> kontroli lub użyć <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> dotyczą wszystkich obiektów, ustawiając dla właściwości <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> właściwości <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>Zwraca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> tylko wtedy, gdy wartość <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> nie jest `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Aby utworzyć niestandardowego modułu renderowania  
  
1.  Rozszerzanie <xref:System.Windows.Forms.ToolStripRenderer> klasy.  
  
2.  Implementowanie potrzeby niestandardowe renderowanie przez zastąpienie odpowiednie *na...* elementy członkowskie  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Aby ustawić niestandardowego modułu renderowania jako bieżący renderowania  
  
1.  Aby ustawić niestandardowego modułu renderowania dla jednego <xref:System.Windows.Forms.ToolStrip>ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości niestandardowego modułu renderowania.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  Lub ustawienie niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> klasy zawartych w aplikacji: Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> niestandardowego modułu renderowania i ustaw dla właściwości <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> właściwości <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [Informacje o formancie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip — architektura formantu](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Podsumowanie technologii formantów ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)