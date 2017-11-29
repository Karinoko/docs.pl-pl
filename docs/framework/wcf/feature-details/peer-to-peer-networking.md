---
title: "Sieci równorzędne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e66a2f87d69ddba1676ed5e210859edfb5d8e41
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="f2acb-102">Sieci równorzędne</span><span class="sxs-lookup"><span data-stu-id="f2acb-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="f2acb-103">Kanał elementu równorzędnego jest technologią komunikacji (P2P) wielopartyjnej, peer-to-peer w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2acb-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="f2acb-104">Umożliwia bezpieczne i skalowalne oparta na komunikatach P2P kanał komunikacji dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2acb-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="f2acb-105">Jednym z typowych przykładów wielopartyjnej aplikacji, które mogą korzystać z kanału równorzędnego jest współpracy aplikacji, na przykład rozmowy, w przypadku, gdy grupa osób rozmów ze sobą w sposób peer-to-peer, bez serwerów.</span><span class="sxs-lookup"><span data-stu-id="f2acb-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="f2acb-106">Kanał elementu równorzędnego umożliwia P2P współpracy, dystrybucji zawartości, równoważenia obciążenia i rozproszonego przetwarzania w scenariuszach zarówno konsumenta, jak i enterprise.</span><span class="sxs-lookup"><span data-stu-id="f2acb-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="f2acb-107">Kanał elementu równorzędnego jest domyślnie włączone na [!INCLUDE[wv](../../../../includes/wv-md.md)], ponieważ jest wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2acb-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f2acb-108">Dostęp do kanału równorzędnego klas, dodaj odwołania do System.ServiceModel.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="f2acb-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="f2acb-109">Poniższe sekcje zawierają informacje dotyczące sieci peer-to-peer i korzystania z kanału równorzędnego klasy do tworzenia aplikacji w sieci równorzędnej.</span><span class="sxs-lookup"><span data-stu-id="f2acb-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2acb-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f2acb-110">In This Section</span></span>  
 <span data-ttu-id="f2acb-111">[Scenariusze obejmujące kanał równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): w tym artykule opisano scenariusze programowania obsługiwane przez interfejsy API kanał elementu równorzędnego, takie jak wiadomości, współpracy, publikacji/subskrypcji rozproszonego przetwarzania i gier.</span><span class="sxs-lookup"><span data-stu-id="f2acb-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="f2acb-112">[Pojęcia kanałów równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): w tym artykule opisano siatki elementów równorzędnych, węzły równorzędne zabezpieczenia kanału równorzędnego i mechanizmy rozpoznawania elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f2acb-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="f2acb-113">[Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): znajdują się wskazówki dotyczące tworzenia aplikacji kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f2acb-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="f2acb-114">Przykłady kodu dla kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="f2acb-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="f2acb-115">Program rozpoznawania nazw niestandardowego elementu równorzędnego kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="f2acb-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="f2acb-116">Blog zespołu kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="f2acb-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="f2acb-117">[Blog zespołu kanału równorzędnego](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="f2acb-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>