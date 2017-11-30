---
title: "Przykład współużytkowania portów Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d3ee04dfd400e09e6392e78498d80a59bb88b11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="d4367-102">Przykład współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d4367-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="d4367-103">Protokół TCP/IP używa 16-bitową liczbę zwanej portem do rozróżniania połączeń z wieloma aplikacjami sieciowymi uruchomiona na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d4367-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="d4367-104">Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4367-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="d4367-105">Inne aplikacje nie może nasłuchiwać na tym porcie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="d4367-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4367-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d4367-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4367-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d4367-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4367-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d4367-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4367-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d4367-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="d4367-110">Wiele protokołów ma standard lub domyślny numer portu, które korzystają z.</span><span class="sxs-lookup"><span data-stu-id="d4367-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="d4367-111">Na przykład protokołu HTTP zazwyczaj używa portu TCP 80.</span><span class="sxs-lookup"><span data-stu-id="d4367-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="d4367-112">Internet Information Services (IIS) ma odbiornika Udostępnianie portów między wiele aplikacji HTTP.</span><span class="sxs-lookup"><span data-stu-id="d4367-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="d4367-113">Usługi IIS nasłuchuje na porcie bezpośrednio i przekazuje dalej wiadomości do odpowiedniej aplikacji na podstawie informacji w strumieniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d4367-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="d4367-114">Dzięki temu wiele aplikacji HTTP użyć tego samego numeru portu bez konieczności konkurować zarezerwować portu do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d4367-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="d4367-115">Udostępnianie portów NetTcp jest [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]funkcja umożliwiająca podobnie wiele aplikacji sieci może współużytkować jeden port.</span><span class="sxs-lookup"><span data-stu-id="d4367-115">NetTcp Port Sharing is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="d4367-116">Usługa udostępniania portów NetTcp akceptuje połączenia za pomocą protokołu net.tcp i przekazuje dalej wiadomości na podstawie ich adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d4367-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="d4367-117">Nie włączono usługi udostępniania portów NetTcp domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d4367-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="d4367-118">Przed uruchomieniem tego przykładu, musisz ręcznie włączyć usługę.</span><span class="sxs-lookup"><span data-stu-id="d4367-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="d4367-119">Aby uzyskać więcej informacji, zobacz [porady: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="d4367-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="d4367-120">Jeśli usługa zostanie wyłączona, jest wyjątek po uruchomieniu aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="d4367-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="d4367-121">Udostępnianie portów jest włączona na serwerze <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość <xref:System.ServiceModel.NetTcpBinding> powiązanie lub <xref:System.ServiceModel.Channels.TcpTransportBindingElement> elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d4367-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="d4367-122">Klient nie trzeba wiedzieć, jak udostępnianie portów został skonfigurowany do używania go na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d4367-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="d4367-123">Włączenie udostępniania portów</span><span class="sxs-lookup"><span data-stu-id="d4367-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="d4367-124">Poniższy kod ilustruje, włączanie Udostępnianie portów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d4367-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="d4367-125">Rozpoczyna wystąpienia `ICalculator` usługi na stały port o losowy ścieżka identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d4367-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="d4367-126">Mimo że dwie usługi mogą współużytkować tego samego portu, ich ogólną adresy punktów końcowych nadal musi być unikatowa, aby Usługa udostępniania portów NetTcp rozesłać komunikaty do odpowiedniej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4367-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  
  
```  
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```  
  
 <span data-ttu-id="d4367-127">Udostępnianie portów jest włączona, umożliwia uruchamianie usługi wiele razy bez konfliktu przez numer portu.</span><span class="sxs-lookup"><span data-stu-id="d4367-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="d4367-128">Jeśli zmienisz kod, aby wyłączyć udostępnianie portów uruchamiania dwie kopie wyników usługi w drugim Niepowodzenie z <xref:System.ServiceModel.AddressAlreadyInUseException>.</span><span class="sxs-lookup"><span data-stu-id="d4367-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="d4367-129">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="d4367-129">Running the Sample</span></span>  
 <span data-ttu-id="d4367-130">Klient testowy służy do sprawdzania, czy komunikaty są poprawnie kierowane do usługi udostępniania portów.</span><span class="sxs-lookup"><span data-stu-id="d4367-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  
  
```  
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```  
  
 <span data-ttu-id="d4367-131">Każde wystąpienie usługi drukowania jego unikatowy numer oraz adres.</span><span class="sxs-lookup"><span data-stu-id="d4367-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="d4367-132">Na przykład może zostać wyświetlony następujący tekst po uruchomieniu service.exe.</span><span class="sxs-lookup"><span data-stu-id="d4367-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="d4367-133">Wprowadź numer usługi widocznej w tym miejscu po uruchomieniu client.exe.</span><span class="sxs-lookup"><span data-stu-id="d4367-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="d4367-134">W tym przykładzie można uruchomić w konfiguracji między komputerami, zmieniając wygenerowany adres używany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="d4367-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="d4367-135">W Client.cs Zmień ciąg formatu adresu punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="d4367-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="d4367-136">Zamień wszystkie odwołania do "localhost" adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="d4367-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="d4367-137">Po wprowadzeniu tej zmiany, należy ponownie skompilować próbki.</span><span class="sxs-lookup"><span data-stu-id="d4367-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4367-138">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d4367-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d4367-139">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d4367-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="d4367-140">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4367-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="d4367-141">Włącz NetTcp usługi udostępniania portów jak opisano wcześniej w sekcji wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="d4367-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="d4367-142">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4367-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="d4367-143">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4367-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="d4367-144">Szczegółowe informacje dotyczące uruchamiania tego przykładu znajdują się wcześniej w działaniu sekcji przykładowe.</span><span class="sxs-lookup"><span data-stu-id="d4367-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4367-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4367-145">See Also</span></span>