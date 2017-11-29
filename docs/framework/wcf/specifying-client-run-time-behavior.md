---
title: "Określanie zachowania klienta w czasie wykonywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3aebab3799af562d958eb8e3e83380e734fe9268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-client-run-time-behavior"></a><span data-ttu-id="07f5e-102">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="07f5e-102">Specifying Client Run-Time Behavior</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="07f5e-103">klientów, takie jak [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usług, można skonfigurować do modyfikowania zachowania w czasie wykonywania do własnych aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="07f5e-103"> clients, like [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, can be configured to modify the run-time behavior to suit the client application.</span></span> <span data-ttu-id="07f5e-104">Atrybuty trzy są dostępne do określania zachowania klienta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07f5e-104">Three attributes are available for specifying client run-time behavior.</span></span> <span data-ttu-id="07f5e-105">Obiekty klienta dwustronnego wywołania zwrotnego można użyć <xref:System.ServiceModel.CallbackBehaviorAttribute> i <xref:System.ServiceModel.Description.CallbackDebugBehavior> atrybuty do modyfikowania zachowania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07f5e-105">Duplex client callback objects can use the <xref:System.ServiceModel.CallbackBehaviorAttribute> and <xref:System.ServiceModel.Description.CallbackDebugBehavior> attributes to modify their run-time behavior.</span></span> <span data-ttu-id="07f5e-106">Ten atrybut <xref:System.ServiceModel.Description.ClientViaBehavior>, może służyć do rozdzielania logicznej docelowej z docelowego bezpośredniej sieci.</span><span class="sxs-lookup"><span data-stu-id="07f5e-106">The other attribute, <xref:System.ServiceModel.Description.ClientViaBehavior>, can be used to separate the logical destination from the immediate network destination.</span></span> <span data-ttu-id="07f5e-107">Ponadto klienta dwustronnego wywołania zwrotnego typów mogą korzystać z niektórych zachowań po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="07f5e-107">In addition, duplex client callback types can use some of the service-side behaviors.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="07f5e-108">[Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="07f5e-108"> [Specifying Service Run-Time Behavior](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).</span></span>  
  
## <a name="using-the-callbackbehaviorattribute"></a><span data-ttu-id="07f5e-109">Przy użyciu CallbackBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="07f5e-109">Using the CallbackBehaviorAttribute</span></span>  
 <span data-ttu-id="07f5e-110">Możesz skonfigurować lub rozszerzyć sposób wykonywania realizacji kontrakt wywołania zwrotnego w aplikacji klienta przy użyciu <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="07f5e-110">You can configure or extend the execution behavior of a callback contract implementation in a client application by using the <xref:System.ServiceModel.CallbackBehaviorAttribute> class.</span></span> <span data-ttu-id="07f5e-111">Ten atrybut pełni podobną funkcję wywołania zwrotnego klasy jako <xref:System.ServiceModel.ServiceBehaviorAttribute> klasy, z wyjątkiem wystąpień ustawienia zachowania i transakcji.</span><span class="sxs-lookup"><span data-stu-id="07f5e-111">This attribute performs a similar function for the callback class as the <xref:System.ServiceModel.ServiceBehaviorAttribute> class, with the exception of instancing behavior and transaction settings.</span></span>  
  
 <span data-ttu-id="07f5e-112"><xref:System.ServiceModel.CallbackBehaviorAttribute> Klasy musi odnosić się do klasy, która implementuje kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="07f5e-112">The <xref:System.ServiceModel.CallbackBehaviorAttribute> class must be applied to the class that implements the callback contract.</span></span> <span data-ttu-id="07f5e-113">Jeśli zastosowano implementacji obsługującej kontrakt <xref:System.InvalidOperationException> wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07f5e-113">If applied to a nonduplex contract implementation, an <xref:System.InvalidOperationException> exception is thrown at run time.</span></span> <span data-ttu-id="07f5e-114">Poniższy kod przedstawia przykład <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy dla obiektu wywołania zwrotnego, który używa <xref:System.Threading.SynchronizationContext> obiektem, aby określić wątku do organizowania, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> właściwość Sprawdzanie poprawności komunikatu, wymuszenie i <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> właściwości do zwrócenia Wyjątki jako <xref:System.ServiceModel.FaultException> obiektów do usługi w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="07f5e-114">The following code example shows a <xref:System.ServiceModel.CallbackBehaviorAttribute> class on a callback object that uses the <xref:System.Threading.SynchronizationContext> object to determine the thread to marshal to, the <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> property to enforce message validation, and the <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> property to return exceptions as <xref:System.ServiceModel.FaultException> objects to the service for debugging purposes.</span></span>  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a><span data-ttu-id="07f5e-115">Aby włączyć przepływ informacji o zarządzanych wyjątku przy użyciu CallbackDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="07f5e-115">Using CallbackDebugBehavior to Enable the Flow of Managed Exception Information</span></span>  
 <span data-ttu-id="07f5e-116">Można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania przez ustawienie <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwości `true` pliku programowo lub z konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07f5e-116">You can enable the flow of managed exception information in a client callback object back to the service for debugging purposes by setting the <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> property to `true` either programmatically or from an application configuration file.</span></span>  
  
 <span data-ttu-id="07f5e-117">Zwraca informacje o zarządzanym wyjątku do usług może stanowić zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawnienie informacji o wewnętrznego klienta można użyć implementacji nieautoryzowany usług.</span><span class="sxs-lookup"><span data-stu-id="07f5e-117">Returning managed exception information to services can be a security risk because exception details expose information about the internal client implementation that  unauthorized services could use.</span></span> <span data-ttu-id="07f5e-118">Ponadto mimo że <xref:System.ServiceModel.Description.CallbackDebugBehavior> również można ustawić właściwości programowo, można go łatwo Pamiętaj, aby wyłączyć <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> podczas wdrażania.</span><span class="sxs-lookup"><span data-stu-id="07f5e-118">In addition, although the <xref:System.ServiceModel.Description.CallbackDebugBehavior> properties can also be set programmatically, it can be easy to forget to disable <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> when deploying.</span></span>  
  
 <span data-ttu-id="07f5e-119">Z powodu zagadnień związanych z zabezpieczeniami zdecydowanie zalecane jest:</span><span class="sxs-lookup"><span data-stu-id="07f5e-119">Because of the security issues involved, it is strongly recommended that:</span></span>  
  
-   <span data-ttu-id="07f5e-120">Użyj pliku konfiguracji aplikacji można ustawić wartości <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="07f5e-120">You use an application configuration file to set the value of the <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="07f5e-121">Czynności wykonywane tylko w kontrolowany debugowania scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="07f5e-121">You do so only in controlled debugging scenarios.</span></span>  
  
 <span data-ttu-id="07f5e-122">Poniższy przykład kodu pokazuje klienta pliku konfiguracji, który powoduje, że [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Aby uzyskać informacje o zarządzanym wyjątku w kliencie obiektu wywołania zwrotnego wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="07f5e-122">The following code example shows a client configuration file that instructs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to return managed exception information from a client callback object in SOAP messages.</span></span>  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a><span data-ttu-id="07f5e-123">Używając zachowania ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="07f5e-123">Using the ClientViaBehavior Behavior</span></span>  
 <span data-ttu-id="07f5e-124">Można użyć <xref:System.ServiceModel.Description.ClientViaBehavior> zachowania, aby określić jednolitego identyfikatora zasobów, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="07f5e-124">You can use the <xref:System.ServiceModel.Description.ClientViaBehavior> behavior to specify the Uniform Resource Identifier for which the transport channel should be created.</span></span> <span data-ttu-id="07f5e-125">Używanie tego zachowania, gdy docelowego bezpośredniej sieci nie jest zamierzone procesora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="07f5e-125">Use this behavior when the immediate network destination is not the intended processor of the message.</span></span> <span data-ttu-id="07f5e-126">Dzięki temu konwersacji z wieloma przeskokami, gdy aplikacja wywołująca nie zna ultimate docelowego lub docelowego `Via` nagłówka nie jest adresem.</span><span class="sxs-lookup"><span data-stu-id="07f5e-126">This enables multiple-hop conversations when the calling application does not necessarily know the ultimate destination or when the destination `Via` header is not an address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f5e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07f5e-127">See Also</span></span>  
 [<span data-ttu-id="07f5e-128">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="07f5e-128">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)