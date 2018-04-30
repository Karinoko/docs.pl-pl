### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="e4c90-101">Wiązania WCF za pomocą trybu zabezpieczeń TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e4c90-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4c90-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e4c90-102">Details</span></span>|<span data-ttu-id="e4c90-103">Począwszy od programu .NET Framework 4.6.1, powiązania WCF, która używa trybu zabezpieczeń TransportWithMessageCredential można skonfigurować do odbierania wiadomości z niepodpisanych &quot;do&quot; nagłówki dla kluczy asymetrycznych zabezpieczeń. Domyślnie niepodpisane &quot;do&quot; nagłówków będą w dalszym ciągu odrzucone w .NET 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="e4c90-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET 4.6.1.</span></span> <span data-ttu-id="e4c90-104">One tylko będą akceptowane, jeśli ten nowy tryb działania za pomocą przełącznika konfiguracji Switch.System.ServiceModel.AllowUnsignedToHeader wybranych aplikacji. Ponieważ jest to funkcji opcjonalnych, nie powinna wpływać na działanie istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4c90-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span>|
|<span data-ttu-id="e4c90-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e4c90-105">Suggestion</span></span>|<span data-ttu-id="e4c90-106">Ponieważ jest to funkcji opcjonalnych, nie powinna wpływać na działanie istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4c90-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span> <span data-ttu-id="e4c90-107">Aby kontrolować, czy nowe zachowanie jest używany, należy użyć następującego ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="e4c90-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e4c90-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="e4c90-108">Scope</span></span>|<span data-ttu-id="e4c90-109">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="e4c90-109">Transparent</span></span>|
|<span data-ttu-id="e4c90-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="e4c90-110">Version</span></span>|<span data-ttu-id="e4c90-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="e4c90-111">4.6.1</span></span>|
|<span data-ttu-id="e4c90-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e4c90-112">Type</span></span>|<span data-ttu-id="e4c90-113">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="e4c90-113">Retargeting</span></span>|
|<span data-ttu-id="e4c90-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e4c90-114">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
