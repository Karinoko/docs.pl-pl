---
title: '&lt;security&gt; w &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f552e12e98e1fd760a9b36f6984a41a32f96533f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192528"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a>&lt;security&gt; w &lt;wsHttpBinding&gt;
Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsHttpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|— Opcjonalne. Określa typ zabezpieczeń, która jest stosowana. Wartość domyślna to `Message`.<br />— Ten atrybut jest typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Tryb atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Transportu|Zabezpieczenia przy użyciu protokołu HTTPS. Usługa musi zostać skonfigurowane przy użyciu certyfikatów SSL. Komunikat jest całkowicie zabezpieczony przy użyciu protokołu HTTPS i jest uwierzytelniany przez klienta za pomocą certyfikatu SSL usługi. Uwierzytelnianie klienta jest kontrolowany za pośrednictwem `ClientCredentials` atrybutu. z [ \<transportu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).|  
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP. Domyślnie treści protokołu SOAP jest zaszyfrowana i podpisana. Ten tryb zapewnia szeroką gamę funkcji, takich jak tego, czy poświadczenia usługi są dostępne pod adresem klientem poza pasmem, pakiet algorytmów, używać oraz poziom ochrony do zastosowania do treści wiadomości za pomocą właściwości Security.Message. Uwierzytelnianie klienta jest wykonywane raz na sesji i wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
|TransportWithMessageCredential|W tym trybie HTTPS zapewnia integralność, poufność i uwierzytelniania serwera i zabezpieczenia wiadomości protokołu SOAP zapewnia uwierzytelnianie klienta. Domyślnie uwierzytelnianie klienta jest wykonywane raz na sesję, a wyniki uwierzytelniania są buforowane na czas trwania sesji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<transport >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|Określa ustawienia zabezpieczenia transportu. Ten element odnosi się do <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiadomości. Ten element odnosi się do <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Bezpiecznego powiązania aplikacji transportu HTTP.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa WSHttpBinding zaprojektowano pod kątem współdziałanie z usługami, które implementują WS-* specyfikacji. Zabezpieczenia transportu dla tego powiązania jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP lub HTTPS.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
