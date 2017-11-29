---
title: "Współdziałanie z aplikacjami POX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6dbdd72dce196ea58550cff956a7b0e6fe0b1a73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="8dc52-102">Współdziałanie z aplikacjami POX</span><span class="sxs-lookup"><span data-stu-id="8dc52-102">Interoperability with POX Applications</span></span>
<span data-ttu-id="8dc52-103">"Zwykły starego XML" (POX) aplikacji komunikacji przez wymianę raw komunikaty HTTP, które zawierają tylko dane aplikacji XML, który nie jest umieszczone wewnątrz koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="8dc52-104">może zapewnić zarówno usług i klientów, którzy używają POX wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8dc52-104"> can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="8dc52-105">W usłudze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] może służyć do wdrożenia usług, które udostępniają punktów końcowych do klientów, takich jak przeglądarki sieci Web i języki skryptów, które wysyłania i odbierania wiadomości POX.</span><span class="sxs-lookup"><span data-stu-id="8dc52-105">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="8dc52-106">Na komputerze klienckim [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania może służyć do wdrożenia klientów, które komunikują się z usługami opartymi na POX.</span><span class="sxs-lookup"><span data-stu-id="8dc52-106">On the client, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dc52-107">Ten dokument został pierwotnie napisane dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="8dc52-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]<span data-ttu-id="8dc52-108">3.5 ma wbudowaną obsługę pracy z aplikacjami POX.</span><span class="sxs-lookup"><span data-stu-id="8dc52-108"> 3.5 has built-in support for working with POX applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8dc52-109">zobacz [modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="8dc52-109"> see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span></span>  
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="8dc52-110">POX programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="8dc52-110">POX Programming with WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8dc52-111">usługi, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dc52-111"> services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="8dc52-112">To niestandardowe powiązanie zawiera dwa elementy:</span><span class="sxs-lookup"><span data-stu-id="8dc52-112">This custom binding contains two elements:</span></span>  
  
-   <span data-ttu-id="8dc52-113">[ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) i</span><span class="sxs-lookup"><span data-stu-id="8dc52-113">The [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) and</span></span>  
  
-   <span data-ttu-id="8dc52-114">[ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="8dc52-114">The [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
 <span data-ttu-id="8dc52-115">Standardowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodera wiadomości tekstowych specjalnie jest skonfigurowana do używania <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartość, która pozwala na przetwarzanie XML wiadomości ładunków nie przychodzące otoczona koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-115">The standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8dc52-116">klientów, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX Użyj podobne wiązanie (pokazano w poniższym kodzie konieczne).</span><span class="sxs-lookup"><span data-stu-id="8dc52-116"> clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 <span data-ttu-id="8dc52-117">Ponieważ POX klientów należy jawnie określić identyfikatory URI, do którego wysyłania wiadomości, one zazwyczaj należy skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> na ręczny tryb adresowania przez ustawienie <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> właściwości `true` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="8dc52-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="8dc52-118">Dzięki temu wiadomości mogą być adresowane jawnie przez kod aplikacji i nie jest konieczne utworzyć nową <xref:System.ServiceModel.ChannelFactory> za każdym razem, gdy aplikacja wysyła komunikat do inny identyfikator URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>  
  
 <span data-ttu-id="8dc52-119">Ponieważ POX wiadomości nie należy używać nagłówków SOAP w celu przedstawienia informacji o protokole ważne, POX klientów i usług często muszą manipulować części realizacji źródłowego żądania HTTP, które są używane do wysyłania i odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8dc52-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="8dc52-120">Informacje protokołu specyficzne dla protokołu HTTP, takie jak nagłówków HTTP i kodów stanu są udostępniane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania za pomocą dwóch klas:</span><span class="sxs-lookup"><span data-stu-id="8dc52-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programming model through two classes:</span></span>  
  
-   <span data-ttu-id="8dc52-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje o żądaniu HTTP, takich jak nagłówki metoda i żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>  
  
-   <span data-ttu-id="8dc52-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takie jak stan HTTP opis kodu i stan, a także żadnych nagłówków odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>  
  
 <span data-ttu-id="8dc52-123">Poniższy przykładowy kod przedstawia sposób tworzenia HTTP GET komunikat żądania opisanej http://localhost:8100/klientom.</span><span class="sxs-lookup"><span data-stu-id="8dc52-123">The following code example shows how to create an HTTP GET request message that is addressed to http://localhost:8100/customers.</span></span>  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 <span data-ttu-id="8dc52-124">Po pierwsze, puste żądanie <xref:System.ServiceModel.Channels.Message> jest tworzony przez wywołanie metody <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="8dc52-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="8dc52-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr jest używany, aby wskazać, że koperty protokołu SOAP nie jest wymagany i <xref:System.String.Empty> parametr jest przekazywany jako działania.</span><span class="sxs-lookup"><span data-stu-id="8dc52-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="8dc52-126">Komunikat żądania jest następnie adresowane przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8dc52-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="8dc52-127">Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> ustawiono zlecenie HTTP GET, metoda i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ma ustawioną wartość `true` wskazująca, że żadne dane mają być wysyłane w treści komunikatu wychodzącego żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="8dc52-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="8dc52-128">Na koniec właściwości żądania jest dodawany do <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekcji, więc ona mieć wpływ jak transportu HTTP wysyła żądanie komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="8dc52-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="8dc52-129">Komunikat jest gotowa do wysłania przez odpowiednie wystąpienie <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="8dc52-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>  
  
 <span data-ttu-id="8dc52-130">Podobne techniki umożliwiają w usłudze wyodrębnić <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z komunikatu przychodzącego i konstrukcja odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8dc52-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>