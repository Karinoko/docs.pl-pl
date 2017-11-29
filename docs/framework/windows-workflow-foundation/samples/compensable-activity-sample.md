---
title: "Przykładowe działanie compensable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8d7fb5650a8927016e0deebc07a68a8145496db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="99380-102">Przykładowe działanie compensable</span><span class="sxs-lookup"><span data-stu-id="99380-102">Compensable Activity Sample</span></span>
<span data-ttu-id="99380-103">W tym przykładzie przedstawiono sposób użycia `CompensableActivity` działania do definiowania zadań do wykonania dla danej akcji podczas wykonywania normalnych i pracy, które są niezbędne do wykonania tej akcji, odpowiednio w razie potrzeby w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="99380-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="99380-104">Pierwsza część próbki pokazuje, jak można zdefiniować jednostki pracy compensable w [!INCLUDE[wf](../../../../includes/wf-md.md)] przy użyciu `CompensableActivity` działania i jak są wykonywane w przebiegu powiodło się.</span><span class="sxs-lookup"><span data-stu-id="99380-104">The first part of the sample shows how units of compensable work can be defined in [!INCLUDE[wf](../../../../includes/wf-md.md)] using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="99380-105">Druga część próbki pokazuje, jak tej samej jednostki pracy compensable automatycznie zajmie się kompensacji gdy nieoczekiwane zdarzenie zostaje trafiony i wystąpienia przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="99380-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="99380-106">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="99380-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="99380-107">Za pomocą programu Visual Studio 2010, otwórz CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="99380-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="99380-108">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="99380-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="99380-109">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="99380-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99380-110">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="99380-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="99380-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="99380-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99380-112">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="99380-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99380-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="99380-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`  
  
## <a name="see-also"></a><span data-ttu-id="99380-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99380-114">See Also</span></span>