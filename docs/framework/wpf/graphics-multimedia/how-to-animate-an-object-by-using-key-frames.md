---
title: Jak animować obiekt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 5e948b574e1b4a1c431b9495583e9579502576a8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416337"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Jak animować obiekt z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować obiekt, który w tym przykładzie jest <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> kontroli przy użyciu klatek kluczowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy, aby animować kolor zmienia się dla <xref:System.Windows.Controls.Page.Background%2A> właściwość <xref:System.Windows.Controls.Page> kontroli. Przykład animacji zmienia się na pędzel tła różnych w regularnych odstępach czasu. Korzysta z tą animację <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> klasy w celu utworzenia trzech różnych klatek kluczowych. Animacja korzysta z klatkami kluczowymi w następujący sposób:  
  
1.  Na końcu pierwszego sekundę animuje wystąpienie <xref:System.Windows.Media.LinearGradientBrush> klasy. Ta sekcja przykładu dotyczy gradientu liniowego kolor tła, tak aby kolor przechodzi z żółtym na pomarańczowy na czerwony.  
  
2.  Na koniec następnej sekundy animuje wystąpienie <xref:System.Windows.Media.RadialGradientBrush> klasy. Ta sekcja przykładu dotyczy gradient promieniowy kolor tła, tak aby kolor zmienia się od białego na niebieski na czarny.  
  
3.  Na koniec trzeciego sekundę animuje wystąpienie <xref:System.Windows.Media.DrawingBrush> klasy. Ta sekcja przykład dotyczy wzorzec szachownicy tła.  
  
4.  Animacja rozpoczyna się od nowa i jest powtarzany na czas nieokreślony.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> jest to jedyny typ używanego przy użyciu klatek kluczowych <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> klasy. Klucz ramek, takich jak <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> tworzenie nagłe zmiany w wartościach, to znaczy, zmiany kolorów w tym przykładzie występuje nieoczekiwanie.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Aby uzyskać pełny przykład, zobacz [przykład animacji ramki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
