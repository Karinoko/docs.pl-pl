### <a name="x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="c9634-101">X509Certificate2.toString(bool) nie zgłasza teraz po .NET nie można obsłużyć certyfikatu</span><span class="sxs-lookup"><span data-stu-id="c9634-101">X509Certificate2.ToString(bool) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c9634-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c9634-102">Details</span></span>|<span data-ttu-id="c9634-103">Wcześniej, tej metody spowoduje zgłoszenie Jeśli <code>true</code> została przekazana dla parametru verbose i zostały zainstalowane certyfikaty, które nie były obsługiwane przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9634-103">Previously, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="c9634-104">Teraz metoda powiedzie się i zwraca nieprawidłowy ciąg, który pomija niedostępny części certyfikat.</span><span class="sxs-lookup"><span data-stu-id="c9634-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="c9634-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c9634-105">Suggestion</span></span>|<span data-ttu-id="c9634-106">Każdy kod w zależności od <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> powinny być aktualizowane oczekiwać, że zwrócony ciąg mogą wyłączyć niektóre dane certyfikatu (na przykład klucz publiczny, klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejsu API będzie mieć wcześniej zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="c9634-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="c9634-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="c9634-107">Scope</span></span>|<span data-ttu-id="c9634-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="c9634-108">Edge</span></span>|
|<span data-ttu-id="c9634-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="c9634-109">Version</span></span>|<span data-ttu-id="c9634-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c9634-110">4.6</span></span>|
|<span data-ttu-id="c9634-111">Typ</span><span class="sxs-lookup"><span data-stu-id="c9634-111">Type</span></span>|<span data-ttu-id="c9634-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c9634-112">Runtime</span></span>|
|<span data-ttu-id="c9634-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c9634-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
