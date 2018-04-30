### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="a2a6b-101">Właściwość CheckForOverflowUnderflow w kontrolce teraz ma wartość true dla System.Drawing</span><span class="sxs-lookup"><span data-stu-id="a2a6b-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a2a6b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a2a6b-102">Details</span></span>|<span data-ttu-id="a2a6b-103">Właściwość CheckForOverflowUnderflow dla zestawu System.Drawing.dll jest ustawiona na true.</span><span class="sxs-lookup"><span data-stu-id="a2a6b-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="a2a6b-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a2a6b-104">Suggestion</span></span>|<span data-ttu-id="a2a6b-105">Poprzednio po wystąpieniu przepełnienia wynik zostałby dyskretnie obcięty.</span><span class="sxs-lookup"><span data-stu-id="a2a6b-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="a2a6b-106">Teraz <xref:System.OverflowException?displayProperty=name> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a2a6b-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="a2a6b-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="a2a6b-107">Scope</span></span>|<span data-ttu-id="a2a6b-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="a2a6b-108">Edge</span></span>|
|<span data-ttu-id="a2a6b-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="a2a6b-109">Version</span></span>|<span data-ttu-id="a2a6b-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a2a6b-110">4.5</span></span>|
|<span data-ttu-id="a2a6b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a2a6b-111">Type</span></span>|<span data-ttu-id="a2a6b-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a2a6b-112">Runtime</span></span>|
