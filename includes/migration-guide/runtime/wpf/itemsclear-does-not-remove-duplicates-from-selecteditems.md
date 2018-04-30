### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="0a5c5-101">Items.Clear nie powoduje usunięcia duplikaty z SelectedItems</span><span class="sxs-lookup"><span data-stu-id="0a5c5-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0a5c5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0a5c5-102">Details</span></span>|<span data-ttu-id="0a5c5-103">Załóżmy, że selektor (z włączono wybór wielokrotny) wykryto duplikaty jego <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> kolekcji — ten sam element występuje więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="0a5c5-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> collection - the same item appears more than once.</span></span>  <span data-ttu-id="0a5c5-104">Usuwanie tych elementów ze źródła danych (np. przez wywołanie Items.Clear) nie powiodło się usunięcie ich z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; tylko pierwsze wystąpienie zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="0a5c5-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>; only the first instance is removed.</span></span> <span data-ttu-id="0a5c5-105">Ponadto użycie kolejnych <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (np. SelectedItems.Clear()) mogą wystąpić problemy takie jak <xref:System.ArgumentException?displayProperty=name>, ponieważ <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> zawiera elementy, które nie są już w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="0a5c5-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=name>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contains items that are no longer in the data source.</span></span>|
|<span data-ttu-id="0a5c5-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0a5c5-106">Suggestion</span></span>|<span data-ttu-id="0a5c5-107">Uaktualnij program, jeśli to możliwe do .NET 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0a5c5-107">Upgrade if possible to .NET 4.6.2.</span></span>|
|<span data-ttu-id="0a5c5-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="0a5c5-108">Scope</span></span>|<span data-ttu-id="0a5c5-109">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="0a5c5-109">Minor</span></span>|
|<span data-ttu-id="0a5c5-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="0a5c5-110">Version</span></span>|<span data-ttu-id="0a5c5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="0a5c5-111">4.5</span></span>|
|<span data-ttu-id="0a5c5-112">Typ</span><span class="sxs-lookup"><span data-stu-id="0a5c5-112">Type</span></span>|<span data-ttu-id="0a5c5-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0a5c5-113">Runtime</span></span>|
|<span data-ttu-id="0a5c5-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0a5c5-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
