---
title: ManualResetEvent i ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85d0c5c291743c6daac549e15d479fcf332235c
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452826"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent i ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalne, które można ręcznie zresetować po zostanie zasygnalizowane. Ta klasa reprezentuje przypadkiem szczególnym klasy bazowej, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacji koncepcyjnego dla użycia i funkcje ręczne Resetowanie zdarzenia.  
  
 A <xref:System.Threading.ManualResetEvent> obiekt pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda jest wywoływana. Dowolną liczbę oczekujących wątki lub wątki, które oczekiwania na zdarzenie po zostało zasygnalizowane, może być zwolnione, gdy stan obiektu jest sygnalizowane.
  
 W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> klasy w celu zapewnienia lepszej wydajności po spodziewane czasy oczekiwania będą bardzo krótkie, a gdy zdarzenie nie przekraczają granice procesu. <xref:System.Threading.ManualResetEventSlim> używa zajęty, obracanie przez krótki czas podczas oczekiwania na zdarzenie zostało zasygnalizowane. W przypadku krótkie czasy oczekiwania rotowania może być znacznie mniej kosztowne niż za pomocą uchwytów oczekiwania. Jednakże, jeśli zdarzenie nie zasygnalizowane w przedziale czasu, <xref:System.Threading.ManualResetEventSlim> sortuje ponownie do oczekiwania uchwyt wydarzeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [AutoResetEvent](autoresetevent.md)  
- [SpinWait](spinwait.md)  
- [Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md)
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)  
- [Wątkowość](index.md)  
