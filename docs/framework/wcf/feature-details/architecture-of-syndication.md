---
title: Architektura syndykacji
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: f0a6b288860c343157f31f74d5a461fad1784e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492822"
---
# <a name="architecture-of-syndication"></a>Architektura syndykacji
Interfejs API zespolonego umożliwia model programowania niezależny od formatu, który umożliwia zawartości zespolonej do zapisania do przesyłania w różnych formatach. Model danych abstrakcyjny składa się z następujących klas:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Te klasy mapowania ściśle konstrukcje specyfikacją Atom 1.0, mimo że niektóre nazwy są różne.  
  
 W konsoli Windows Communication Foundation (WCF) zespolonego źródła danych są modelowane jako inny rodzaj operacji usługi, co typ zwracany w przypadku jednej z klas pochodnych <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Pobieranie źródło danych ma formę wymiany komunikatów żądań i odpowiedzi. Klient wysyła żądanie do usługi i usługa odpowiada. Komunikat żądania ma wartość protokołu infrastruktury (na przykład HTTP raw) i komunikat odpowiedzi zawiera ładunek, która składa się z formatu często rozpoznawanych syndication (RSS 2.0 i Atom 1.0). Usługi, które implementuje te wymiany komunikatów są określane jako usługi zespolonego.  
  
 Kontrakt usługi zespolonego zawiera zestaw działań, które zwraca wystąpienie klasy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> klasy. W poniższym przykładzie pokazano deklaracji interfejsu usługi zespolonego.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Obsługa zespolonego bazuje na Model programowania interfejsu REST usługi WCF, który definiuje <xref:System.ServiceModel.WebHttpBinding> powiązania, który jest używany w połączeniu z <xref:System.ServiceModel.Description.WebHttpBehavior> udostępnić źródła danych jako usługi. Aby uzyskać więcej informacji na temat Model programowania interfejsu REST usługi WCF, zobacz [programowania omówienie modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Specyfikacja Atom 1.0 umożliwia sekund ułamkowa należy określić w jednym z jego konstrukcji daty. Podczas serializowania i deserializowania implementacji WCF ignoruje ułamkowych części sekundy.  
  
## <a name="object-model"></a>Model obiektu  
 Model obiektów dla zespolonego składa się z grup klas w poniższych tabelach.  
  
 Formatowanie klasy:  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> wystąpienie do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> klas pochodnych do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpienie do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> klas pochodnych do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> wystąpienia w formacie RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> klas pochodnych w formacie RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpienia w formacie RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> klas pochodnych w formacie RSS 2.0.|  
  
 Klasy modelu obiektu:  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Klasa, która reprezentuje kategorię zespolonego źródła danych.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Klasa podstawowa reprezentuje zawartość zespolonego.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Klasa, która stanowi rozszerzenie elementu zespolonego.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Kolekcja <xref:System.ServiceModel.Syndication.SyndicationElementExtension> obiektów.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Klasa, która reprezentuje obiekt źródła najwyższego poziomu.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Klasa reprezentująca element źródła.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Klasa, która reprezentuje łącze w zespolonego źródła danych lub elementów.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Klasa, która reprezentuje konstrukcję osoby Atom.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Klasa, która reprezentuje zespolonego obsługiwanych wersji protokołu.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Klasa reprezentująca żadnego <xref:System.ServiceModel.Syndication.SyndicationItem> zawartości ma być wyświetlony dla użytkownika końcowego.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Wyliczenie reprezentuje różne rodzaje zespolonego tekst zawartości obsługiwane.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Klasa, która reprezentuje zespolonego zawartość, która składa się z adresu URL do innego zasobu.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Klasa, która reprezentuje zespolonego zawartość, która nie ma być wyświetlany w przeglądarce.|  
  
 Podstawowe abstrakcje danych w modelu obiektów są źródła danych i elementów, które odpowiadają <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klasy. Źródło danych przedstawia niektóre metadanych źródła danych na poziomie (na przykład tytuł, opis i autor), lokalizację do przechowywania nieznane rozszerzenia i zestaw elementów, które tworzą reszty źródła informacji o zawartości. Element udostępnia niektóre metadane poziomie elementu (na przykład tytuł, podsumowanie i PublicationDate), lokalizację do przechowywania nieznane rozszerzenia i zawartość elementu zawierającego pozostałej części zawartość elementu informacji. Abstrakcje podstawowe źródło danych, a element są obsługiwane przez dodatkowe klasy, które reprezentują typowe konstrukcje danych przywoływany w specyfikacji Atom 1.0 i RSS.  
  
 Informacje w wystąpienia źródła danych może zostać przekonwertowany do szerokiej gamy formatów XML. Proces konwersji do i z pliku XML jest zarządzana przez <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> klasy. Ta klasa jest abstrakcyjna; implementacje konkretnych są udostępniane dla Atom 1.0 i RSS 2.0 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Aby używać klasy pochodne źródła danych, użyj <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> lub <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> zgodnie z ich zezwala na określanie klasy pochodnej źródła danych. Aby użyć klasy pochodnej elementu Użyj albo <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> lub <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> jako pozwala użytkownikowi na określenie klasy pochodnej elementu trzecich mogą dziedziczyć realizacji <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> do obsługi zespolonego różne formaty.  
  
## <a name="extensibility"></a>Rozszerzalność  
  
-   Kluczowy element zespolony protokołów jest rozszerzalności. Zarówno Atom 1.0 i RSS 2.0 umożliwiają dodawanie atrybuty i elementy do zespolonego źródła danych, które nie są zdefiniowane w specyfikacji. Model programowania syndykacji WCF udostępnia dwa sposoby pracy z atrybutów niestandardowych i rozszerzenia: wyprowadzanie nową klasą a typowaniem luźnym dostępu. Aby uzyskać więcej informacji, zobacz [rozszerzalność syndykacji](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
