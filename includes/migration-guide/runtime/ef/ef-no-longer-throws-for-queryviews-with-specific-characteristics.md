### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="55a2b-101">EF już zgłasza dla QueryViews o określonej charakterystyce</span><span class="sxs-lookup"><span data-stu-id="55a2b-101">EF no longer throws for QueryViews with specific characteristics</span></span>

|   |   |
|---|---|
|<span data-ttu-id="55a2b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="55a2b-102">Details</span></span>|<span data-ttu-id="55a2b-103">Entity Framework już zgłasza <xref:System.StackOverflowException?displayProperty=name> wyjątku, gdy aplikacja wykonuje zapytania, która obejmuje QueryView z od 0 do 1 właściwość nawigacji, który próbuje dołączyć powiązanych jednostek w ramach zapytania.</span><span class="sxs-lookup"><span data-stu-id="55a2b-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=name> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="55a2b-104">Na przykład wywołując <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="55a2b-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>|
|<span data-ttu-id="55a2b-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="55a2b-105">Suggestion</span></span>|<span data-ttu-id="55a2b-106">Ta zmiana wpływa tylko na kod, który używa QueryViews z 1-od 0 do 1 relacje uruchomiona kwerendę dotyczącą tego wywołania. Obejmują.</span><span class="sxs-lookup"><span data-stu-id="55a2b-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="55a2b-107">Zwiększa niezawodność, a powinny być przezroczyste do niemal wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55a2b-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="55a2b-108">Jednak jeśli spowoduje nieoczekiwane zachowanie, można wyłączyć ją, dodając następujący wpis do <code>&lt;appSettings&gt;</code> sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="55a2b-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="language-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="55a2b-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="55a2b-109">Scope</span></span>|<span data-ttu-id="55a2b-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="55a2b-110">Edge</span></span>|
|<span data-ttu-id="55a2b-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="55a2b-111">Version</span></span>|<span data-ttu-id="55a2b-112">4.5.2</span><span class="sxs-lookup"><span data-stu-id="55a2b-112">4.5.2</span></span>|
|<span data-ttu-id="55a2b-113">Typ</span><span class="sxs-lookup"><span data-stu-id="55a2b-113">Type</span></span>|<span data-ttu-id="55a2b-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="55a2b-114">Runtime</span></span>|
