### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="f004f-101">SqlConnection.Open w systemie Windows 7 kończy się niepowodzeniem z systemem innym niż — IFS podstawowego dostawcy usługi Winsock lub LSP obecne</span><span class="sxs-lookup"><span data-stu-id="f004f-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f004f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f004f-102">Details</span></span>|<span data-ttu-id="f004f-103"><xref:System.Data.SqlClient.SqlConnection.Open> i <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> Niepowodzenie w programie .NET Framework 4.5, jeśli zostanie uruchomione na komputerze z systemem Windows 7 z systemem innym niż — IFS podstawowego dostawcy usługi Winsock lub LSP znajdują się na komputerze. Aby określić, czy zainstalowano podstawowego dostawcy nie - IFS lub LSP, użyj <code>netsh WinSock Show Catalog</code> polecenia i sprawdź, czy każdy <code>Winsock Catalog Provider Entry</code> elementu, który jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="f004f-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="f004f-104">Jeśli ma wartość flagi usługi <code>0x20000</code> ustawiony bit, dostawca używa uchwytów IFS i będzie pracował prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f004f-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="f004f-105">Jeśli <code>0x20000</code> bit jest wyczyszczone (nie ustawiono), jest podstawowego dostawcy nie - IFS lub LSP.</span><span class="sxs-lookup"><span data-stu-id="f004f-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>|
|<span data-ttu-id="f004f-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f004f-106">Suggestion</span></span>|<span data-ttu-id="f004f-107">Ten błąd został rozwiązany w programie .NET Framework 4.5.2, więc można uniknąć przez uaktualnienie programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f004f-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="f004f-108">Alternatywnie można uniknąć przez usunięcie wszelkich zainstalowanych z systemem innym niż — IFS dostawców LSP interfejsu Winsock.</span><span class="sxs-lookup"><span data-stu-id="f004f-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>|
|<span data-ttu-id="f004f-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="f004f-109">Scope</span></span>|<span data-ttu-id="f004f-110">Pomocnicza</span><span class="sxs-lookup"><span data-stu-id="f004f-110">Minor</span></span>|
|<span data-ttu-id="f004f-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="f004f-111">Version</span></span>|<span data-ttu-id="f004f-112">4.5</span><span class="sxs-lookup"><span data-stu-id="f004f-112">4.5</span></span>|
|<span data-ttu-id="f004f-113">Typ</span><span class="sxs-lookup"><span data-stu-id="f004f-113">Type</span></span>|<span data-ttu-id="f004f-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f004f-114">Runtime</span></span>|
|<span data-ttu-id="f004f-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f004f-115">Affected APIs</span></span>|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
