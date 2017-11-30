---
title: 'Porady: tworzenie WSFederationHttpBinding'
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
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3314519e89a78f188d78a5e5af641d7c87ee1c46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a><span data-ttu-id="6099d-102">Porady: tworzenie WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6099d-102">How to: Create a WSFederationHttpBinding</span></span>
<span data-ttu-id="6099d-103">W [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], <xref:System.ServiceModel.WSFederationHttpBinding> klasy ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) zapewnia mechanizm udostępnianie usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="6099d-103">In [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], the <xref:System.ServiceModel.WSFederationHttpBinding> class ([\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in configuration) provides a mechanism for exposing a federated service.</span></span> <span data-ttu-id="6099d-104">Oznacza to, że usługa, która wymaga od klientów uwierzytelniania za pomocą tokenu zabezpieczającego wydanego przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-104">That is, a service that requires clients to authenticate using a security token issued by a security token service.</span></span> <span data-ttu-id="6099d-105">W tym temacie przedstawiono sposób konfigurowania <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6099d-105">This topic shows how to set up a <xref:System.ServiceModel.WSFederationHttpBinding> in both code and configuration.</span></span> <span data-ttu-id="6099d-106">Po utworzeniu powiązania punktu końcowego można skonfigurować do używania tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6099d-106">Once the binding is created, you can set up an endpoint to use that binding.</span></span>  
  
 <span data-ttu-id="6099d-107">Podstawowe kroki przedstawione poniżej:</span><span class="sxs-lookup"><span data-stu-id="6099d-107">The basic steps are outlined as follows:</span></span>  
  
1.  <span data-ttu-id="6099d-108">Wybierz tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6099d-108">Select a security mode.</span></span> <span data-ttu-id="6099d-109"><xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje `Message`, nawet przez kilka przeskoków, która umożliwia zabezpieczeń na trasie na poziomie komunikatu i `TransportWithMessageCredential`, który zapewnia lepszą wydajność w przypadku, gdy klient i usługa ułatwia bezpośrednie połączenie za pośrednictwem PROTOKÓŁ HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6099d-109">The <xref:System.ServiceModel.WSFederationHttpBinding> supports `Message`, which provides end-to-end security at the message level, even across multiple hops, and `TransportWithMessageCredential`, which provides better performance in cases where the client and the service can make a direct connection over HTTPS.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6099d-110"><xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje również `None` jako tryb zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6099d-110">The <xref:System.ServiceModel.WSFederationHttpBinding> also supports `None` as a security mode.</span></span> <span data-ttu-id="6099d-111">Ten tryb nie jest bezpieczna i jest dostępne tylko do celów debugowania.</span><span class="sxs-lookup"><span data-stu-id="6099d-111">This mode is not secure and is provided for debugging purposes only.</span></span> <span data-ttu-id="6099d-112">Jeśli punkt końcowy usługi jest wdrażany z <xref:System.ServiceModel.WSFederationHttpBinding> z jej ustawić tryb zabezpieczeń `None`, wynikowy klienta powiązania (generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) jest <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z tryb zabezpieczeń `None`.</span><span class="sxs-lookup"><span data-stu-id="6099d-112">If a service endpoint is deployed with a <xref:System.ServiceModel.WSFederationHttpBinding> with its security mode set to `None`, the resulting client binding (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) is a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with a security mode of `None`.</span></span>  
  
     <span data-ttu-id="6099d-113">W przeciwieństwie do innych powiązania dostarczane przez system nie jest konieczne wybieranie typu poświadczeń klienta przy użyciu `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="6099d-113">Unlike other system-provided bindings, it is not necessary to select a client credential type when using the `WSFederationHttpBinding`.</span></span> <span data-ttu-id="6099d-114">Jest tak, ponieważ typ poświadczeń klienta jest zawsze wystawionego tokenu.</span><span class="sxs-lookup"><span data-stu-id="6099d-114">This is because the client credential type is always an issued token.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6099d-115">uzyskuje token z określonego wystawcę i przedstawia tokenu usługi do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="6099d-115"> acquires a token from a specified issuer and presents that token to the service to authenticate the client.</span></span>  
  
2.  <span data-ttu-id="6099d-116">Na klientach federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwość adres URL usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-116">On federated clients, set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> property to the URL of the security token service.</span></span> <span data-ttu-id="6099d-117">Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> do powiązania w celu użycia do komunikowania się z usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-117">Set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> to the binding to use to communicate with the security token service.</span></span>  
  
3.  <span data-ttu-id="6099d-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-118">Optional.</span></span> <span data-ttu-id="6099d-119">Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> właściwości do jednolity identyfikator zasobów (URI) typu tokenu.</span><span class="sxs-lookup"><span data-stu-id="6099d-119">Set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> property to the Uniform Resource Identifier (URI) of a token type.</span></span> <span data-ttu-id="6099d-120">Na usług federacyjnych Określ typ tokenu, który oczekuje usługi.</span><span class="sxs-lookup"><span data-stu-id="6099d-120">On federated services, specify the token type that the service expects.</span></span> <span data-ttu-id="6099d-121">Na klientach federacyjnych Określ typ tokenu żądania klienta z usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-121">On federated clients, specify the token type the client requests from the security token service.</span></span>  
  
     <span data-ttu-id="6099d-122">Jeśli nie tokenu określono typu, klientów generuje tokeny zabezpieczające żądania WS-Trust (RSTs) bez tokenu typu identyfikatora URI i usług spodziewać się uwierzytelnianie klientów za pomocą tokenu zabezpieczeń potwierdzenia Markup Language (SAML) 1.1 domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6099d-122">If no token type is specified, clients generate WS-Trust Request Security Tokens (RSTs) without a token type URI, and services expect client authentication using a Security Assertions Markup Language (SAML) 1.1 token by default.</span></span>  
  
     <span data-ttu-id="6099d-123">Identyfikator URI dla tokenu SAML 1.1 jest "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".</span><span class="sxs-lookup"><span data-stu-id="6099d-123">The URI for a SAML 1.1 token is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".</span></span>  
  
4.  <span data-ttu-id="6099d-124">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-124">Optional.</span></span> <span data-ttu-id="6099d-125">W usługach federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> właściwość adres URL metadanych usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-125">On federated services, set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> property to the metadata URL of a security token service.</span></span> <span data-ttu-id="6099d-126">Punkt końcowy metadanych umożliwia klientom usługi wybierz para powiązanie odpowiednie/punktu końcowego, jeśli usługa jest skonfigurowana do publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="6099d-126">The metadata endpoint enables clients of the service to select an appropriate binding/endpoint pair, if the service is configured to publish metadata.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6099d-127">Publikowanie metadanych, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).</span><span class="sxs-lookup"><span data-stu-id="6099d-127"> publishing metadata, see [Publishing Metadata](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).</span></span>  
  
 <span data-ttu-id="6099d-128">Można również ustawić inne właściwości, takich jak typ klucz używany jako dowód klucza wystawionego tokenu, pakiet algorytmów do użycia między klientem a usługą, czy do negocjowania lub jawnie określ poświadczenia usługi, szczególne oświadczeń usługi oczekuje wystawiony token zawierał i wszelkie dodatkowe elementy XML dodane do żądania, które klient wysyła do usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-128">You can also set other properties, including the type of key used as a proof key in the issued token, the algorithm suite to use between the client and the service, whether to negotiate or explicitly specify the service credential, any specific claims the service expects the issued token to contain, and any additional XML elements that must be added to the request the client sends to the security token service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6099d-129">`NegotiateServiceCredential` Właściwość ma zastosowanie tylko podczas `SecurityMode` ma ustawioną wartość `Message`.</span><span class="sxs-lookup"><span data-stu-id="6099d-129">The `NegotiateServiceCredential` property is only relevant when the `SecurityMode` is set to `Message`.</span></span> <span data-ttu-id="6099d-130">Jeśli `SecurityMode` ustawiono `TransportWithMessageCredential`, a następnie `NegotiateServiceCredential` właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="6099d-130">If `SecurityMode` is set to `TransportWithMessageCredential`, then the `NegotiateServiceCredential` property is ignored.</span></span>  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a><span data-ttu-id="6099d-131">Aby skonfigurować WSFederationHttpBinding w kodzie</span><span class="sxs-lookup"><span data-stu-id="6099d-131">To configure a WSFederationHttpBinding in code</span></span>  
  
1.  <span data-ttu-id="6099d-132">Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6099d-132">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding>.</span></span>  
  
2.  <span data-ttu-id="6099d-133">Ustaw <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="6099d-133">Set the <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.WSFederationHttpSecurityMode> or <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> as required.</span></span> <span data-ttu-id="6099d-134">Jeśli pakiet algorytmów innych niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> jest wymagane, ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> właściwości na wartość pobranych z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="6099d-134">If an algorithm suite other than <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> is required, set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> property to a value taken from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>  
  
3.  <span data-ttu-id="6099d-135">Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="6099d-135">Set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> property as appropriate.</span></span>  
  
4.  <span data-ttu-id="6099d-136">Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> właściwości <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` lub.`AsymmetricKey`</span><span class="sxs-lookup"><span data-stu-id="6099d-136">Set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> property to <xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey` or .`AsymmetricKey`</span></span> <span data-ttu-id="6099d-137">co jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="6099d-137">as required.</span></span>  
  
5.  <span data-ttu-id="6099d-138">Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6099d-138">Set the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> property to the appropriate value.</span></span> <span data-ttu-id="6099d-139">Jeśli wartość nie jest ustawiona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1", które wskazuje tokeny SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="6099d-139">If no value is set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] defaults to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1", which indicates SAML 1.1 tokens.</span></span>  
  
6.  <span data-ttu-id="6099d-140">Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; Opcjonalnie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-140">Required on the client if no local issuer is specified; optional on the service.</span></span> <span data-ttu-id="6099d-141">Utwórz <xref:System.ServiceModel.EndpointAddress> zawierający informacje o adres i tożsamość usługi tokenu zabezpieczającego i przypisz <xref:System.ServiceModel.EndpointAddress> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6099d-141">Create an <xref:System.ServiceModel.EndpointAddress> that contains the address and identity information of the security token service and assign the <xref:System.ServiceModel.EndpointAddress> instance to the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> property.</span></span>  
  
7.  <span data-ttu-id="6099d-142">Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; nie są używane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-142">Required on the client if no local issuer is specified; not used on the service.</span></span> <span data-ttu-id="6099d-143">Utwórz <xref:System.ServiceModel.Channels.Binding> dla `SecurityTokenService` i przypisz <xref:System.ServiceModel.Channels.Binding> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6099d-143">Create a <xref:System.ServiceModel.Channels.Binding> for the `SecurityTokenService` and assign the <xref:System.ServiceModel.Channels.Binding> instance to the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> property.</span></span>  
  
8.  <span data-ttu-id="6099d-144">Nie jest używany na komputerze klienckim; Opcjonalnie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-144">Not used on the client; optional on the service.</span></span> <span data-ttu-id="6099d-145">Utwórz <xref:System.ServiceModel.EndpointAddress> wystąpienie metadanych usługi tokenu zabezpieczeń i przypisz go do `IssuerMetadataAddress` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6099d-145">Create an <xref:System.ServiceModel.EndpointAddress> instance for the metadata of the security token service and assign it to the `IssuerMetadataAddress` property.</span></span>  
  
9. <span data-ttu-id="6099d-146">Opcjonalnie zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="6099d-146">Optional on both the client and the service.</span></span> <span data-ttu-id="6099d-147">Utwórz i Dodaj jeden lub więcej <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6099d-147">Create and add one or more <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instances to the collection returned by the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> property.</span></span>  
  
10. <span data-ttu-id="6099d-148">Opcjonalnie zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="6099d-148">Optional on both the client and the service.</span></span> <span data-ttu-id="6099d-149">Utwórz i Dodaj jeden lub więcej <xref:System.Xml.XmlElement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6099d-149">Create and add one or more <xref:System.Xml.XmlElement> instances to the collection returned by the <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> property.</span></span>  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a><span data-ttu-id="6099d-150">Aby utworzyć punkt końcowy federacyjnych w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6099d-150">To create a federated endpoint in configuration</span></span>  
  
1.  <span data-ttu-id="6099d-151">Utwórz [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako element podrzędny [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6099d-151">Create a [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) as a child of the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element in the application configuration file.</span></span>  
  
2.  <span data-ttu-id="6099d-152">Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element jako element podrzędny [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6099d-152">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element as a child of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="6099d-153">Utwórz `<security>` element jako element podrzędny [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-153">Create a `<security>` element as a child of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
4.  <span data-ttu-id="6099d-154">Ustaw `mode` atrybutu `<security>` elementu na wartość `Message` lub `TransportWithMessageCredential`, co jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="6099d-154">Set the `mode` attribute on the `<security>` element to a value of `Message` or `TransportWithMessageCredential`, as required.</span></span>  
  
5.  <span data-ttu-id="6099d-155">Utwórz `<message>` element jako element podrzędny `<security>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-155">Create a `<message>` element as a child of the `<security>` element.</span></span>  
  
6.  <span data-ttu-id="6099d-156">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-156">Optional.</span></span> <span data-ttu-id="6099d-157">Ustaw `algorithmSuite` atrybutu `<message>` element odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6099d-157">Set the `algorithmSuite` attribute on the `<message>` element with an appropriate value.</span></span> <span data-ttu-id="6099d-158">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="6099d-158">The default is `Basic256`.</span></span>  
  
7.  <span data-ttu-id="6099d-159">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-159">Optional.</span></span> <span data-ttu-id="6099d-160">Jeśli klucz asymetryczny potwierdzającego jest wymagane, ustaw `issuedKeyType` atrybutu `<message>` elementu `AsymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="6099d-160">If an asymmetric proof key is required, set the `issuedKeyType` attribute of the `<message>` element to `AsymmetricKey`.</span></span> <span data-ttu-id="6099d-161">Wartość domyślna to `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="6099d-161">The default is `SymmetricKey`.</span></span>  
  
8.  <span data-ttu-id="6099d-162">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-162">Optional.</span></span> <span data-ttu-id="6099d-163">Ustaw `issuedTokenType` atrybutu `<message>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-163">Set the `issuedTokenType` attribute on the `<message>` element.</span></span>  
  
9. <span data-ttu-id="6099d-164">Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; Opcjonalnie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-164">Required on the client if no local issuer is specified; optional on the service.</span></span> <span data-ttu-id="6099d-165">Utwórz `<issuer>` element jako element podrzędny `<message>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-165">Create an `<issuer>` element as a child of the `<message>` element.</span></span>  
  
10. <span data-ttu-id="6099d-166">Ustaw `address` atrybutu `<issuer>` element i określ adres, pod którym usługa tokenu zabezpieczającego akceptuje żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="6099d-166">Set the `address` attribute to the `<issuer>` element and specify the address at which the security token service accepts token requests.</span></span>  
  
11. <span data-ttu-id="6099d-167">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6099d-167">Optional.</span></span> <span data-ttu-id="6099d-168">Dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6099d-168">Add an `<identity>` child element and specify the identity of the security token service</span></span>  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6099d-169">[Usługi uwierzytelnianie i tożsamość](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6099d-169"> [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
13. <span data-ttu-id="6099d-170">Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; nie są używane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-170">Required on the client if no local issuer is specified; not used on the service.</span></span> <span data-ttu-id="6099d-171">Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) w sekcji powiązania, który może służyć do komunikacji z usługą tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6099d-171">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element in the bindings section that can be used to communicate with the security token service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6099d-172">Tworzenie powiązania, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6099d-172"> creating a binding, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
14. <span data-ttu-id="6099d-173">Określanie powiązania utworzony w poprzednim kroku, ustawiając `binding` i `bindingConfiguration` atrybuty `<issuer>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-173">Specify the binding created in the previous step by setting the `binding` and `bindingConfiguration` attributes of the `<issuer>` element.</span></span>  
  
15. <span data-ttu-id="6099d-174">Nie jest używany na komputerze klienckim; Opcjonalnie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6099d-174">Not used on the client; optional on the service.</span></span> <span data-ttu-id="6099d-175">Utwórz `<issuerMetadata>` element jako element podrzędny <`message`> elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-175">Create an `<issuerMetadata>` element as a child of the <`message`> element.</span></span> <span data-ttu-id="6099d-176">Następnie w `address` atrybutu `<issuerMetadata>` elementu, określ adres, pod którym usługi tokenu zabezpieczającego Publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="6099d-176">Then, in an `address` attribute on the `<issuerMetadata>` element, specify the address at which the security token service is to publish its metadata.</span></span> <span data-ttu-id="6099d-177">Opcjonalnie dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6099d-177">Optionally, add an `<identity>` child element and specify the identity of the security token service.</span></span>  
  
16. <span data-ttu-id="6099d-178">Opcjonalnie zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="6099d-178">Optional on both the client and the service.</span></span> <span data-ttu-id="6099d-179">Dodaj `<claimTypeRequirements>` element jako element podrzędny `<message>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6099d-179">Add a `<claimTypeRequirements>` element as a child of the `<message>` element.</span></span> <span data-ttu-id="6099d-180">Określ wymaganych i opcjonalnych oświadczeń korzystający usługi przez dodanie [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementy `<claimTypeRequirements>` element i określając oświadczenie typu z `claimType` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6099d-180">Specify required and optional claims that the service relies on by adding [\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elements to the `<claimTypeRequirements>` element and specifying the claim type with the `claimType` attribute.</span></span> <span data-ttu-id="6099d-181">Określ, czy dany oświadczenia jest wymagany lub opcjonalny przez ustawienie `isOptional` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6099d-181">Specify whether a given claim is required or optional by setting the `isOptional` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6099d-182">Przykład</span><span class="sxs-lookup"><span data-stu-id="6099d-182">Example</span></span>  
 <span data-ttu-id="6099d-183">Poniższy przykład kodu pokazuje kodu do konfigurowania `WSFederationHttpBinding` imperatively.</span><span class="sxs-lookup"><span data-stu-id="6099d-183">The following code sample shows code for setting up a `WSFederationHttpBinding` imperatively.</span></span>  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6099d-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6099d-184">See Also</span></span>  
 [<span data-ttu-id="6099d-185">Federacyjna</span><span class="sxs-lookup"><span data-stu-id="6099d-185">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="6099d-186">Federacja — przykład</span><span class="sxs-lookup"><span data-stu-id="6099d-186">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [<span data-ttu-id="6099d-187">Porady: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6099d-187">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)