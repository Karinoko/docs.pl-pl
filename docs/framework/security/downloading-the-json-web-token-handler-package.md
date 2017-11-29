---
title: "Pobieranie pakietu programu obsługi tokenów sieci Web JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="469c3-102">Pobieranie pakietu programu obsługi tokenów sieci Web JSON</span><span class="sxs-lookup"><span data-stu-id="469c3-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="469c3-103">W tym temacie omówiono sposób pobierania i używania programu obsługi tokenów sieci Web JSON w projekcie.</span><span class="sxs-lookup"><span data-stu-id="469c3-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="469c3-104">Pobieranie programu obsługi tokenów sieci Web JSON</span><span class="sxs-lookup"><span data-stu-id="469c3-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="469c3-105">Rozszerzenia JSON programu obsługi tokenów sieci Web jest dostępna jako pakietu NuGet, który dodaje konieczne zestawy, a odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="469c3-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="469c3-106">Jeśli nie masz już zainstalowany NuGet, przejdź do [nuget.org](http://nuget.org) go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="469c3-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="469c3-107">Widać Historia wersji rozszerzenia odwiedzając jej stronę na NuGet: [obsługi tokenów sieci Web JSON na NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="469c3-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="469c3-108">Pobieranie programu obsługi tokenów sieci Web JSON przy użyciu graficznego interfejsu użytkownika Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="469c3-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="469c3-109">W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="469c3-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="469c3-110">W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `JWT Token Handler` i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="469c3-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="469c3-111">W okienku wyników kliknij **zainstalować** przycisku do pierwszego wyniku.</span><span class="sxs-lookup"><span data-stu-id="469c3-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="469c3-112">Pakiet zostanie rozpocząć pobieranie.</span><span class="sxs-lookup"><span data-stu-id="469c3-112">The package will begin downloading.</span></span> <span data-ttu-id="469c3-113">Przed dodaniem jej do projektu, pojawi się okno dialogowe akceptacji licencji.</span><span class="sxs-lookup"><span data-stu-id="469c3-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="469c3-114">Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.</span><span class="sxs-lookup"><span data-stu-id="469c3-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="469c3-115">Najnowsze zestawów programu obsługi tokenów sieci Web JSON zostanie pobrany i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="469c3-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="469c3-116">Pobieranie programu obsługi tokenów sieci Web JSON przy użyciu konsoli Menedżera pakietów</span><span class="sxs-lookup"><span data-stu-id="469c3-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="469c3-117">W programie Visual Studio, kliknij przycisk **narzędzia**, **Menedżer pakietów biblioteki**, a następnie **Konsola Menedżera pakietów**.</span><span class="sxs-lookup"><span data-stu-id="469c3-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="469c3-118">**Konsola Menedżera pakietów** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="469c3-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="469c3-119">Wprowadź poniższy tekst i naciśnij klawisz **Enter**:</span><span class="sxs-lookup"><span data-stu-id="469c3-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="469c3-120">Najnowsze zestawów programu obsługi tokenów sieci Web JSON zostanie pobrany i dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="469c3-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>