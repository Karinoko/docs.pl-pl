---
title: "Śledzenie cykliczne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b86867793424d6d0b42a18d6a2fbd6175bc1a47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="circular-tracing"></a><span data-ttu-id="5a0d4-102">Śledzenie cykliczne</span><span class="sxs-lookup"><span data-stu-id="5a0d4-102">Circular Tracing</span></span>
<span data-ttu-id="5a0d4-103">W tym przykładzie przedstawiono implementacji obiektu nasłuchującego śledzenia cyklicznego buforu.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="5a0d4-104">Typowy scenariusz dla usług produkcji jest usług, które są dostępne przez dłuższy czas i ma włączonego na niskim poziomie rejestrowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="5a0d4-105">Te usługi używać dużej ilości miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="5a0d4-106">Podczas rozwiązywania problemów z usługą, najnowszych danych w dzienniku śledzenia ma zastosowanie w rozwiązaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="5a0d4-107">Ten przykład przedstawia implementację odbiornika śledzenia cyklicznego buforu, w którym tylko najnowsze dane śledzenia są przechowywane na dysku do skonfigurowanej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="5a0d4-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) i zawiera odbiornik śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a0d4-109">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5a0d4-110">W tym przykładzie przyjęto założenie, że czytelnik zna [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowe i przeczytanie w dokumentacji dostarczonej [śledzenie i rejestrowanie komunikatów](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="5a0d4-111">Odbiornik śledzenia bufora cykliczne</span><span class="sxs-lookup"><span data-stu-id="5a0d4-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="5a0d4-112">Pojęcie za implementacji obiektu nasłuchującego śledzenia cyklicznego buforu jest dwóch plików, które każdego przechowywać do połowy danych dziennika całkowita żądanego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="5a0d4-113">Odbiornik tworzą jeden plik i zapisuje do tego pliku, dopóki nie osiągnie limitu połowy rozmiaru danych, po czym przełącza do pliku.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="5a0d4-114">Gdy odbiornika osiągnie limit dla drugiego pliku - zastępuje pierwszy plik z nowe śledzenie.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="5a0d4-115">Tym odbiorniku pochodną `XmlWriteTraceListener` i umożliwia dzienniki, aby je przeglądać za pomocą [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5a0d4-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="5a0d4-116">Podczas próby wyświetlić dzienniki, dwa pliki dziennika można łatwo odtwarzane otwierając oba pliki dziennika w tym samym czasie w narzędziu Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="5a0d4-117">Narzędzia podglądu śledzenia usługi automatycznie odpowiada on za sortowanie dane śledzenia, aby były wyświetlane w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5a0d4-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5a0d4-118">Configuration</span></span>  
 <span data-ttu-id="5a0d4-119">Usługę można skonfigurować do używania cykliczne nasłuchującego śledzenia buforu, dodając następujący kod dla elementów źródła i odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="5a0d4-120">Maksymalny rozmiar jest określany przez ustawienie `maxFileSizeKB` atrybut w konfiguracji odbiornika śledzenia cykliczne.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="5a0d4-121">Zostało to przedstawione w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a0d4-122">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="5a0d4-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5a0d4-123">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a0d4-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5a0d4-124">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a0d4-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5a0d4-125">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a0d4-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a0d4-126">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5a0d4-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5a0d4-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5a0d4-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a0d4-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a0d4-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="5a0d4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a0d4-130">See Also</span></span>  
 [<span data-ttu-id="5a0d4-131">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="5a0d4-131">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)