---
title: '&lt;sendMessageChannelCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1543142a8ff5fb77db48d0e479433c533e7eff83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsendmessagechannelcachegt"></a><span data-ttu-id="b768c-102">&lt;sendMessageChannelCache&gt;</span><span class="sxs-lookup"><span data-stu-id="b768c-102">&lt;sendMessageChannelCache&gt;</span></span>
<span data-ttu-id="b768c-103">Zachowanie usługi umożliwiające dostosowywanie udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi przy użyciu działań dotyczących komunikatów wysyłania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b768c-103">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="b768c-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b768c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b768c-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b768c-105">\<behaviors></span></span>  
<span data-ttu-id="b768c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b768c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b768c-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b768c-107">\<behavior></span></span>  
<span data-ttu-id="b768c-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="b768c-108">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b768c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b768c-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b768c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b768c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b768c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b768c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b768c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b768c-112">Attributes</span></span>  
  
|<span data-ttu-id="b768c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b768c-113">Attribute</span></span>|<span data-ttu-id="b768c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b768c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b768c-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="b768c-115">allowUnsafeCaching</span></span>|<span data-ttu-id="b768c-116">Wartość logiczna, która wskazuje, czy należy włączyć buforowanie.</span><span class="sxs-lookup"><span data-stu-id="b768c-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="b768c-117">Jeśli usługa przepływu pracy ma powiązań niestandardowe lub niestandardowe zachowania, buforowanie może być niebezpieczne i dlatego jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="b768c-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="b768c-118">Jednak jeśli chcesz włączyć buforowanie na wartość tej właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="b768c-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b768c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b768c-119">Child Elements</span></span>  
  
|<span data-ttu-id="b768c-120">Element</span><span class="sxs-lookup"><span data-stu-id="b768c-120">Element</span></span>|<span data-ttu-id="b768c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b768c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b768c-122">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="b768c-122">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="b768c-123">Określa ustawienia pamięci podręcznej kanału.</span><span class="sxs-lookup"><span data-stu-id="b768c-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="b768c-124">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="b768c-124">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="b768c-125">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="b768c-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b768c-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b768c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b768c-127">Element</span><span class="sxs-lookup"><span data-stu-id="b768c-127">Element</span></span>|<span data-ttu-id="b768c-128">Opis</span><span class="sxs-lookup"><span data-stu-id="b768c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b768c-129">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b768c-129">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b768c-130">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="b768c-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b768c-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b768c-131">Remarks</span></span>  
 <span data-ttu-id="b768c-132">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="b768c-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="b768c-133">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b768c-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b768c-134">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="b768c-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="b768c-135">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="b768c-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="b768c-136">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b768c-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="b768c-137">jak zmienić domyślne pamięci podręcznej udostępnianie poziomów i ustawienia dla fabryki kanałów i pamięci podręcznej kanału pamięci podręcznej, zobacz [Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="b768c-137"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b768c-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="b768c-138">Example</span></span>  
 <span data-ttu-id="b768c-139">W usłudze hostowanej przepływu pracy można określić fabrykę pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b768c-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="b768c-140">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="b768c-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="b768c-141">W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera **MyChannelCacheBehavior** zachowania usługi przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="b768c-141">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="b768c-142">To zachowanie usługi zostanie dodany do usługi za pośrednictwem **behaviorConfiguarion** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b768c-142">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b768c-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b768c-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 [<span data-ttu-id="b768c-144">Poziomy zmiana współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="b768c-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)