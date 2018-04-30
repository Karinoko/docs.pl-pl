### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="ac23b-101">Profilowanie aplikacji ASP.Net MVC4 może prowadzić do krytyczny błąd aparatu wykonywania</span><span class="sxs-lookup"><span data-stu-id="ac23b-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ac23b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ac23b-102">Details</span></span>|<span data-ttu-id="ac23b-103">Używanie zestawów narzędzia NGEN/profile profilowania może ulec awarii PROFILOWANEGO aplikacji platformy ASP.NET MVC 4 przy uruchamianiu z "Wykonywania aparatu wyjątek krytyczny"</span><span class="sxs-lookup"><span data-stu-id="ac23b-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="ac23b-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ac23b-104">Suggestion</span></span>|<span data-ttu-id="ac23b-105">Tego problemu w programie .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="ac23b-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="ac23b-106">Alternatywnie profilera mogą uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ac23b-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="ac23b-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="ac23b-107">Scope</span></span>|<span data-ttu-id="ac23b-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="ac23b-108">Edge</span></span>|
|<span data-ttu-id="ac23b-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="ac23b-109">Version</span></span>|<span data-ttu-id="ac23b-110">4.5</span><span class="sxs-lookup"><span data-stu-id="ac23b-110">4.5</span></span>|
|<span data-ttu-id="ac23b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="ac23b-111">Type</span></span>|<span data-ttu-id="ac23b-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ac23b-112">Runtime</span></span>|
