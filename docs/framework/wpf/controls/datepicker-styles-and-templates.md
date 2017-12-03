---
title: Style selektora daty i szablony
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbe8a3935da2d9aa928467b4c64da455f3b53c5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker-styles-and-templates"></a>Style selektora daty i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.DatePicker> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Części selektora daty  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.DatePicker> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|Katalog główny formantu.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Przycisk otwiera i zamyka <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Pole tekstowe, które umożliwia wprowadzania daty.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Okienko wyskakujące <xref:System.Windows.Controls.DatePicker> formantu.|  
  
## <a name="datepicker-states"></a>Stany selektora daty  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.DatePicker> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.DatePicker> Jest wyłączona.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="datepickertextbox-parts"></a>Części DatePickerTextBox  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Primitives.DatePickerTextBox> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|Element, który zawiera początkowy tekst w <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlany w tym elemencie.|  
  
## <a name="datepickertextbox-states"></a>Stany DatePickerTextBox  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Primitives.DatePickerTextBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Wyłączone|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> Jest wyłączona.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Fokus|FocusStates|Formant ma fokus.|  
|Bez fokusu|FocusStates|Formant nie ma fokusa.|  
|Oznaczone znakiem wodnym|WatermarkStates|Kontrolka wyświetla jego początkowy tekst.  <xref:System.Windows.Controls.Primitives.DatePickerTextBox> Jest w stanie, gdy użytkownik nie ma wprowadzony tekst lub wybrać datę.|  
|Unwatermarked|WatermarkStates|Użytkownik wprowadził tekstu do <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ani nie wybrano daty w <xref:System.Windows.Controls.DatePicker>.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="datepicker-controltemplate-example"></a>Przykład ControlTemplate selektora daty  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.DatePicker> formantu.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Dostosowywanie formantu](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)