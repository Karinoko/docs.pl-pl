---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a5ab416dc484dddc0b6aa0ec25757921815c723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="b26b1-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="b26b1-102">OverloadGroups</span></span>
<span data-ttu-id="b26b1-103">W tym przykładzie składa się z działania (`CreateLocation`), który ma dwie właściwości interesujące:</span><span class="sxs-lookup"><span data-stu-id="b26b1-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="b26b1-104">Niektóre wymagane jej argumentów i niektóre z nich opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b26b1-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="b26b1-105">Pozwala użytkownikowi na wybranie zapewnienie jeden z dwóch różnych zestawów argumentów.</span><span class="sxs-lookup"><span data-stu-id="b26b1-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="b26b1-106">Te zachowania, są wykonywane za pomocą te dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="b26b1-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="b26b1-107">`[isRequired]`weryfikuje, że właściwość określonego działania jest przypisywanie, a jeśli nie, zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b26b1-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="b26b1-108">`[OverloadGroup]`umieszcza razem zestaw argumentów, dzięki czemu można wybrać za pomocą jednego zestawu, lub inny użytkownik działania.</span><span class="sxs-lookup"><span data-stu-id="b26b1-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="b26b1-109">Użytkownik nie można używać argumentów z różnych grup przeciążenia, w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="b26b1-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="b26b1-110">Po skonfigurowaniu różnych przepływów pracy, należy wywołać <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> co powoduje zwrócenie <xref:System.Activities.Validation.ValidationResults> Kolekcja <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation`.</span><span class="sxs-lookup"><span data-stu-id="b26b1-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation`.</span></span> <span data-ttu-id="b26b1-111">Drukuj <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation` obiekty do konsoli.</span><span class="sxs-lookup"><span data-stu-id="b26b1-111">Print the <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation` objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b26b1-112">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b26b1-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b26b1-113">Otwórz **OverloadGroups.sln** przykładowe rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b26b1-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b26b1-114">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b26b1-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b26b1-115">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b26b1-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b26b1-116">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b26b1-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b26b1-117">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b26b1-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b26b1-118">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b26b1-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`  
  
## <a name="see-also"></a><span data-ttu-id="b26b1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b26b1-119">See Also</span></span>