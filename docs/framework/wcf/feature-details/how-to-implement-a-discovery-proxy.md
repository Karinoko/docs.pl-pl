---
title: "Instrukcje: Wdrażanie serwera proxy odnajdywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d3c4dd0ec54334cb59b8cc896ddcd9fcc6af482e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="79bb4-102">Instrukcje: Wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="79bb4-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="79bb4-103">W tym temacie opisano sposób wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-103">This topic explains how to implement a discovery proxy.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79bb4-104">Funkcja odnajdowania w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], zobacz [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="79bb4-104"> the discovery feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="79bb4-105">Serwera proxy odnajdywania może być zaimplementowany przez klasę, która rozszerza tworzenie <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="79bb4-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="79bb4-106">Istnieje wiele innych klas pomocy technicznej zdefiniowany i używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="79bb4-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="79bb4-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, i `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="79bb4-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="79bb4-108">Implementuje te klasy <xref:System.IAsyncResult> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="79bb4-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="79bb4-109"><xref:System.IAsyncResult> zobacz [System.IAsyncResult interfejsu](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="79bb4-109"> <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>
  
 <span data-ttu-id="79bb4-110">Wdrażanie serwera proxy odnajdywania dzieli się na trzy główne części w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="79bb4-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>  
  
-   <span data-ttu-id="79bb4-111">Definiowanie klasy, która zawiera magazyn danych i rozszerza klasy abstrakcyjnej <xref:System.ServiceModel.Discovery.DiscoveryProxy> klasy.</span><span class="sxs-lookup"><span data-stu-id="79bb4-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>  
  
-   <span data-ttu-id="79bb4-112">Implementowanie Pomocnika `AsyncResult` klasy.</span><span class="sxs-lookup"><span data-stu-id="79bb4-112">Implement the helper `AsyncResult` class.</span></span>  
  
-   <span data-ttu-id="79bb4-113">Hosta serwera Proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-113">Host the Discovery Proxy.</span></span>  
  
### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="79bb4-114">Aby utworzyć nowy projekt aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="79bb4-114">To create a new console application project</span></span>  
  
1.  <span data-ttu-id="79bb4-115">Uruchom [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79bb4-115">Start [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="79bb4-116">Utwórz nowy projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="79bb4-116">Create a new console application project.</span></span> <span data-ttu-id="79bb4-117">Nazwij projekt `DiscoveryProxy` i nazwa rozwiązania `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="79bb4-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>  
  
3.  <span data-ttu-id="79bb4-118">Dodaj następujące odwołania do projektu</span><span class="sxs-lookup"><span data-stu-id="79bb4-118">Add the following references to the project</span></span>  
  
    1.  <span data-ttu-id="79bb4-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="79bb4-119">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="79bb4-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="79bb4-120">System.Servicemodel.Discovery.dll</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="79bb4-121">Upewnij się, czy odwołania w wersji 4.0 lub nowszej tych zestawów.</span><span class="sxs-lookup"><span data-stu-id="79bb4-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>  
  
### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="79bb4-122">Aby zaimplementować klasy ProxyDiscoveryService</span><span class="sxs-lookup"><span data-stu-id="79bb4-122">To implement the ProxyDiscoveryService class</span></span>  
  
1.  <span data-ttu-id="79bb4-123">Dodaj nowy plik kodu do projektu i nadaj mu nazwę DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="79bb4-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>  
  
2.  <span data-ttu-id="79bb4-124">Dodaj następujące `using` instrukcje DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="79bb4-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using System.Xml;  
    ```  
  
3.  <span data-ttu-id="79bb4-125">Pochodzi `DiscoveryProxyService` z <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="79bb4-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="79bb4-126">Zastosuj `ServiceBehavior` do klasy atrybutu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="79bb4-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>  
  
    ```  
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]  
    public class DiscoveryProxyService : DiscoveryProxy  
    {  
    }  
    ```  
  
4.  <span data-ttu-id="79bb4-127">Wewnątrz `DiscoveryProxy` klasa definiuje słownik do przechowywania zarejestrowanych usług.</span><span class="sxs-lookup"><span data-stu-id="79bb4-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>  
  
    ```  
    // Repository to store EndpointDiscoveryMetadata.   
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;  
    ```  
  
5.  <span data-ttu-id="79bb4-128">Zdefiniuj konstruktora, który inicjuje słownika.</span><span class="sxs-lookup"><span data-stu-id="79bb4-128">Define a constructor that initializes the dictionary.</span></span>  
  
    ```  
    public DiscoveryProxyService()  
            {  
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();  
            }  
    ```  
  
### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="79bb4-129">Aby zdefiniować metody używane do aktualizowania pamięci podręcznej serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="79bb4-129">To define the methods used to update the discovery proxy cache</span></span>  
  
1.  <span data-ttu-id="79bb4-130">Implementowanie `AddOnlineservice` metody nad dodaniem usług do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="79bb4-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="79bb4-131">Jest to zawsze serwer proxy otrzyma komunikat powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="79bb4-131">This is called every time the proxy receives an announcement message.</span></span>  
  
    ```  
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
            {  
                lock (this.onlineServices)  
                {  
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;                  
                }  
  
                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");  
            }  
    ```  
  
2.  <span data-ttu-id="79bb4-132">Implementowanie `RemoveOnlineService` metodę, która służy do usuwania usług z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="79bb4-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>  
  
    ```  
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
            {  
                if (endpointDiscoveryMetadata != null)  
                {  
                    lock (this.onlineServices)  
                    {  
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);                      
                    }  
  
                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");  
                }      
            }  
    ```  
  
3.  <span data-ttu-id="79bb4-133">Implementowanie `MatchFromOnlineService` metody, które będzie próbował dopasować usługi z usługą w słowniku.</span><span class="sxs-lookup"><span data-stu-id="79bb4-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>  
  
    ```  
    void MatchFromOnlineService(FindRequestContext findRequestContext)  
            {  
                lock (this.onlineServices)  
                {  
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                    {  
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))  
                        {  
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);  
                        }  
                    }  
                }  
            }  
    ```  
  
    ```  
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)  
            {  
                EndpointDiscoveryMetadata matchingEndpoint = null;  
                lock (this.onlineServices)  
                {  
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                    {  
                        if (criteria.Address == endpointDiscoveryMetadata.Address)  
                        {  
                            matchingEndpoint = endpointDiscoveryMetadata;  
                        }  
                    }  
                }  
                return matchingEndpoint;  
            }  
    ```  
  
4.  <span data-ttu-id="79bb4-134">Implementowanie `PrintDiscoveryMetadata` metodę, która zapewnia użytkownikowi dostęp do konsoli tekst output, jakie odnajdywania wykonywanie operacji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="79bb4-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>  
  
    ```  
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)  
            {  
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");  
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)  
                {  
                    Console.WriteLine("** " + contractName.ToString());  
                    break;  
                }  
                Console.WriteLine("**** Operation Completed");  
            }  
    ```  
  
5.  <span data-ttu-id="79bb4-135">Dodaj następujące klasy AsyncResult do DiscoveryProxyService.</span><span class="sxs-lookup"><span data-stu-id="79bb4-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="79bb4-136">Te klasy są używane w celu rozróżnienia wyniki różnych operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="79bb4-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>  
  
    ```  
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult  
            {  
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);  
                }  
            }  
  
            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult  
            {  
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);  
                }  
            }  
  
            sealed class OnFindAsyncResult : AsyncResult  
            {  
                public OnFindAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnFindAsyncResult>(result);  
                }  
            }  
  
            sealed class OnResolveAsyncResult : AsyncResult  
            {  
                EndpointDiscoveryMetadata matchingEndpoint;  
  
                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.matchingEndpoint = matchingEndpoint;  
                    this.Complete(true);  
                }  
  
                public static EndpointDiscoveryMetadata End(IAsyncResult result)  
                {  
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);  
                    return thisPtr.matchingEndpoint;  
                }  
            }  
    ```  
  
### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="79bb4-137">Aby zdefiniować metody, które implementuje funkcje serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="79bb4-137">To define the methods that implement the discovery proxy functionality</span></span>  
  
1.  <span data-ttu-id="79bb4-138">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-139">Ta metoda jest wywoływana, gdy serwera proxy odnajdywania odbiera anonse online.</span><span class="sxs-lookup"><span data-stu-id="79bb4-139">This method is called when the discovery proxy receives an online announcement message.</span></span>  
  
    ```  
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy  
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
            {          
                this.AddOnlineService(endpointDiscoveryMetadata);  
                return new OnOnlineAnnouncementAsyncResult(callback, state);  
            }  
    ```  
  
2.  <span data-ttu-id="79bb4-140">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-141">Ta metoda jest wywoływana po zakończeniu serwera proxy odnajdywania przetwarza komunikat powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="79bb4-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>  
  
    ```  
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)  
            {  
                OnOnlineAnnouncementAsyncResult.End(result);  
            }  
    ```  
  
3.  <span data-ttu-id="79bb4-142">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-143">Ta metoda jest wywoływana z odnajdywaniem serwera proxy odbiera komunikat powiadomienia w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="79bb4-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>  
  
    ```  
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy  
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
            {  
                this.RemoveOnlineService(endpointDiscoveryMetadata);  
                return new OnOfflineAnnouncementAsyncResult(callback, state);  
            }  
    ```  
  
4.  <span data-ttu-id="79bb4-144">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-145">Ta metoda jest wywoływana, gdy serwera proxy odnajdywania zakończy przetwarzanie komunikatu powiadomienia w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="79bb4-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>  
  
    ```  
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)  
            {  
                OnOfflineAnnouncementAsyncResult.End(result);  
            }  
    ```  
  
5.  <span data-ttu-id="79bb4-146">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-147">Ta metoda jest wywoływana, gdy serwera proxy odnajdywania odbiera żądanie Znajdź.</span><span class="sxs-lookup"><span data-stu-id="79bb4-147">This method is called when the discovery proxy receives a find request.</span></span>  
  
    ```  
    // OnBeginFind method is called when a Probe request message is received by the Proxy  
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)  
            {  
                this.MatchFromOnlineService(findRequestContext);  
                return new OnFindAsyncResult(callback, state);  
            }  
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)  
    {  
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);  
        return new OnFindAsyncResult(  
                    matchingEndpoints,  
                    callback,  
                    state);  
    }  
    ```  
  
6.  <span data-ttu-id="79bb4-148">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-149">Ta metoda jest wywoływana po zakończeniu serwera proxy odnajdywania przetwarzania żądania wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-149">This method is called when the discovery proxy finishes processing a find request.</span></span>  
  
    ```  
    protected override void OnEndFind(IAsyncResult result)  
            {  
                OnFindAsyncResult.End(result);  
            }  
    ```  
  
7.  <span data-ttu-id="79bb4-150">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-151">Ta metoda jest wywoływana podczas serwera proxy odnajdywania odbiera komunikat Rozwiąż.</span><span class="sxs-lookup"><span data-stu-id="79bb4-151">This method is called when the discovery proxy receives a resolve message.</span></span>  
  
    ```  
    // OnBeginFind method is called when a Resolve request message is received by the Proxy  
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)  
            {  
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);  
            }  
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)  
    {  
        return new OnResolveAsyncResult(  
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),  
            callback,  
            state);  
    }  
    ```  
  
8.  <span data-ttu-id="79bb4-152">Zastąpienie <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="79bb4-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="79bb4-153">Ta metoda jest wywoływana po zakończeniu serwera proxy odnajdywania przetwarza komunikat rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="79bb4-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>  
  
    ```  
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)  
    {  
        return OnResolveAsyncResult.End(result);  
    }  
    ```  
  
 <span data-ttu-id="79bb4-154">OnBegin...</span><span class="sxs-lookup"><span data-stu-id="79bb4-154">The OnBegin..</span></span> <span data-ttu-id="79bb4-155">/ OnEnd...</span><span class="sxs-lookup"><span data-stu-id="79bb4-155">/ OnEnd..</span></span> <span data-ttu-id="79bb4-156">metody udostępniają logiki dla operacji odnajdowania kolejne.</span><span class="sxs-lookup"><span data-stu-id="79bb4-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="79bb4-157">Na przykład <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> i <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> metody implementują logikę Znajdź serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="79bb4-158">Te metody są wykonywane wysyłania odpowiedzi do klienta, serwera proxy odnajdywania odbiera wiadomości sondy.</span><span class="sxs-lookup"><span data-stu-id="79bb4-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="79bb4-159">Logiki Znajdź można zmodyfikować zgodnie z wymaganiami, na przykład można zastosować niestandardowy zakres dopasowania algorytmów lub określonych metadanych XML aplikacji, podczas analizowania w ramach operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>  
  
### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="79bb4-160">Aby zaimplementować klasy AsyncResult</span><span class="sxs-lookup"><span data-stu-id="79bb4-160">To implement the AsyncResult class</span></span>  
  
1.  <span data-ttu-id="79bb4-161">Zdefiniuj abstrakcyjna klasa podstawowa AsyncResult, który jest używany do uzyskania różnych klas wynik asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="79bb4-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>  
  
2.  <span data-ttu-id="79bb4-162">Utwórz nowy plik kodu o nazwie AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="79bb4-162">Create a new code file called AsyncResult.cs.</span></span>  
  
3.  <span data-ttu-id="79bb4-163">Dodaj następujące `using` instrukcje AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="79bb4-163">Add the following `using` statements to AsyncResult.cs.</span></span>  
  
    ```  
    using System;  
    using System.Threading;  
    ```  
  
4.  <span data-ttu-id="79bb4-164">Dodaj następujące klasy AsyncResult.</span><span class="sxs-lookup"><span data-stu-id="79bb4-164">Add the following AsyncResult class.</span></span>  
  
    ```  
    abstract class AsyncResult : IAsyncResult  
        {  
            AsyncCallback callback;  
            bool completedSynchronously;  
            bool endCalled;  
            Exception exception;  
            bool isCompleted;  
            ManualResetEvent manualResetEvent;  
            object state;  
            object thisLock;  
  
            protected AsyncResult(AsyncCallback callback, object state)  
            {  
                this.callback = callback;  
                this.state = state;  
                this.thisLock = new object();  
            }  
  
            public object AsyncState  
            {  
                get  
                {  
                    return state;  
                }  
            }  
  
            public WaitHandle AsyncWaitHandle  
            {  
                get  
                {  
                    if (manualResetEvent != null)  
                    {  
                        return manualResetEvent;  
                    }  
                    lock (ThisLock)  
                    {  
                        if (manualResetEvent == null)  
                        {  
                            manualResetEvent = new ManualResetEvent(isCompleted);  
                        }  
                    }  
                    return manualResetEvent;  
                }  
            }  
  
            public bool CompletedSynchronously  
            {  
                get  
                {  
                    return completedSynchronously;  
                }  
            }  
  
            public bool IsCompleted  
            {  
                get  
                {  
                    return isCompleted;  
                }  
            }  
  
            object ThisLock  
            {  
                get  
                {  
                    return this.thisLock;  
                }  
            }  
  
            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)  
                where TAsyncResult : AsyncResult  
            {  
                if (result == null)  
                {  
                    throw new ArgumentNullException("result");  
                }  
  
                TAsyncResult asyncResult = result as TAsyncResult;  
  
                if (asyncResult == null)  
                {  
                    throw new ArgumentException("Invalid async result.", "result");  
                }  
  
                if (asyncResult.endCalled)  
                {  
                    throw new InvalidOperationException("Async object already ended.");  
                }  
  
                asyncResult.endCalled = true;  
  
                if (!asyncResult.isCompleted)  
                {  
                    asyncResult.AsyncWaitHandle.WaitOne();  
                }  
  
                if (asyncResult.manualResetEvent != null)  
                {  
                    asyncResult.manualResetEvent.Close();  
                }  
  
                if (asyncResult.exception != null)  
                {  
                    throw asyncResult.exception;  
                }  
  
                return asyncResult;  
            }  
  
            protected void Complete(bool completedSynchronously)  
            {  
                if (isCompleted)  
                {  
                    throw new InvalidOperationException("This async result is already completed.");  
                }  
  
                this.completedSynchronously = completedSynchronously;  
  
                if (completedSynchronously)  
                {  
                    this.isCompleted = true;  
                }  
                else  
                {  
                    lock (ThisLock)  
                    {  
                        this.isCompleted = true;  
                        if (this.manualResetEvent != null)  
                        {  
                            this.manualResetEvent.Set();  
                        }  
                    }  
                }  
  
                if (callback != null)  
                {  
                    callback(this);  
                }  
            }  
  
            protected void Complete(bool completedSynchronously, Exception exception)  
            {  
                this.exception = exception;  
                Complete(completedSynchronously);  
            }  
        }  
    ```  
  
### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="79bb4-165">Do obsługi obiektu DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="79bb4-165">To host the DiscoveryProxy</span></span>  
  
1.  <span data-ttu-id="79bb4-166">Otwórz plik Program.cs w projekcie DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="79bb4-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>  
  
2.  <span data-ttu-id="79bb4-167">Dodaj następujące `using` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="79bb4-167">Add the following `using` statements.</span></span>  
  
    ```  
    using System;  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    ```  
  
3.  <span data-ttu-id="79bb4-168">W ramach `Main()` metody, Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="79bb4-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="79bb4-169">Spowoduje to utworzenie wystąpienia `DiscoveryProxy` klasy.</span><span class="sxs-lookup"><span data-stu-id="79bb4-169">This creates an instance of the `DiscoveryProxy` class.</span></span>  
  
    ```  
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
                // Host the DiscoveryProxy service  
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());  
    ```  
  
4.  <span data-ttu-id="79bb4-170">Następnie dodaj następujący kod, aby dodać punkt końcowy odnajdowania i punktu końcowego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="79bb4-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>  
  
    ```  
    try  
              {                  
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages  
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
                  discoveryEndpoint.IsSystemEndpoint = false;  
  
                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages  
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));                  
  
                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);  
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);  
  
                  proxyServiceHost.Open();  
  
                  Console.WriteLine("Proxy Service started.");  
                  Console.WriteLine();  
                  Console.WriteLine("Press <ENTER> to terminate the service.");  
                  Console.WriteLine();  
                  Console.ReadLine();  
  
                  proxyServiceHost.Close();  
              }  
              catch (CommunicationException e)  
              {  
                  Console.WriteLine(e.Message);  
              }  
              catch (TimeoutException e)  
              {  
                  Console.WriteLine(e.Message);  
              }     
  
              if (proxyServiceHost.State != CommunicationState.Closed)  
              {  
                  Console.WriteLine("Aborting the service...");  
                  proxyServiceHost.Abort();  
              }  
    ```  
  
 <span data-ttu-id="79bb4-171">Ukończono wdrażanie serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="79bb4-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="79bb4-172">W dalszym ciągu na [porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="79bb4-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79bb4-173">Przykład</span><span class="sxs-lookup"><span data-stu-id="79bb4-173">Example</span></span>  
 <span data-ttu-id="79bb4-174">Jest to pełna lista kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="79bb4-174">This is the full listing of the code used in this topic.</span></span>  
  
```  
// DiscoveryProxy.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using System.Xml;  
  
namespace Microsoft.Samples.Discovery  
{  
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]  
    public class DiscoveryProxyService : DiscoveryProxy  
    {  
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.  
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;  
  
        public DiscoveryProxyService()  
        {  
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();  
        }  
  
        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy  
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
        {          
            this.AddOnlineService(endpointDiscoveryMetadata);  
            return new OnOnlineAnnouncementAsyncResult(callback, state);  
        }  
  
        protected override void OnEndOnlineAnnouncement(IAsyncResult result)  
        {  
            OnOnlineAnnouncementAsyncResult.End(result);  
        }  
  
        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy  
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
        {  
            this.RemoveOnlineService(endpointDiscoveryMetadata);  
            return new OnOfflineAnnouncementAsyncResult(callback, state);  
        }  
  
        protected override void OnEndOfflineAnnouncement(IAsyncResult result)  
        {  
            OnOfflineAnnouncementAsyncResult.End(result);  
        }  
  
        // OnBeginFind method is called when a Probe request message is received by the Proxy  
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)  
        {  
            this.MatchFromOnlineService(findRequestContext);  
            return new OnFindAsyncResult(callback, state);  
        }  
  
        protected override void OnEndFind(IAsyncResult result)  
        {  
            OnFindAsyncResult.End(result);  
        }  
  
        // OnBeginFind method is called when a Resolve request message is received by the Proxy  
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)  
        {  
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);  
        }  
  
        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)  
        {  
            return OnResolveAsyncResult.End(result);  
        }  
  
        // The following are helper methods required by the Proxy implementation  
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
        {  
            lock (this.onlineServices)  
            {  
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;                  
            }  
  
            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");  
        }  
  
        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
        {  
            if (endpointDiscoveryMetadata != null)  
            {  
                lock (this.onlineServices)  
                {  
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);                      
                }  
  
                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");  
            }      
        }  
  
        void MatchFromOnlineService(FindRequestContext findRequestContext)  
        {  
            lock (this.onlineServices)  
            {  
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                {  
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))  
                    {  
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);  
                    }  
                }  
            }  
        }  
  
        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)  
        {  
            EndpointDiscoveryMetadata matchingEndpoint = null;  
            lock (this.onlineServices)  
            {  
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                {  
                    if (criteria.Address == endpointDiscoveryMetadata.Address)  
                    {  
                        matchingEndpoint = endpointDiscoveryMetadata;  
                    }  
                }  
            }  
            return matchingEndpoint;  
        }  
  
        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)  
        {  
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");  
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)  
            {  
                Console.WriteLine("** " + contractName.ToString());  
                break;  
            }  
            Console.WriteLine("**** Operation Completed");  
        }  
  
        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult  
        {  
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);  
            }  
        }  
  
        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult  
        {  
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);  
            }  
        }  
  
        sealed class OnFindAsyncResult : AsyncResult  
        {  
            public OnFindAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnFindAsyncResult>(result);  
            }  
        }  
  
        sealed class OnResolveAsyncResult : AsyncResult  
        {  
            EndpointDiscoveryMetadata matchingEndpoint;  
  
            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.matchingEndpoint = matchingEndpoint;  
                this.Complete(true);  
            }  
  
            public static EndpointDiscoveryMetadata End(IAsyncResult result)  
            {  
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);  
                return thisPtr.matchingEndpoint;  
            }  
        }  
    }  
}  
```  
  
```  
// AsyncResult.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Threading;  
  
namespace Microsoft.Samples.Discovery  
{  
    abstract class AsyncResult : IAsyncResult  
    {  
        AsyncCallback callback;  
        bool completedSynchronously;  
        bool endCalled;  
        Exception exception;  
        bool isCompleted;  
        ManualResetEvent manualResetEvent;  
        object state;  
        object thisLock;  
  
        protected AsyncResult(AsyncCallback callback, object state)  
        {  
            this.callback = callback;  
            this.state = state;  
            this.thisLock = new object();  
        }  
  
        public object AsyncState  
        {  
            get  
            {  
                return state;  
            }  
        }  
  
        public WaitHandle AsyncWaitHandle  
        {  
            get  
            {  
                if (manualResetEvent != null)  
                {  
                    return manualResetEvent;  
                }  
                lock (ThisLock)  
                {  
                    if (manualResetEvent == null)  
                    {  
                        manualResetEvent = new ManualResetEvent(isCompleted);  
                    }  
                }  
                return manualResetEvent;  
            }  
        }  
  
        public bool CompletedSynchronously  
        {  
            get  
            {  
                return completedSynchronously;  
            }  
        }  
  
        public bool IsCompleted  
        {  
            get  
            {  
                return isCompleted;  
            }  
        }  
  
        object ThisLock  
        {  
            get  
            {  
                return this.thisLock;  
            }  
        }  
  
        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)  
            where TAsyncResult : AsyncResult  
        {  
            if (result == null)  
            {  
                throw new ArgumentNullException("result");  
            }  
  
            TAsyncResult asyncResult = result as TAsyncResult;  
  
            if (asyncResult == null)  
            {  
                throw new ArgumentException("Invalid async result.", "result");  
            }  
  
            if (asyncResult.endCalled)  
            {  
                throw new InvalidOperationException("Async object already ended.");  
            }  
  
            asyncResult.endCalled = true;  
  
            if (!asyncResult.isCompleted)  
            {  
                asyncResult.AsyncWaitHandle.WaitOne();  
            }  
  
            if (asyncResult.manualResetEvent != null)  
            {  
                asyncResult.manualResetEvent.Close();  
            }  
  
            if (asyncResult.exception != null)  
            {  
                throw asyncResult.exception;  
            }  
  
            return asyncResult;  
        }  
  
        protected void Complete(bool completedSynchronously)  
        {  
            if (isCompleted)  
            {  
                throw new InvalidOperationException("This async result is already completed.");  
            }  
  
            this.completedSynchronously = completedSynchronously;  
  
            if (completedSynchronously)  
            {  
                this.isCompleted = true;  
            }  
            else  
            {  
                lock (ThisLock)  
                {  
                    this.isCompleted = true;  
                    if (this.manualResetEvent != null)  
                    {  
                        this.manualResetEvent.Set();  
                    }  
                }  
            }  
  
            if (callback != null)  
            {  
                callback(this);  
            }  
        }  
  
        protected void Complete(bool completedSynchronously, Exception exception)  
        {  
            this.exception = exception;  
            Complete(completedSynchronously);  
        }  
    }  
}  
```  
  
```  
// program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Program  
    {  
        public static void Main()  
        {  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
            // Host the DiscoveryProxy service  
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());  
  
            try  
            {                  
                // Add DiscoveryEndpoint to receive Probe and Resolve messages  
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
                discoveryEndpoint.IsSystemEndpoint = false;  
  
                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages  
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));                  
  
                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);  
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);  
  
                proxyServiceHost.Open();  
  
                Console.WriteLine("Proxy Service started.");  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to terminate the service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                proxyServiceHost.Close();  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            catch (TimeoutException e)  
            {  
                Console.WriteLine(e.Message);  
            }     
  
            if (proxyServiceHost.State != CommunicationState.Closed)  
            {  
                Console.WriteLine("Aborting the service...");  
                proxyServiceHost.Abort();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="79bb4-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79bb4-175">See Also</span></span>  
 [<span data-ttu-id="79bb4-176">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="79bb4-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="79bb4-177">Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="79bb4-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="79bb4-178">Porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi</span><span class="sxs-lookup"><span data-stu-id="79bb4-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 [<span data-ttu-id="79bb4-179">Porady: testowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="79bb4-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)