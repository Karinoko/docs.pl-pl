---
title: 'Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 146b3bba3a880c780644eecd277827823793b5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515308"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Funkcje lepszą integrację usług sieci web i przepływów pracy w formularzu tworzenia pierwszej kontraktu przepływu pracy. Narzędzie do projektowania przepływu pracy pierwszy kontraktu pozwala na projektowanie najpierw kontraktu w kodzie. Narzędzie następnie automatycznie generuje szablon czynności w przyborniku operacji w umowie.  
  
> [!NOTE]
>  Ten temat zawiera wskazówki krok po kroku dotyczące tworzenia usługi przepływu pracy pierwszy kontraktu. Aby uzyskać więcej informacji na temat przepływu pracy pierwszy kontraktu usługi programowanie zobacz [kontraktu pierwszego tworzenia usługi przepływu pracy](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>Tworzenie projektu przepływu pracy  
  
1.  W programie Visual Studio, wybierz **pliku**, **nowy projekt**. Wybierz **WCF** węźle **C#** w węźle **szablony** drzewa, a następnie wybierz **aplikacji usługi przepływu pracy WCF** szablonu.  
  
2.  Nazwa nowego projektu `ContractFirst` i kliknij przycisk **Ok**.  
  
### <a name="creating-the-service-contract"></a>Tworzenie kontraktu usługi  
  
1.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** . Wybierz **kod** węźle po lewej stronie oraz **klasy** szablonu po prawej stronie. Nazwa nowej klasy `IBookService` i kliknij przycisk **Ok**.  
  
2.  W górnej części okna kodu, który pojawia się, Dodaj instrukcję Using `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Zmień definicję klasy próbki do następujących definicji interfejsu.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  Tworzenie projektu przez naciśnięcie przycisku **Ctrl + Shift + B**.  
  
### <a name="importing-the-service-contract"></a>Importowanie kontraktu usługi  
  
1.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **kontraktu usługi Import**. W obszarze  **\<bieżącego projektu >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**.  
  
2.  Zostanie otwarte okno dialogowe informujący, że operacja zakończyła się pomyślnie, a wygenerowanego działania będzie wyświetlana w przyborniku po utworzeniu projektu. Kliknij przycisk **OK**.  
  
3.  Tworzenie projektu przez naciśnięcie przycisku **Ctrl + Shift + B**, dzięki czemu importowanych działania zostanie wyświetlony w przyborniku.  
  
4.  W **Eksploratora rozwiązań**, otwórz Service1.xamlx. Usługi przepływu pracy będą wyświetlane w projektancie.  
  
5.  Wybierz **sekwencji** działania. Kliknij w oknie właściwości **...** przycisk **ImplementedContract** właściwości. W **edytora kolekcji typu** okno zostanie wyświetlone, kliknij przycisk **typu** listy rozwijanej i wybierz **Przeglądaj w poszukiwaniu typów...** wpis. W **Przeglądaj i wybierz .net typ** okna dialogowego, w obszarze  **\<bieżącego projektu >**, otwórz wszystkie węzły podrzędne i wybierz **IBookService**. Kliknij przycisk **OK**. W **edytora kolekcji typu** okna dialogowego, kliknij przycisk **OK**.  
  
6.  Wybierz i Usuń **ReceiveRequest** i **SendResponse** działań.  
  
7.  Przeciągnij z przybornika, **Buy_ReceiveAndSendReply** i **Checkout_Receive** działania na **usługa Sekwencyjna** działania.
