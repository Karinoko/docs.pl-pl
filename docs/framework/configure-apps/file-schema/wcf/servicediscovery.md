---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c371455767b912bd124c2207a1cc29b8ead71cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="80894-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="80894-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="80894-103">Określa wykrywalność usługi punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="80894-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="80894-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="80894-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80894-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="80894-105">\<behaviors></span></span>  
<span data-ttu-id="80894-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="80894-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="80894-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="80894-107">\<behavior></span></span>  
<span data-ttu-id="80894-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="80894-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80894-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="80894-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80894-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80894-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80894-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80894-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80894-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80894-112">Attributes</span></span>  
 <span data-ttu-id="80894-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="80894-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80894-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80894-114">Child Elements</span></span>  
  
|<span data-ttu-id="80894-115">Element</span><span class="sxs-lookup"><span data-stu-id="80894-115">Element</span></span>|<span data-ttu-id="80894-116">Opis</span><span class="sxs-lookup"><span data-stu-id="80894-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80894-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="80894-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="80894-118">Kolekcja punktów końcowych powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="80894-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="80894-119">Ta sekcja umożliwia określenie punktów końcowych na potrzeby wysyłania wiadomości powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="80894-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="80894-120">\<obiektu discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="80894-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="80894-121">Kolekcja odnajdywania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="80894-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="80894-122">Ta sekcja umożliwia określenie punktów końcowych do nasłuchiwania dla komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="80894-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80894-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80894-123">Parent Elements</span></span>  
  
|<span data-ttu-id="80894-124">Element</span><span class="sxs-lookup"><span data-stu-id="80894-124">Element</span></span>|<span data-ttu-id="80894-125">Opis</span><span class="sxs-lookup"><span data-stu-id="80894-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80894-126">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="80894-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="80894-127">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="80894-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80894-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80894-128">Remarks</span></span>  
 <span data-ttu-id="80894-129">Po dodaniu do konfiguracji zachowania usługi, ten element konfiguracji, że wszystkie punkty końcowe usługi wykrywania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="80894-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="80894-130">Można dodatkowo skonfigurować funkcji odnajdywania takich punktów końcowych przy użyciu [ \<obiektu discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) lub [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="80894-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="80894-131">Użyj [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) sekcji, aby skonfigurować anonsów, określając konfiguracji punktu końcowego, który ma być używana do wysyłania anonsów usługi (online/Hello i offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="80894-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="80894-132">Użyj [ \<obiektu discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) sekcji, aby ręcznie określić punkt końcowy do nasłuchiwania dla komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="80894-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80894-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="80894-133">Example</span></span>  
 <span data-ttu-id="80894-134">W poniższym przykładzie konfiguracja Określa, że CalculatorService być wykrywalny i opcjonalnie określa punkt końcowy powiadomienia do użycia.</span><span class="sxs-lookup"><span data-stu-id="80894-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
  ...  
  </service>  
</services>  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="udpEndpoint"  
                        kind="udpAnnouncementEndpoint" />  
        </announcementEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80894-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80894-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>