---
title: 'Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 1b76d21cb4f416aae76e7597ad16cfd45e5b7cad
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210269"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF

Windows Communication Foundation (WCF) pozwala utworzyć usługę, która uwidacznia punkt końcowy sieci Web. Punktów końcowych sieci Web wysyłać dane w formacie JSON lub XML, nie ma żadnych koperty protokołu SOAP. W tym temacie pokazano, jak można uwidocznić punkt końcowy.

> [!NOTE]
> Jedynym sposobem, aby zabezpieczyć punkt końcowy sieci Web jest je ujawnić za pośrednictwem protokołu HTTPS za pomocą zabezpieczeń transportu. Korzystając z zabezpieczeń opartych na komunikat, informacje o zabezpieczeniach zwykle jest umieszczany w nagłówkach protokołu SOAP, a ponieważ komunikaty wysyłane do punktów końcowych SOAP nie zawiera żadnych koperty protokołu SOAP, występuje nigdzie nie można umieścić informacje o zabezpieczeniach i konieczne jest zastosowanie zabezpieczeń transportu.

## <a name="to-create-a-web-endpoint"></a>Aby utworzyć punkt końcowy sieci Web

1. Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołań operacji POST. Można jednak określić metodę HTTP, (na przykład, HEAD, PUT lub DELETE), aby zamapować na operację, określając "metoda =" parametru. <xref:System.ServiceModel.Web.WebGetAttribute> nie ma "metoda =" parametr i tylko mapy GET wywołania operacji usługi.

2. Implementowanie kontraktu usługi.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Do obsługi usługi

1. Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.Description.WebHttpBehavior>.

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Jeśli nie zostanie dodany punkt końcowy <xref:System.ServiceModel.Web.WebServiceHost> automatycznie tworzy domyślny punkt końcowy. <xref:System.ServiceModel.Web.WebServiceHost> dodaje także <xref:System.ServiceModel.Description.WebHttpBehavior> i wyłącza stronę pomocy protokołu HTTP i funkcje GET usługi sieci Web Services Description Language (WSDL), więc punkt końcowy metadanych nie kolidują z domyślnego punktu końcowego HTTP.
    >
    >  Dodawanie punktu końcowego bez protokołu SOAP z adresem URL "" powoduje, że nieoczekiwane zachowanie podczas próby wywołania operacji w punkcie końcowym. Przyczyną tego jest nasłuchiwania, którego identyfikator URI punktu końcowego jest taki sam jak identyfikator URI strony pomocy (strona jest wyświetlana, gdy możesz przejść pod adres podstawowy usługi WCF).

     Możesz wykonać jedną z następujących czynności, aby temu zapobiec:

    - Zawsze określać identyfikator URI nie jest pusty dla punktu końcowego protokołem SOAP.

    - Wyłącz strony pomocy. Można to zrobić, używając następującego kodu:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Otworzyć hosta usługi i zaczekaj, aż użytkownik naciśnie klawisz ENTER.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Niniejszy przykład pokazuje, jak hostować usługi stylu sieci Web za pomocą aplikacji konsoli. Możesz również hostować usługi w ramach usług IIS. Aby to zrobić, należy określić <xref:System.ServiceModel.Activation.WebServiceHostFactory> klasy w pliku SVC, tak jak pokazano w poniższym kodzie.

    ```
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Do wywołania operacji usługi mapowane na GET w programie Internet Explorer

1. Otwórz program Internet Explorer i wpisz "`http://localhost:8000/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER. Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/`), adres względny punktu końcowego (""), operacja usługi do wywołania ("EchoWithGet") i znak zapytania, a następnie listę nazwanych parametrów rozdzielone handlowe "i" (&).

## <a name="to-call-service-operations-in-code"></a>Do wywołania operacji usługi w kodzie

1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.ChannelFactory%601> w ramach `using` bloku.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego <xref:System.ServiceModel.ChannelFactory%601> wywołania.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Utwórz kanał i wywołania tej usługi.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Zamknij <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Przykład

Oto pełny kod dla tego przykładu.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Podczas kompilowania odwołanie Service.cs System.ServiceModel.dll i System.ServiceModel.Web.dll.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)