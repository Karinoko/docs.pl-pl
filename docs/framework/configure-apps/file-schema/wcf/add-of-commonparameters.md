---
title: '&lt;add&gt; w &lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbdc3b87b0b501ffdbe2d6b16d59e86659b27585
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="69f04-102">&lt;add&gt; w &lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="69f04-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="69f04-103">Określa pary nazwa wartość parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="69f04-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="69f04-104">Zazwyczaj ten parametr zawiera parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.</span><span class="sxs-lookup"><span data-stu-id="69f04-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="69f04-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="69f04-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="69f04-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="69f04-106">\<behaviors></span></span>  
<span data-ttu-id="69f04-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="69f04-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="69f04-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="69f04-108">\<behavior></span></span>  
<span data-ttu-id="69f04-109">\<Obiekt workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="69f04-109">\<workflowRuntime></span></span>  
<span data-ttu-id="69f04-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="69f04-110">\<commonParameters></span></span>  
<span data-ttu-id="69f04-111">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="69f04-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f04-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="69f04-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69f04-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69f04-113">Attributes and Elements</span></span>  
 <span data-ttu-id="69f04-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69f04-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69f04-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69f04-115">Attributes</span></span>  
  
|<span data-ttu-id="69f04-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69f04-116">Attribute</span></span>|<span data-ttu-id="69f04-117">Opis</span><span class="sxs-lookup"><span data-stu-id="69f04-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69f04-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="69f04-118">name</span></span>|<span data-ttu-id="69f04-119">Nazwa parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="69f04-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="69f04-120">value</span><span class="sxs-lookup"><span data-stu-id="69f04-120">value</span></span>|<span data-ttu-id="69f04-121">Wartość parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="69f04-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69f04-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69f04-122">Child Elements</span></span>  
 <span data-ttu-id="69f04-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="69f04-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69f04-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69f04-124">Parent Elements</span></span>  
  
|<span data-ttu-id="69f04-125">Element</span><span class="sxs-lookup"><span data-stu-id="69f04-125">Element</span></span>|<span data-ttu-id="69f04-126">Opis</span><span class="sxs-lookup"><span data-stu-id="69f04-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69f04-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="69f04-127">\<commonParameters></span></span>](http://msdn.microsoft.com/en-us/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="69f04-128">Kolekcja wspólnych parametrów używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="69f04-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="69f04-129">Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.</span><span class="sxs-lookup"><span data-stu-id="69f04-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f04-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69f04-130">Remarks</span></span>  
 <span data-ttu-id="69f04-131">`<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="69f04-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="69f04-132">Dla usług, które zatwierdzania pracy wsadów magazynów trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, można włączyć je ponowić próbę ich transakcji przy użyciu `EnableRetries` parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="69f04-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="69f04-133">Zwróć uwagę, że `EnableRetries` parametru można ustawić albo globalną (jak pokazano w *CommonParameters* sekcji) lub dla poszczególnych usług obsługujące `EnableRetries` (jak pokazano w *usług*sekcji).</span><span class="sxs-lookup"><span data-stu-id="69f04-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="69f04-134">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="69f04-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69f04-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="69f04-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69f04-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69f04-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="69f04-137">Pliki konfiguracji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="69f04-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="69f04-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="69f04-138">\<commonParameters></span></span>](http://msdn.microsoft.com/en-us/d0e1e6fc-985a-4713-b7da-194e30dfab4c)