---
title: '&lt;Stany&gt; z &lt;activityStateQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ee98263f43d9557d0ee81484ff8550f0e927ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a><span data-ttu-id="25a21-102">&lt;Stany&gt; z &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="25a21-102">&lt;states&gt; of &lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="25a21-103">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="25a21-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="25a21-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="25a21-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="25a21-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="25a21-105">\<system.serviceModel></span></span>  
<span data-ttu-id="25a21-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="25a21-106">\<tracking></span></span>  
<span data-ttu-id="25a21-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="25a21-107">\<trackingProfile></span></span>  
<span data-ttu-id="25a21-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="25a21-108">\<workflow></span></span>  
<span data-ttu-id="25a21-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="25a21-109">\<activityStateQueries></span></span>  
<span data-ttu-id="25a21-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="25a21-110">\<activityStateQuery></span></span>  
<span data-ttu-id="25a21-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="25a21-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a21-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="25a21-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25a21-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25a21-113">Attributes and Elements</span></span>  
 <span data-ttu-id="25a21-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25a21-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25a21-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25a21-115">Attributes</span></span>  
 <span data-ttu-id="25a21-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="25a21-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25a21-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25a21-117">Child Elements</span></span>  
  
|<span data-ttu-id="25a21-118">Element</span><span class="sxs-lookup"><span data-stu-id="25a21-118">Element</span></span>|<span data-ttu-id="25a21-119">Opis</span><span class="sxs-lookup"><span data-stu-id="25a21-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25a21-120">\<Stan ></span><span class="sxs-lookup"><span data-stu-id="25a21-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="25a21-121">Element konfiguracji zawiera stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="25a21-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25a21-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25a21-122">Parent Elements</span></span>  
  
|<span data-ttu-id="25a21-123">Element</span><span class="sxs-lookup"><span data-stu-id="25a21-123">Element</span></span>|<span data-ttu-id="25a21-124">Opis</span><span class="sxs-lookup"><span data-stu-id="25a21-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25a21-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="25a21-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="25a21-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25a21-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="25a21-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="25a21-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25a21-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25a21-128">Remarks</span></span>  
 <span data-ttu-id="25a21-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="25a21-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="25a21-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="25a21-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="25a21-131">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="25a21-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="25a21-132">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="25a21-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25a21-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25a21-133">See Also</span></span>  
 <span data-ttu-id="25a21-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="25a21-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="25a21-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="25a21-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="25a21-136">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="25a21-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="25a21-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="25a21-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)