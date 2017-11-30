---
title: Propagacja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bfe861d6b535c7158ae930d4f31ac0ad4bae6721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="propagation"></a><span data-ttu-id="47750-102">Propagacja</span><span class="sxs-lookup"><span data-stu-id="47750-102">Propagation</span></span>
<span data-ttu-id="47750-103">W tym temacie opisano działanie propagacją [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] śledzenie modelu.</span><span class="sxs-lookup"><span data-stu-id="47750-103">This topic describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="47750-104">Przy użyciu propagacji służące do skorelowania działań w obrębie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="47750-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="47750-105">Propagacja zapewnia użytkownikowi bezpośredni korelacji błędu śledzi w tej samej jednostce przetwarzania przez punkty końcowe aplikacji, na przykład żądania.</span><span class="sxs-lookup"><span data-stu-id="47750-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="47750-106">Błędy emitowane na różnych punktów końcowych w tej samej jednostce przetwarzania są pogrupowane w to samo działanie nawet w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47750-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="47750-107">Jest to realizowane za pośrednictwem Propagacja identyfikatora działania w nagłówkach wiadomości.</span><span class="sxs-lookup"><span data-stu-id="47750-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="47750-108">W związku z tym jeśli upłynie limit czasu klienta z powodu wewnętrznego błędu serwera, oba błędy są wyświetlane w to samo działanie do bezpośredniego korelacji.</span><span class="sxs-lookup"><span data-stu-id="47750-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="47750-109">Aby to zrobić, użyj `ActivityTracing` ustawienie, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="47750-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="47750-110">Ponadto ustawić `propagateActivity` atrybutu dla `System.ServiceModel` źródła śledzenia na wszystkich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="47750-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="47750-111">Propagacja działania jest konfigurowalne możliwości, który powoduje, że [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] można dodać nagłówka do wiadomości wychodzących, takich jak identyfikator działania na TLS.</span><span class="sxs-lookup"><span data-stu-id="47750-111">Activity propagation is a configurable capability that causes [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="47750-112">Jeśli dołączysz to na kolejnych ślady po stronie serwera, firma Microsoft skorelowania działania klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="47750-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="47750-113">Propagacji definicji</span><span class="sxs-lookup"><span data-stu-id="47750-113">Propagation Definition</span></span>  
 <span data-ttu-id="47750-114">GAId M działania jest propagowana do działania N, jeśli wszystkie następujące warunki.</span><span class="sxs-lookup"><span data-stu-id="47750-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="47750-115">N została utworzona, ponieważ M</span><span class="sxs-lookup"><span data-stu-id="47750-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="47750-116">W M gAId jest znana N</span><span class="sxs-lookup"><span data-stu-id="47750-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="47750-117">W N gAId jest równa gAId M firmy.</span><span class="sxs-lookup"><span data-stu-id="47750-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="47750-118">GAId są propagowane za pomocą identyfikatora nagłówek komunikatu, jak pokazano na poniższej schematu XML.</span><span class="sxs-lookup"><span data-stu-id="47750-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="47750-119">Poniżej przedstawiono przykładowy nagłówek komunikatu.</span><span class="sxs-lookup"><span data-stu-id="47750-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="47750-120">Propagacja i granice działania</span><span class="sxs-lookup"><span data-stu-id="47750-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="47750-121">Gdy identyfikator działania są propagowane w obrębie punktów końcowych, odbiorcy wiadomości emituje rozpoczęcia i zatrzymania śledzi z tym identyfikatorem działania (propagowany).</span><span class="sxs-lookup"><span data-stu-id="47750-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="47750-122">W związku z tym jest rozpoczęcie i zakończenie śledzenia z tym gAId z każdego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="47750-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="47750-123">Jeśli punkty końcowe w ramach tego samego procesu, użyj takiej samej nazwy źródła śledzenia są tworzone wielu rozpoczęcie i zakończenie o tej samej sekcji (tego samego gAId, tego samego źródła śledzenia, sam proces).</span><span class="sxs-lookup"><span data-stu-id="47750-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="47750-124">Synchronizacja</span><span class="sxs-lookup"><span data-stu-id="47750-124">Synchronization</span></span>  
 <span data-ttu-id="47750-125">Aby zsynchronizować zdarzenia przez punkty końcowe, które działają na różnych maszynach, CorrelationId jest dodawana do nagłówka identyfikatora, który są propagowane w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="47750-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="47750-126">Narzędzia można użyć tego Identyfikatora zsynchronizować zdarzeń na komputerach z rozbieżność zegara.</span><span class="sxs-lookup"><span data-stu-id="47750-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="47750-127">W szczególności narzędzia podglądu śledzenia usługi używa tego Identyfikatora wyświetlania przepływów wiadomości między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="47750-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47750-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47750-128">See Also</span></span>  
 [<span data-ttu-id="47750-129">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="47750-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="47750-130">Przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="47750-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="47750-131">Scenariusze śledzenia end-To-End</span><span class="sxs-lookup"><span data-stu-id="47750-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="47750-132">Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="47750-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)