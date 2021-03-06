---
title: '&lt;AppContextSwitchOverrides&gt; — Element'
ms.custom: updateeachrelease
ms.date: 09/19/2018
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2a81c4ec4f679b99f5f5a4d2a2c21270691e93
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839806"
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; — Element
Definiuje co najmniej jeden przełączniki posługują się <xref:System.AppContext> Aby klasa zapewniała mechanizm rezygnacji z nowych funkcji.  
  
 \<Konfiguracja >  
 \<runtime>  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany.<br /><br /> Definiuje co najmniej jedną nazwę przełącznika i ich skojarzone wartości logiczne.|  
  
### <a name="value-attribute"></a>wartość atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|"nazwa = wartość"|Nazwa przełącznika wstępnie zdefiniowany wraz z jego wartość (`true` lub `false`). Wiele pary nazwa/wartość przełącznika są oddzielone średnikami (";"). Aby uzyskać listę nazw wstępnie zdefiniowanych przełączników, obsługiwane przez program .NET Framework Zobacz sekcję Uwagi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu .NET Framework 4.6 `<AppContextSwitchOverrides>` elementu w pliku konfiguracji umożliwia wywołań interfejsu API, aby ustalić, czy jego aplikacja może korzystać z zalet nowych funkcji lub zachowania zgodności z poprzednimi wersjami biblioteki. Na przykład, jeśli zachowanie interfejsu API została zmieniona między dwoma wersjami biblioteki `<AppContextSwitchOverrides>` element pozwala obiektom wywołującym tego interfejsu API, aby zrezygnować z nowego zachowania na wersje biblioteki, które obsługują nowe funkcje. Dla aplikacji, które wywoływania interfejsów API na platformie .NET Framework `<AppContextSwitchOverrides>` element można również zezwolić wywoływania, w których aplikacje są przeznaczone dla starszej wersji programu .NET Framework, aby skorzystać z nowych funkcji, jeśli jego aplikacja jest uruchomiona na wersję .NET Framework, który zawiera funkcje.  
  
 `value` Atrybutu `<AppContextSwitchOverrides>` element składa się z pojedynczy ciąg, który składa się z jednego lub więcej par nazwa/wartość rozdzielaną średnikami.  Każda nazwa identyfikuje przełącznik zgodności, a jego wartość jest wartością logiczną (`true` lub `false`) oznacza to, czy przełącznik jest ustawiona. Domyślnie jest `false`, i udostępnia nowych funkcji w bibliotekach. Tylko zapewniają poprzednie funkcjonalności Jeśli przełącznik ma wartość (jego wartość jest `true`). Dzięki temu biblioteki, aby podać nowe zachowanie dla istniejących interfejsów API, zezwalając obiektów wywołujących, które zależą od poprzedniego zachowania, aby zrezygnować z nowych funkcji.  
  
 .NET Framework obsługuje następujące parametry:  
  
|Nazwa przełącznika|Opis|Wprowadzono|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Określa, czy Windows Presentation Foundation używa starszej wersji jest algorytm dla określania układu. Aby uzyskać więcej informacji, zobacz [ograniczenie: układ platformy WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Określa, czy domyślny algorytm używany do podpisywania części pakietu przez PackageDigitalSignatureManager jest algorytm SHA1 lub SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Po ustawieniu `false`, umożliwia debugowanie projektów opartych na XAML przepływu pracy z programem Visual Studio, gdy Standard FIPS jest włączony. Bez tego <xref:System.NullReferenceException> jest zgłaszany w wywołaniach do metod w zestawie System.Activities.|.NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Określa, czy sumy kontrolnej dla wystąpienia przepływu pracy w debugerze, używa algorytmu MD5 lub SHA1. | .NET framework 4.7|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Określa, czy ślady stosu uzyskać przy użyciu przenośnych plików PDB może zawierać informacje o pliku i wierszu źródła. `false` Aby dołączyć pliku i wierszu informacji o źródle; w przeciwnym razie `true`.|.NET framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Formanty czy <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek podczas <xref:System.Drawing.Icon> obiekt ma ramek PNG. Aby uzyskać więcej informacji, zobacz [środki zaradcze: PNG ramki w obiektach ikonę](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Określa, czy <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> obiekty są prawidłowo usunięte, po dodaniu do kolekcji przy <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> metody. `true` Aby zachować starsze zachowanie; `false` do usuwania wszystkich obiektów prywatnej czcionki. |.NET framework 4.7.2|
|`Switch.System.Drawing.Printing.`</br>`OptimizePrintPreview`|Formanty czy wydajność <xref:System.Windows.Forms.PrintPreviewDialog> została zoptymalizowana pod kątem drukarek sieciowych. Aby uzyskać więcej informacji, zobacz [printpreviewdialog — informacje o formancie](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Określa, czy operacje asynchroniczne nie przepływać z kontekstu wątku wywołującego. Aby uzyskać więcej informacji, zobacz [CurrentCulture i CurrentUICulture przepływać przez zadania](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Formanty czy <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda próbuje dopasować typ oświadczenia tylko w przypadku ostatni wpis DNS. Aby uzyskać więcej informacji, zobacz [środki zaradcze: metoda X509CertificateClaimSet.FindClaims](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Określa, czy zezwalać na AuthorizationContext.Empty zwracać obiektu modyfikowalnego.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Formanty czy ścieżki dłuższe niż `MAX_PATH` throw (260 znaków) <xref:System.IO.PathTooLongException>. Aby uzyskać więcej informacji, zobacz [długa ścieżka pomocy technicznej](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Określa, czy macierzystym procedury systemu operacyjnego są używane do dekompresji przez <xref:System.IO.Compression.DeflateStream> klasy. `false` Aby użyć natywnych interfejsów API; `true` używać <xref:System.IO.Compression.DeflateStream> implementacji.|.NET framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Używa ukośnik odwrotny ("\\") zamiast ukośnika ("/") jako separatora ścieżki w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości. Aby uzyskać więcej informacji, zobacz [środki zaradcze: separatora ścieżki ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Określa, czy wyjątki systemowe, które są generowane na wątkach w tle utworzonych za pomocą działania <xref:System.IO.Ports.SerialPort> strumieni zakończyć proces.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Określa, czy ścieżki starszych normalizacji jest używana i ścieżek identyfikatora URI są obsługiwane przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody. Aby uzyskać więcej informacji, zobacz [środki zaradcze: ścieżka normalizacji](~/docs/framework/migration-guide/mitigation-path-normalization.md) i [środki zaradcze: sprawdza dwukropek, ścieżkę](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Określa, czy test porównuje równość <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> właściwości jednego obiektu z <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> drugiego obiektu. Aby uzyskać więcej informacji, zobacz [nieprawidłowa implementacja MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Wyłącza certyfikatu weryfikacji identyfikatora (OID) obiektu rozszerzonego użycia klucza (EKU). Rozszerzenie rozszerzone użycie klucza (EKU) to zbiór identyfikatorów obiektów (OID), które wskazują aplikacje, które używają klucza.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Wyłącza środki zaradcze TLS1.0 przeglądarki wykorzystać przeciwko SSL/TLS (BEAST), wyłączając użytkowania SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Formanty czy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> i <xref:System.Net.Security.SslStream?displayProperty=nameWithType> klasy mogą używać protokołu SSL 3.0. Aby uzyskać więcej informacji, zobacz [ograniczenie: protokoły TLS](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Wyłącza wersje protokołu TLS SystemDefault powracanie do domyślnej Tls12, Tls11, Tls.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Wyłącza alerty po stronie serwera SslStream TLS.|.NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Formanty czy [klasa DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializuje niektórych znaków kontrolnych opartych na standardach wersji ECMAScript 6 i V8. Aby uzyskać więcej informacji, zobacz [środki zaradcze: serializacja znaki kontrolne przy użyciu elementu DataContractJsonSerializer](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Formanty czy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje wiele dostosowań lub tylko jednego dopasowania dla strefy czasowej. Jeśli `true`, używa ona <xref:System.TimeZoneInfo> typ do serializacji i deserializacji danych daty i godziny; w przeciwnym razie używa <xref:System.TimeZone> typ, który nie obsługuje wielu reguł dopasowania.|.NET Framework 4.6.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Formanty czy <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> Konstruktor Ustawia nowy obiekt <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> właściwość o istniejące odwołanie do obiektu. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Konstruktor ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Formanty czy próba ponownego użycia <xref:System.Security.Cryptography.AesCryptoServiceProvider> zgłasza odszyfrowujący <xref:System.Security.Cryptography.CryptographicException>. Aby uzyskać więcej informacji, zobacz [odszyfrowujący AesCryptoServiceProvider zapewnia wielokrotnego użytku przekształcenie](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Formanty czy wartość [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) właściwość [IntPtr](xref:System.IntPtr) czy reprezentuje lokalizację w pamięci okna obsługi, lub czy jest to uchwyt okna (HWND). Aby uzyskać więcej informacji, zobacz [środki zaradcze: CspParameters.ParentWindowHandle oczekuje HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedCMS jest algorytm SHA1 lub SHA256. |.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Określa, czy wartość domyślna dla niektórych operacji SignedXML jest algorytm SHA1 lub SHA256. |.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Określa, czy `TransportWithMessageCredential` tryb zabezpieczeń umożliwia komunikatów za pomocą niepodpisany "nagłówek do". Jest to przełącznik zgłoszenie zgody na uczestnictwo. Aby uzyskać więcej informacji, zobacz [zmiany środowiska uruchomieniowego w programie .NET Framework 4.6.1](~/docs/framework/migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Formanty czy <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Konstruktor wyrzuca <xref:System.ArgumentException> po spełnieniu jednego z elementów `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Określa, czy próbę użycia X509 certyfikatów przy użyciu dostawcy magazynu kluczy CSG zgłasza wyjątek. Aby uzyskać więcej informacji, zobacz [WCF transport security obsługuje certyfikaty przechowywane przy użyciu CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Korzystając z protokołu HTTP przy użyciu samodzielnie hostowanej usługi, ustawienie tej wartości na `true` powoduje, że usługi WCF do ignorowania dodawania aplikacji `Connection: close` nagłówka do nagłówków odpowiedzi na żądanie. Ustawienie tej wartości na `false` umożliwia dodawanie `Connection: close` nagłówka do nagłówków odpowiedzi, co powoduje zamknięcie gniazda żądania po wysłaniu odpowiedzi.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Obsługuje zakleszczenia wynikających z ograniczenia wystąpień usługi współużytkowane do pojedynczego wątku wykonania w danym momencie.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Wraz z `Switch.System.Net.DontEnableSchUseStrongCrypto`, określa, czy zabezpieczenie wiadomości WCF używa protokołu TLS 1.1 i TLS 1.2.|.NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Wartość `false` ustawia domyślną konfigurację, aby system operacyjny wybrać protokół. Wartość `true` ustawiana domyślnie do protokołu najwyższy dostępny. (Ta funkcja jest dostępna również na gałąź z poprzednich wersji w ramach obsługi)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Określa, czy komunikat domyślny algorytm dla wiadomości usługi MSMQ w usłudze WCF podpisywania jest algorytm SHA1 lub SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Określa, czy WCF używa SHA1 lub skrót SHA256 do wygenerowania losowych nazw dla nazwanych potoków.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Określa, czy [obiektu NullReferenceException](xref:System.NullReferenceException) kiedy komunikat o wyjątku ma wartość null.|.NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Określa, czy wyjątki generowane podczas uruchamiania usługi są propagowane do obiektu wywołującego <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> metody.|.NET Framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Określa, czy niektóre zakodowane w formacie procent, które zostały czasami zdekodowany teraz spójnie lewej kodowania znaków. Jeśli `true`, są one zdekodowany; w przeciwnym razie `false`.|.NET framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Określa obsługi znaków dwukierunkowy Unicode w identyfikatorach URI. `true` Aby usunąć je z identyfikatorów URI; `false` zachowanie i procent zakodować je.|.NET framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Określa, czy Windows Presentation Foundation mają zastosowanie stary algorytm (`true`) lub nowy algorytm (`false`) w przydzielanie miejsca, aby \*-kolumn. Aby uzyskać więcej informacji, zobacz [środki zaradcze: przydzielenie miejsca na formant siatki do kolumn Star](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Zdarzenie zmiany formanty czy selektora lub kartę sterowania zawsze aktualizuje wartość jego właściwości wybranej wartości przed zgłoszeniem zaznaczenia.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Określa, czy renderowanie na podstawie zaznaczenia — moduł definiowania układu dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> kontroli w celu zapobieżenia zamknięte tekstu (`false`), lub czy renderowania tekstu tylko w warstwie moduł definiowania układu kodu (`true`).|.NET framework 4.7.2|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Określa, czy wartość DPI zmianach w na systemie (wartość `false`) lub według poszczególnych monitorów (wartość `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Określa, czy deweloper musi obsługiwać specjalnie <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> akcji, gdy tekst kontrolki jest obecna. `true` Aby obsłużyć <xref:System.Windows.Forms.DomainUpDown.UpButton> działania. `false` dla <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> i <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akcji mają być prawidłowo synchronizowany.|.NET framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Oznacza brak kod, który umożliwia niestandardowego zgody <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji bezpiecznie filtrować wiadomości bez zgłaszania wyjątku podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana. Aby uzyskać więcej informacji, zobacz [środki zaradcze: niestandardowe IMessageFilter.PreFilterMessage implementacje](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Określa, czy <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> właściwość zwraca kontroli źródła, gdy użytkownik otwiera menu z zagnieżdżoną <xref:System.Windows.Forms.ToolStripMenuItem> kontroli. `true` Aby zwrócić `null`, starsze zachowanie; `false` do zwrócenia do kontroli źródła.|.NET framework 4.7.2|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Określa, czy jest to opcjonalne `WM_POINTER`— oparte na dotyku/pióro stosu jest włączona w aplikacjach WPF. Aby uzyskać więcej informacji, zobacz [środki zaradcze: oparte na wskaźnikach Dotyk i pomocy technicznej pióra](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Określa, czy domyślny algorytm skrótu używany do sumy kontrolne SHA256 (`false`) lub SHA1 (`true`).|.NET framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Określa, czy starszej [obiektu NullReferenceException](xref:System.NullReferenceException) jest generowany, a nie wyjątek, który wskazuje, w szczególności przyczyną wyjątku (takie jak [directorynotfoundexception —](xref:System.IO.DirectoryNotFoundException) lub [ FileNotFoundException](xref:System.IO.FileNotFoundException). Jest on przeznaczony do użytku przez kod, który zależy od obsługi [obiektu NullReferenceException](xref:System.NullReferenceException). | .NET framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Formanty dostępne począwszy od programu .NET Framework 4.7.1 funkcje ułatwień dostępu są włączone czy wyłączone. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Formanty, czy funkcje są dostępne w programie .NET Framework 4.7.2 ułatwień dostępu są włączane (`false`) lub wyłączony (`true`). Jeśli `true`, `Switch.UseLegacyAccessibilityFeatures` musi być także `true` Aby włączyć funkcje ułatwień dostępu w programie .NET Framework 4.7.1.|.NET framework 4.7.2|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Określa, czy pusta sekwencja klucza w klucze złożone są ignorowane przez sprawdzanie poprawności schematu XSD. Aby uzyskać więcej informacji, zobacz [środki zaradcze: Walidacja schematu XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Zamiast opcji dodawania `AppContextSwitchOverrides` elementu do pliku konfiguracji aplikacji, można również ustawić przełączników programowo przez wywołanie metody `static` (w języku C#) lub `Shared` (w języku Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.  
  
 Biblioteka deweloperzy mogą również definiować niestandardowe przełączników, aby umożliwić wywołującym zrezygnować z zmienione funkcje wprowadzone w nowszych bibliotek. Aby uzyskać więcej informacji, zobacz <xref:System.AppContext> klasy.  
  
## <a name="switches-in-aspnet-applications"></a>Przełączniki w aplikacjach ASP.NET

Można skonfigurować aplikację ASP.NET, aby użyć ustawień zgodności, dodając [ \<Dodaj >](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) elementu [ \<appSettings >](~/docs/framework/configure-apps/file-schema/appsettings/index.md) sekcja pliku web.config. 

W poniższym przykładzie użyto `<add>` elementu do dodania dwóch ustawień `<appSettings>` sekcja pliku web.config:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Przykład

 W poniższym przykładzie użyto `AppContextSwitchOverrides` elementu, aby zdefiniować przełącznikiem zgodność z pojedynczą aplikacją `Switch.System.Globalization.NoAsyncCurrentCulture`, który uniemożliwia przechodzącym przez wątki w wywołaniach metody asynchronicznej przez kulturę.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 W poniższym przykładzie użyto `AppContextSwitchOverrides` elementu, aby zdefiniować dwa przełączniki zgodności aplikacji `Switch.System.Globalization.NoAsyncCurrentCulture` i `Switch.System.IO.BlockLongPaths`. Należy pamiętać, że średnik oddziela dwie pary nazwa/wartość.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<środowisko uruchomieniowe > Element](runtime-element.md)  
 [\<Konfiguracja > Element](../configuration-element.md)
