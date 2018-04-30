### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="a3290-101">Zakleszczenie może powodować podczas korzystania z usługi współużytkowane</span><span class="sxs-lookup"><span data-stu-id="a3290-101">Deadlock may result when using Reentrant services</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a3290-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a3290-102">Details</span></span>|<span data-ttu-id="a3290-103">Zakleszczenie może skutkować współużytkowane usługi, który ogranicza wystąpień usługi jeden wątek na raz.</span><span class="sxs-lookup"><span data-stu-id="a3290-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="a3290-104">Usługi podatne na ten problem będzie występował będzie mieć następujące <xref:System.ServiceModel.ServiceBehaviorAttribute> w ich kodu:</span><span class="sxs-lookup"><span data-stu-id="a3290-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span><pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]&#13;&#10;</code></pre>|
|<span data-ttu-id="a3290-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a3290-105">Suggestion</span></span>|<span data-ttu-id="a3290-106">Aby rozwiązać ten problem, można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a3290-106">To address this issue, you can do the following:</span></span><ul><li><span data-ttu-id="a3290-107">Ustaw tryb współbieżności usługi <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> lub &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span><span class="sxs-lookup"><span data-stu-id="a3290-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="a3290-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a3290-108">For example:</span></span></li></ul><pre><code class="language-csharp">[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single)]&#13;&#10;</code></pre><ul><li><span data-ttu-id="a3290-109">Zainstaluj najnowszą aktualizację programu .NET Framework 4.6.2, lub Uaktualnij do nowszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3290-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="a3290-110">Powoduje wyłączenie przepływ <xref:System.Threading.ExecutionContext> w <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a3290-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a3290-111">To zachowanie jest konfigurowalne; odpowiada to dodanie następującego ustawienia app do pliku konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a3290-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span></li></ul><pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&#13;&#10;The value of &#39;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&#39; should never be set to &#39;false&#39; for Rentrant services.&#13;&#10;</code></pre>|
|<span data-ttu-id="a3290-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="a3290-112">Scope</span></span>|<span data-ttu-id="a3290-113">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="a3290-113">Minor</span></span>|
|<span data-ttu-id="a3290-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="a3290-114">Version</span></span>|<span data-ttu-id="a3290-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a3290-115">4.6.2</span></span>|
|<span data-ttu-id="a3290-116">Typ</span><span class="sxs-lookup"><span data-stu-id="a3290-116">Type</span></span>|<span data-ttu-id="a3290-117">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="a3290-117">Retargeting</span></span>|
|<span data-ttu-id="a3290-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a3290-118">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType></li></ul>|
