### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="90b99-101">ObjectContext.Translate i ObjectContext.ExecuteStoreQuery obsługują teraz typu wyliczenia</span><span class="sxs-lookup"><span data-stu-id="90b99-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

|   |   |
|---|---|
|<span data-ttu-id="90b99-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="90b99-102">Details</span></span>|<span data-ttu-id="90b99-103">W .NET 4.0, parametru ogólnego <code>T</code> z <code>ObjectContext.Translate</code> i <code>ObjectContext.ExecuteStoreQuery</code> metody może nie być wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="90b99-103">In .NET 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="90b99-104">W tym scenariuszu jest teraz obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90b99-104">That scenario is now supported.</span></span>|
|<span data-ttu-id="90b99-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="90b99-105">Suggestion</span></span>|<span data-ttu-id="90b99-106">Jeśli Przetłumacz lub ExecuteStoreQuery została wywołana dla typu wyliczeniowego w programie .NET 4.0, "0" została zwrócona.</span><span class="sxs-lookup"><span data-stu-id="90b99-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET 4.0, '0' was returned.</span></span> <span data-ttu-id="90b99-107">Jeśli to zachowanie pożądane, wywołań ma być zastąpiona stała 0 (lub odpowiednik wyliczenia go).</span><span class="sxs-lookup"><span data-stu-id="90b99-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>|
|<span data-ttu-id="90b99-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="90b99-108">Scope</span></span>|<span data-ttu-id="90b99-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="90b99-109">Edge</span></span>|
|<span data-ttu-id="90b99-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="90b99-110">Version</span></span>|<span data-ttu-id="90b99-111">4.5</span><span class="sxs-lookup"><span data-stu-id="90b99-111">4.5</span></span>|
|<span data-ttu-id="90b99-112">Typ</span><span class="sxs-lookup"><span data-stu-id="90b99-112">Type</span></span>|<span data-ttu-id="90b99-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="90b99-113">Runtime</span></span>|
|<span data-ttu-id="90b99-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="90b99-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
