---
title: Jak kontrolować kiedy tekst TextBox aktualizuje źródło
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 52f3a8d3a5d78a211367722b3042eb50f6ac36d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557228"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Jak kontrolować kiedy tekst TextBox aktualizuje źródło
W tym temacie opisano sposób użycia <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość, aby kontrolować czas powiązania źródła aktualizacji. Temat używa <xref:System.Windows.Controls.TextBox> formant jako przykład.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> Właściwość ma wartość domyślną <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Oznacza to, czy aplikacja ma <xref:System.Windows.Controls.TextBox> z z danymi <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> właściwości, wpisz w <xref:System.Windows.Controls.TextBox> nie zaktualizować źródła do <xref:System.Windows.Controls.TextBox> traci fokus (na przykład po kliknięciu od <xref:System.Windows.Controls.TextBox>).  
  
 Jeśli źródło aktualizacji podczas wpisywania, należy ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> powiązania <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. W poniższym przykładzie wyróżnione wiersze kodu pokazują, że `Text` właściwości obu <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.TextBlock> są powiązane z tą samą właściwością źródła. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość <xref:System.Windows.Controls.TextBox> powiązania ma ustawioną wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 W związku z tym <xref:System.Windows.Controls.TextBlock> pokazuje tego samego tekstu (z powodu zmiany pliku źródłowego), jako użytkownik wprowadzi tekst do <xref:System.Windows.Controls.TextBox>, jak pokazano na poniższym zrzucie ekranu przykładu:  
  
 ![Zrzut ekranu przedstawiający przykład powiązania danych proste](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Jeśli masz okna dialogowego lub formularza można edytować użytkownika, a chcesz mają być odroczone aktualizacje źródłowego, dopóki użytkownik nie zakończy Edycja pól i kliknie przycisk "OK", można ustawić <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości powiązania do <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, jak w poniższym przykładzie:  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Podczas ustawiania <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> do wartości <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, wartość źródła zmienia tylko, gdy aplikacja wywołuje <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> metody. Poniższy przykład przedstawia sposób wywołania <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> dla `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Użyj tę samą metodę dla właściwości inne formanty, ale należy pamiętać, że inne właściwości mają domyślnie <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartość <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> strony właściwości.  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Właściwość dotyczy źródło aktualizacji i w związku z tym dotyczy tylko <xref:System.Windows.Data.BindingMode.TwoWay> lub <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania. Aby uzyskać <xref:System.Windows.Data.BindingMode.TwoWay> i <xref:System.Windows.Data.BindingMode.OneWayToSource> powiązania do pracy źródła obiektu konieczność zapewnienia powiadomienia o zmianie właściwości. Może się odwoływać do próbek wymienione w tym temacie, aby uzyskać więcej informacji. Ponadto można przyjrzeć się [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
