---
title: Usługi aplikacji klienta
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d58510240593f73ff761aa669035f28598006c10
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522003"
---
# <a name="client-application-services"></a>Usługi aplikacji klienta
Usługi aplikacji klienta ułatwiają tworzenie aplikacji Windows, które używają [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] logowania, ról i profilu usługi aplikacji w ramach rozszerzenia AJAX programu Microsoft ASP.NET 2.0. Te usługi umożliwiają wielu sieci Web i aplikacji opartych na Windows, aby udostępnić funkcje zarządzania użytkownikami z jednego serwera i informacji o użytkowniku. Na przykład możesz korzystać z tych usług do wykonywania następujących zadań:  
  
-   Uwierzytelnienia użytkownika. Usługa uwierzytelniania można użyć do zweryfikowania tożsamości użytkownika.  
  
-   Określ rolę lub role uwierzytelnionego użytkownika. Usługi ról można użyć do zmiany interfejsu użytkownika aplikacji w taki sposób, w zależności od roli użytkownika. Na przykład możesz podać dodatkowe funkcje dla użytkowników, którzy znajdują się w roli administratora.  
  
-   Store i dostępu dla użytkownika ustawienia aplikacji znajdujących się na serwerze. Usługa ustawień sieci Web (znany także jako usługa profilu) umożliwia współużytkowanie ustawień przez wiele aplikacji i lokalizacji.  
  
 Usługi aplikacji klienta zalet modelu rozszerzalności usługi sieci Web za pośrednictwem dostawców usług klienta, które można określić w plikach konfiguracji aplikacji. Ci dostawcy usług obejmują funkcje w trybie offline, które korzysta z lokalnej pamięci podręcznej do uwierzytelniania, ról i ustawienia danych, gdy połączenie sieciowe jest niedostępne.  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi aplikacji, zobacz [przegląd usług aplikacji ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 W tym artykule opisano funkcje dostępne za pośrednictwem dostawców usług aplikacji klienta.  
  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 W tym artykule opisano sposób używania projektanta projektu programu Visual Studio, aby włączyć i konfiguracji aplikacji usługi. Opisano również odpowiednie zmiany do pliku App.config.  
  
 [Instrukcje: implementowanie logowania użytkownika przy użyciu usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Opisuje sposób sprawdzania poprawności użytkownika, gdy aplikacja jest skonfigurowana do używania dostawcy usług uwierzytelniania klienta.  
  
 [Przewodnik: używanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 W tym artykule opisano sposób łączenia wszystkich funkcji usług aplikacji klienckich w jednej aplikacji. Ten przewodnik zawiera wskazówki dotyczące end-to-end. Na przykład zawiera instrukcje dotyczące sposobu tworzenia aplikacji usługi sieci Web platformy ASP.NET, używanej do testowania usług aplikacji klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie usług aplikacji ASP.NET](https://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Korzystanie z uwierzytelniania formularzy z Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Korzystając z informacji ról przy użyciu Microsoft Ajax](https://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Przy użyciu informacji o profilu z Microsoft Ajax](https://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Uwierzytelnianie ASP.NET](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Zarządzanie przy użyciu ról autoryzacji](https://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md)
