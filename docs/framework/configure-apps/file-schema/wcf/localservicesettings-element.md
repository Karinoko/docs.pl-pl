---
title: '&lt;localServiceSettings&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e251c226484788b7ebc059cd68caf1f3c150c62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalservicesettingsgt-element"></a><span data-ttu-id="931ce-102">&lt;localServiceSettings&gt;, element</span><span class="sxs-lookup"><span data-stu-id="931ce-102">&lt;localServiceSettings&gt; element</span></span>
<span data-ttu-id="931ce-103">Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="931ce-103">Specifies the security settings of a local service for this binding.</span></span>  
  
 <span data-ttu-id="931ce-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="931ce-104">\<system.serviceModel></span></span>  
<span data-ttu-id="931ce-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="931ce-105">\<bindings></span></span>  
<span data-ttu-id="931ce-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="931ce-106">\<customBinding></span></span>  
<span data-ttu-id="931ce-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="931ce-107">\<binding></span></span>  
<span data-ttu-id="931ce-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="931ce-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="931ce-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="931ce-109">Syntax</span></span>  
  
```xml  
<security>  
   <localServiceSettings detectReplays="Boolean"  
      inactivityTimeout="TimeSpan"  
      issuedCookieLifeTime="TimeSpan"  
      maxCachedCookies="Integer"   
      maxClockSkew="TimeSpan"   
      maxPendingSessions="Integer"  
      maxStatefulNegotiations="Integer"  
      negotiationTimeout="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
            replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="931ce-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="931ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="931ce-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="931ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="931ce-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="931ce-112">Attributes</span></span>  
  
|<span data-ttu-id="931ce-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="931ce-113">Attribute</span></span>|<span data-ttu-id="931ce-114">Opis</span><span class="sxs-lookup"><span data-stu-id="931ce-114">Description</span></span>|  
|---------------|-----------------|  
|`detectReplays`|<span data-ttu-id="931ce-115">Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="931ce-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="931ce-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="931ce-116">The default is `false`.</span></span>|  
|`inactivityTimeout`|<span data-ttu-id="931ce-117">Dodatnią <xref:System.TimeSpan> , który określa okres bezczynności kanału czeka zanim upłynie limit czasu. Wartość domyślna to "01: 00:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-117">A positive <xref:System.TimeSpan> that specifies the duration of inactivity the channel waits before it times out. The default is "01:00:00".</span></span>|  
|`issuedCookieLifeTime`|<span data-ttu-id="931ce-118">A <xref:System.TimeSpan> określający czas istnienia nadawany wszystkich nowych plików cookie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="931ce-118">A <xref:System.TimeSpan> that specifies the lifetime issued to all new security cookies.</span></span> <span data-ttu-id="931ce-119">Pliki cookie, które wykraczają poza ich istnienia są odzyskiwane i musi być negocjowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="931ce-119">Cookies that exceed their lifetime are recycled and need to be negotiated again.</span></span> <span data-ttu-id="931ce-120">Wartość domyślna to "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-120">The default value is "10:00:00".</span></span>|  
|`maxCachedCookies`|<span data-ttu-id="931ce-121">Dodatnia liczba całkowita, która określa maksymalną liczbę plików cookie, które mogą być buforowane.</span><span class="sxs-lookup"><span data-stu-id="931ce-121">A positive integer that specifies the maximum number of cookies that can be cached.</span></span> <span data-ttu-id="931ce-122">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="931ce-122">The default is 1000.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="931ce-123">A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.</span><span class="sxs-lookup"><span data-stu-id="931ce-123">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="931ce-124">Wartość domyślna to "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-124">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="931ce-125">Gdy ta wartość ma wartość domyślną, odbiorca akceptuje wiadomości wraz z sygnaturą czasową w czasie wysyłania się do 5 minut lub wcześniej niż czas wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="931ce-125">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="931ce-126">Komunikaty, które nie przejdą testów czasie wysyłania są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="931ce-126">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="931ce-127">To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="931ce-127">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxPendingSessions`|<span data-ttu-id="931ce-128">Dodatnia liczba całkowita, która określa maksymalną liczbę oczekujących sesji bezpieczeństwa obsługiwanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="931ce-128">A positive integer that specifies the maximum number of pending security sessions that the service supports.</span></span> <span data-ttu-id="931ce-129">Po osiągnięciu tego limitu, wszyscy nowi klienci odbierać błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="931ce-129">When this limit is reached, all new clients receive SOAP faults.</span></span> <span data-ttu-id="931ce-130">Wartość domyślna to 1000.</span><span class="sxs-lookup"><span data-stu-id="931ce-130">The default value is 1000.</span></span>|  
|`maxStatefulNegotiations`|<span data-ttu-id="931ce-131">Dodatnia liczba całkowita określająca liczbę negocjacji zabezpieczeń, które mogą być jednocześnie aktywne.</span><span class="sxs-lookup"><span data-stu-id="931ce-131">A positive integer that specifies the number of security negotiations that can be active concurrently.</span></span> <span data-ttu-id="931ce-132">Sesje negocjacji poza limitem są umieszczane w kolejce i może zostać zrealizowane wyłącznie po udostępnieniu przestrzeni poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="931ce-132">Negotiation sessions in excess of the limit are queued and can only be completed when a space below the limit becomes available.</span></span> <span data-ttu-id="931ce-133">Wartość domyślna to 1024.</span><span class="sxs-lookup"><span data-stu-id="931ce-133">The default value is 1024.</span></span>|  
|`negotiationTimeout`|<span data-ttu-id="931ce-134">A <xref:System.TimeSpan> określający czas istnienia zasad bezpieczeństwa używanego przez kanał.</span><span class="sxs-lookup"><span data-stu-id="931ce-134">A <xref:System.TimeSpan> that specifies the lifetime of the security policy used by channel.</span></span> <span data-ttu-id="931ce-135">Po upływie czasu, podejmuje negocjacje kanału z klientem dla nowych zasad zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="931ce-135">When the time expires, the channel renegotiates with the client for a new security policy.</span></span> <span data-ttu-id="931ce-136">Wartość domyślna to "00: 02:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-136">The default value is "00:02:00".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="931ce-137">Wartość logiczna określająca, czy próbować połączenia używające obsługi wiadomości WS-Reliable będą odnawiane po błędach transportu.</span><span class="sxs-lookup"><span data-stu-id="931ce-137">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="931ce-138">Wartość domyślna to `true`, co oznacza, że są próby nieskończone podejmuje próbę ponownego połączenia.</span><span class="sxs-lookup"><span data-stu-id="931ce-138">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="931ce-139">Cykl jest dzielony przez limit czasu bezczynności, co powoduje, że kanał do zgłoszenia wyjątku, gdy nie można go ponownie.</span><span class="sxs-lookup"><span data-stu-id="931ce-139">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="931ce-140">Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="931ce-140">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="931ce-141">Po przekroczeniu tego limitu najstarsza identyfikator jednorazowy jest usuwany i nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="931ce-141">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="931ce-142">Wartość domyślna wynosi 500 000.</span><span class="sxs-lookup"><span data-stu-id="931ce-142">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="931ce-143">A <xref:System.TimeSpan> , który określa czas, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="931ce-143">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="931ce-144">Po tym czasie komunikat wysłany z tego samego identyfikator jednorazowy jak wysyłane przed nie będą akceptowane.</span><span class="sxs-lookup"><span data-stu-id="931ce-144">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="931ce-145">Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu zapobieganie atakom polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="931ce-145">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="931ce-146">Osoba atakująca może powtarzania komunikatu, po wygaśnięciu okna powtarzania.</span><span class="sxs-lookup"><span data-stu-id="931ce-146">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="931ce-147">Ten komunikat, jednak nie powiedzie się `maxClockSkew` testów, które odrzuca wiadomości z sygnaturami czasowymi czasie wysyłania maksymalnie przez określony czas, które są nowsze lub wcześniejszy niż czas wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="931ce-147">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="931ce-148">A <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="931ce-148">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="931ce-149">Wartość domyślna to "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-149">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="931ce-150">A <xref:System.TimeSpan> , który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza.</span><span class="sxs-lookup"><span data-stu-id="931ce-150">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="931ce-151">Wartość domyślna to "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-151">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="931ce-152">Podczas odnawiania klucza klient i serwer muszą zawsze wysyłanie wiadomości przy użyciu najnowszych dostępnych klucza.</span><span class="sxs-lookup"><span data-stu-id="931ce-152">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="931ce-153">Obie strony będzie akceptować zabezpieczonego za pomocą poprzedni klucz sesji do przerzucania czas wygaśnięcia wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="931ce-153">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="931ce-154">Dodatnią <xref:System.TimeSpan> określający okres ważności sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="931ce-154">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="931ce-155">Wartość domyślna to "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="931ce-155">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="931ce-156">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="931ce-156">Child Elements</span></span>  
 <span data-ttu-id="931ce-157">Brak.</span><span class="sxs-lookup"><span data-stu-id="931ce-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="931ce-158">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="931ce-158">Parent Elements</span></span>  
  
|<span data-ttu-id="931ce-159">Element</span><span class="sxs-lookup"><span data-stu-id="931ce-159">Element</span></span>|<span data-ttu-id="931ce-160">Opis</span><span class="sxs-lookup"><span data-stu-id="931ce-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="931ce-161">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="931ce-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="931ce-162">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="931ce-162">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="931ce-163">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="931ce-163">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="931ce-164">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="931ce-164">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="931ce-165">Uwagi</span><span class="sxs-lookup"><span data-stu-id="931ce-165">Remarks</span></span>  
 <span data-ttu-id="931ce-166">Ustawienia są lokalne, ponieważ nie są publikowane jako część zasad zabezpieczeń usługi i nie ma wpływu na powiązań klienta.</span><span class="sxs-lookup"><span data-stu-id="931ce-166">The settings are local because they are not published as part of the security policy of the service and do not affect the client's binding.</span></span>  
  
 <span data-ttu-id="931ce-167">Następujące atrybuty `localServiceSecuritySettings` elementu mogą pomóc ograniczyć przypadki atak typu "odmowa usługi" (DOS) zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="931ce-167">The following attributes of the `localServiceSecuritySettings` element can help mitigate a denial-of-service (DOS) security attack:</span></span>  
  
-   <span data-ttu-id="931ce-168">`maxCachedCookies`: steruje maksymalną liczbą SecurityContextTokens ograniczony czas, które są buforowane na serwerze po wykonaniu negocjacji SPNEGO lub SSL.</span><span class="sxs-lookup"><span data-stu-id="931ce-168">`maxCachedCookies`: controls the maximum number of time-bounded SecurityContextTokens that are cached by the server after doing SPNEGO or SSL negotiation.</span></span>  
  
-   <span data-ttu-id="931ce-169">`issuedCookieLifetime`: Określa okres istnienia SecurityContextTokens, które są wydawane przez serwer po negocjacji SPNEGO lub SSL.</span><span class="sxs-lookup"><span data-stu-id="931ce-169">`issuedCookieLifetime`: controls the lifetime of the SecurityContextTokens that are issued by the server following SPNEGO or SSL negotiation.</span></span> <span data-ttu-id="931ce-170">Serwer buforuje SecurityContextTokens w tym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="931ce-170">The server caches the SecurityContextTokens for this period of time.</span></span>  
  
-   <span data-ttu-id="931ce-171">`maxPendingSessions`: steruje maksymalną liczbą bezpiecznych konwersacji, które są ustalane na serwerze, ale które zostały przetworzone żadnych komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="931ce-171">`maxPendingSessions`: controls the maximum number of secure conversations that are established at the server but for which no application messages have been processed.</span></span> <span data-ttu-id="931ce-172">Ten limit przydziału uniemożliwia klientom ustanawiania bezpiecznych konwersacji w usłudze, co powoduje Usługa do przechowywania stanu dla każdego klienta, ale nigdy nie za ich pomocą.</span><span class="sxs-lookup"><span data-stu-id="931ce-172">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
-   <span data-ttu-id="931ce-173">`inactivityTimeout`: Określa maksymalny czas czy usługa przechowuje bezpiecznej konwersacji aktywności bez kiedykolwiek odbierania komunikatu aplikacji na nim.</span><span class="sxs-lookup"><span data-stu-id="931ce-173">`inactivityTimeout`: controls the maximum time that the service keeps a secure conversation alive without ever receiving an application message on it.</span></span> <span data-ttu-id="931ce-174">Ten limit przydziału uniemożliwia klientom ustanawiania bezpiecznych konwersacji w usłudze, co powoduje Usługa do przechowywania stanu dla każdego klienta, ale nigdy nie za ich pomocą.</span><span class="sxs-lookup"><span data-stu-id="931ce-174">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
 <span data-ttu-id="931ce-175">W sesji bezpiecznej konwersacji, należy pamiętać, że oba `inactivityTimeout` i `receiveTimeout` atrybutów w powiązaniu mają wpływ na limit czasu sesji.</span><span class="sxs-lookup"><span data-stu-id="931ce-175">In a secure conversation session, note that both `inactivityTimeout` and the `receiveTimeout` attributes on the binding affect session timeout.</span></span> <span data-ttu-id="931ce-176">Krótszą dwóch Określa, kiedy występują przekroczenia limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="931ce-176">The shorter of the two determines when timeouts occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931ce-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="931ce-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="931ce-178">Powiązania</span><span class="sxs-lookup"><span data-stu-id="931ce-178">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="931ce-179">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="931ce-179">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="931ce-180">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="931ce-180">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="931ce-181">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="931ce-181">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="931ce-182">Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="931ce-182">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="931ce-183">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="931ce-183">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)