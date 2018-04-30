### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="6b4d1-101">NullReferenceException w kodu z ImageSourceConverter.ConvertFrom obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="6b4d1-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6b4d1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6b4d1-102">Details</span></span>|<span data-ttu-id="6b4d1-103">Wystąpił błąd w kodu dla obsługi wyjątków <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> spowodowane przez niepoprawny <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany zamiast zamierzone wyjątek (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> lub <xref:System.IO.FileNotFoundException?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="6b4d1-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=name> to be thrown instead of the intended exception (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> or <xref:System.IO.FileNotFoundException?displayProperty=name>).</span></span> <span data-ttu-id="6b4d1-104">Ta zmiana poprawia tego błędu, aby metoda teraz zgłasza wyjątek prawo.</span><span class="sxs-lookup"><span data-stu-id="6b4d1-104">This change corrects that error so that the method now throws the right exception.</span></span> <span data-ttu-id="6b4d1-105">Dzięki domyślne wszystkich aplikacji przeznaczonych dla platformy .NET Framework 4.6.2 i poniżej będzie zgłaszać <xref:System.NullReferenceException?displayProperty=name> dla deweloperów korzystających z platformy .NET Framework 4.7 zachowania zgodności i powyżej powinna zostać wyświetlona prawo wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6b4d1-105">By default all applications targeting .NET Framework 4.6.2 and below will continue to throw <xref:System.NullReferenceException?displayProperty=name> for compatibility, developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>|
|<span data-ttu-id="6b4d1-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6b4d1-106">Suggestion</span></span>|<span data-ttu-id="6b4d1-107">Deweloperów, którzy chcą, aby powrócić do pobierania <xref:System.NullReferenceException?displayProperty=name> po przeznaczonych dla platformy .NET Framework 4.7 bądź nowsza można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:</span><span class="sxs-lookup"><span data-stu-id="6b4d1-107">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=name> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span><pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="6b4d1-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="6b4d1-108">Scope</span></span>|<span data-ttu-id="6b4d1-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="6b4d1-109">Edge</span></span>|
|<span data-ttu-id="6b4d1-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="6b4d1-110">Version</span></span>|<span data-ttu-id="6b4d1-111">4.7</span><span class="sxs-lookup"><span data-stu-id="6b4d1-111">4.7</span></span>|
|<span data-ttu-id="6b4d1-112">Typ</span><span class="sxs-lookup"><span data-stu-id="6b4d1-112">Type</span></span>|<span data-ttu-id="6b4d1-113">Przekierowania</span><span class="sxs-lookup"><span data-stu-id="6b4d1-113">Retargeting</span></span>|
|<span data-ttu-id="6b4d1-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6b4d1-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
