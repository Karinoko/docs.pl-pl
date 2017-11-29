---
title: "Fuslogvw.exe (Podgląd dziennika powiązań zasobów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ad02ade9c9e60e53fa8fb91d9a38d6ec12bc2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="9c39b-102">Fuslogvw.exe (Podgląd dziennika powiązań zasobów)</span><span class="sxs-lookup"><span data-stu-id="9c39b-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>
<span data-ttu-id="9c39b-103">Podgląd dziennika powiązań zestawów wyświetla szczegóły dotyczące powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="9c39b-104">Te informacje pomagają zdiagnozować, dlaczego .NET Framework nie może zlokalizować zestawu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c39b-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="9c39b-105">Te błędy są zazwyczaj wynikiem wdrożenia zestawu w nieprawidłowej lokalizacji, obrazu macierzystego, który przestał być prawidłowy lub niezgodności numerów wersji lub kultur.</span><span class="sxs-lookup"><span data-stu-id="9c39b-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="9c39b-106">Środowisko uruchomieniowe języka wspólnego firmy błędu można znaleźć zestawu zwykle jest wyświetlany jako <xref:System.TypeLoadException> w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c39b-107">Program fuslogvw.exe musi być uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9c39b-107">You must run fuslogvw.exe with administrator privileges.</span></span>  
  
 <span data-ttu-id="9c39b-108">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c39b-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9c39b-109">Aby uruchomić narzędzie, należy użyć wiersz polecenia dewelopera (lub wiersz polecenia programu Visual Studio w systemie Windows 7) z poświadczeniami administratora.</span><span class="sxs-lookup"><span data-stu-id="9c39b-109">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="9c39b-110">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9c39b-110">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="9c39b-111">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9c39b-111">At the command prompt, type the following:</span></span>  
  
```  
fuslogvw  
```  
  
 <span data-ttu-id="9c39b-112">Przeglądarka wyświetla wpis dla każdego nieudanego powiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="9c39b-113">Dla każdego niepowodzenia przeglądarka opisuje aplikację, która zainicjowała powiązanie; zestaw, którego ono dotyczy, w tym nazwę, wersję, kulturę oraz klucz publiczny oraz datę i czas wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>  
  
### <a name="to-change-the-log-location-view"></a><span data-ttu-id="9c39b-114">Aby zmienić widok dziennika lokalizacji</span><span class="sxs-lookup"><span data-stu-id="9c39b-114">To change the log location view</span></span>  
  
1.  <span data-ttu-id="9c39b-115">Wybierz **domyślne** przycisk opcji, aby wyświetlić błędy powiązania dla wszystkich typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="9c39b-116">Domyślnie wpisy dziennika są przechowywane na dysku w katalogach użytkowników, w pamięci podręcznej wininet.</span><span class="sxs-lookup"><span data-stu-id="9c39b-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>  
  
2.  <span data-ttu-id="9c39b-117">Wybierz **niestandardowych** przycisk opcji, aby wyświetlić błędy bind w katalogu niestandardowego, który określisz.</span><span class="sxs-lookup"><span data-stu-id="9c39b-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="9c39b-118">Należy określić niestandardowe lokalizację środowiska uruchomieniowego do przechowywania dzienników ustawiając lokalizacja dziennika niestandardowego w **ustawienia dziennika** okna dialogowego, aby prawidłową nazwą folderu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="9c39b-119">Ten katalog powinien być pusty i zawierać tylko pliki, które generuje środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="9c39b-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="9c39b-120">Jeśli zawiera plik wykonywalny, który generuje błąd, który ma zostać zapisany, błąd nie zostanie zapisany, ponieważ narzędzie spróbuje utworzyć katalog o takiej samej nazwie jak plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="9c39b-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="9c39b-121">Ponadto próba uruchomienia pliku wykonywalnego z lokalizacji dziennika nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="9c39b-121">In addition, an attempt to run an executable from the log location will fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9c39b-122">Domyślna lokalizacja powiązania jest preferowana nad niestandardową lokalizacją powiązania.</span><span class="sxs-lookup"><span data-stu-id="9c39b-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="9c39b-123">Środowisko uruchomieniowe przechowuje w pamięci podręcznej wininet domyślną lokalizację powiązania i dlatego czyści ją automatycznie. Jeśli określisz niestandardową lokalizację powiązania, jesteś także odpowiedzialny za jej czyszczenie.</span><span class="sxs-lookup"><span data-stu-id="9c39b-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>  
  
### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="9c39b-124">Aby wyświetlić szczegóły, dotyczące określonego błędu</span><span class="sxs-lookup"><span data-stu-id="9c39b-124">To view details about a specific failure</span></span>  
  
1.  <span data-ttu-id="9c39b-125">Wybierz nazwę aplikacji dla żądnego wpisu w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="9c39b-125">Select the application name of the desired entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="9c39b-126">Kliknij przycisk **znajdują się w dzienniku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-126">Click the **View Log** button.</span></span> <span data-ttu-id="9c39b-127">Można także kliknąć dwukrotnie wybrany wpis.</span><span class="sxs-lookup"><span data-stu-id="9c39b-127">Alternately, you can double-click the selected entry.</span></span>  
  
     <span data-ttu-id="9c39b-128">W narzędziu są wyświetlane następujące szczegółowe informacje o błędzie wybranego powiązania:</span><span class="sxs-lookup"><span data-stu-id="9c39b-128">The tool displays the following details about the selected bind failure:</span></span>  
  
    -   <span data-ttu-id="9c39b-129">Konkretna przyczyna niepowodzenia powiązania, taka jak „nie odnaleziono pliku” lub „niezgodność wersji”.</span><span class="sxs-lookup"><span data-stu-id="9c39b-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>  
  
    -   <span data-ttu-id="9c39b-130">Informacje o aplikacji, która zainicjowała powiązanie, w tym jej nazwa, katalog główny aplikacji (AppBase) i opis prywatnej ścieżki wyszukiwania, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="9c39b-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>  
  
    -   <span data-ttu-id="9c39b-131">Tożsamość zestawu, którego szuka narzędzie.</span><span class="sxs-lookup"><span data-stu-id="9c39b-131">The identity of the assembly the tool is looking for.</span></span>  
  
    -   <span data-ttu-id="9c39b-132">Opis dowolnych zastosowanych polityk wersji Aplikacji, Wydawcy lub Administratora.</span><span class="sxs-lookup"><span data-stu-id="9c39b-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>  
  
    -   <span data-ttu-id="9c39b-133">Czy zestaw został znaleziony w [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="9c39b-133">Whether the assembly was found in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
    -   <span data-ttu-id="9c39b-134">Lista wszystkich badających adresów URL.</span><span class="sxs-lookup"><span data-stu-id="9c39b-134">A list of all probing URLs.</span></span>  
  
 <span data-ttu-id="9c39b-135">Następujący przykładowy wpis dziennika zawiera szczegółowe informacje na temat nieudanych powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="9c39b-136">Aby usunąć pojedynczy wpis z dziennika</span><span class="sxs-lookup"><span data-stu-id="9c39b-136">To delete a single entry from the log</span></span>  
  
1.  <span data-ttu-id="9c39b-137">Wybierz wpis w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="9c39b-137">Select an entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="9c39b-138">Kliknij przycisk **Usuń wpis** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-138">Click the **Delete Entry** button.</span></span>  
  
### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="9c39b-139">Aby usunąć wszystkie wpisy z dziennika</span><span class="sxs-lookup"><span data-stu-id="9c39b-139">To delete all entries from the log</span></span>  
  
-   <span data-ttu-id="9c39b-140">Kliknij przycisk **usunąć wszystkie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-140">Click the **Delete All** button.</span></span>  
  
### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="9c39b-141">Aby odświeżyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="9c39b-141">To refresh the user interface</span></span>  
  
-   <span data-ttu-id="9c39b-142">Kliknij przycisk **Odśwież** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-142">Click the **Refresh** button.</span></span> <span data-ttu-id="9c39b-143">Przeglądarka nie wykrywa automatycznie nowych wpisów dziennika, kiedy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="9c39b-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="9c39b-144">Należy użyć **Odśwież** przycisk umożliwiający ich wyświetlenie.</span><span class="sxs-lookup"><span data-stu-id="9c39b-144">You must use the **Refresh** button to display them.</span></span>  
  
### <a name="to-change-the-log-settings"></a><span data-ttu-id="9c39b-145">Aby zmienić ustawienia dziennika</span><span class="sxs-lookup"><span data-stu-id="9c39b-145">To change the log settings</span></span>  
  
-   <span data-ttu-id="9c39b-146">Kliknij przycisk **ustawienia** przycisk, aby otworzyć **ustawienia dziennika** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="9c39b-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>  
  
### <a name="to-view-the-about-dialog"></a><span data-ttu-id="9c39b-147">Aby wyświetlić okno dialogowe Informacje</span><span class="sxs-lookup"><span data-stu-id="9c39b-147">To view the About dialog</span></span>  
  
-   <span data-ttu-id="9c39b-148">Kliknij przycisk **o** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-148">Click the **About** button.</span></span>  
  
## <a name="binding-logs-for-native-images"></a><span data-ttu-id="9c39b-149">Dzienniki powiązań dla obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="9c39b-149">Binding Logs for Native Images</span></span>  
 <span data-ttu-id="9c39b-150">Domyślnie Fuslogvw.exe rejestruje normalne żądania powiązania zestawów.</span><span class="sxs-lookup"><span data-stu-id="9c39b-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="9c39b-151">Alternatywnie można rejestrować wiązania zestawu dla obrazów natywnych, które zostały utworzone przy użyciu [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="9c39b-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="9c39b-152">Aby rejestrować powiązania zestawów dla obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="9c39b-152">To log assembly binds for native images</span></span>  
  
-   <span data-ttu-id="9c39b-153">W **kategorie dziennika** grupy wybierz **obrazów macierzystych** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>  
  
 <span data-ttu-id="9c39b-154">Następujący dziennik pokazuje błąd spowodowany przez zależność, która nie istniała, kiedy obraz macierzysty został utworzony dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="9c39b-155">Jeżeli zależności w czasie wykonywania różnią się od zależności po uruchomieniu Ngen.exe, powiązanie z obrazem macierzystym jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="9c39b-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 <span data-ttu-id="9c39b-156">Następujący dziennik wyświetla błąd powiązania obrazu macierzystego, który wystąpił, ponieważ ustawienia zabezpieczeń na komputerze, gdy aplikacja została uruchomiona, różniły się od ustawień zabezpieczeń w momencie utworzenia obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="9c39b-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a><span data-ttu-id="9c39b-157">Okno dialogowe Ustawienia dziennika</span><span class="sxs-lookup"><span data-stu-id="9c39b-157">The Log Settings Dialog</span></span>  
 <span data-ttu-id="9c39b-158">Można użyć **ustawienia dziennika** okna dialogowego, aby wykonać następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="9c39b-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>  
  
#### <a name="to-disable-logging"></a><span data-ttu-id="9c39b-159">Aby wyłączyć rejestrowanie</span><span class="sxs-lookup"><span data-stu-id="9c39b-159">To disable logging</span></span>  
  
-   <span data-ttu-id="9c39b-160">Wybierz **dziennika wyłączone** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="9c39b-161">Należy zauważyć, że ta opcja jest domyślnie zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="9c39b-161">Note that this option is selected by default.</span></span>  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="9c39b-162">Aby rejestrować powiązania zestawu w wyjątkach</span><span class="sxs-lookup"><span data-stu-id="9c39b-162">To log assembly binds in exceptions</span></span>  
  
-   <span data-ttu-id="9c39b-163">Wybierz **Zaloguj tekst wyjątku** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="9c39b-164">Tylko najmniej szczegółowe informacje dziennika łączenia są rejestrowane w tekście wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9c39b-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="9c39b-165">Aby wyświetlić pełne informacje, użyj jednego z innych ustawień.</span><span class="sxs-lookup"><span data-stu-id="9c39b-165">To view full information, use one of the other settings.</span></span>  
  
     <span data-ttu-id="9c39b-166">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="9c39b-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="9c39b-167">Aby rejestrować błędy powiązania zestawów</span><span class="sxs-lookup"><span data-stu-id="9c39b-167">To log assembly bind failures</span></span>  
  
-   <span data-ttu-id="9c39b-168">Wybierz **dziennika błędów bind dysku** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-168">Select the **Log bind failures to disk** option button.</span></span>  
  
     <span data-ttu-id="9c39b-169">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="9c39b-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="9c39b-170">Aby rejestrować wszystkie powiązania zestawów</span><span class="sxs-lookup"><span data-stu-id="9c39b-170">To log all assembly binds</span></span>  
  
-   <span data-ttu-id="9c39b-171">Wybierz **logowania wszystkie powiązania przy użyciu dysku** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-171">Select the **Log all binds to disk** option button.</span></span>  
  
     <span data-ttu-id="9c39b-172">Zobacz Ważne informacje dotyczące zestawów, które są ładowane, jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="9c39b-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c39b-173">Jeśli zestaw jest ładowany jako domena neutralne, na przykład przez ustawienie <xref:System.AppDomainSetup.LoaderOptimization%2A> właściwości <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> lub <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, włączanie rejestrowania może wyciek pamięci w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="9c39b-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="9c39b-174">Może się to zdarzyć, jeśli wpis dziennika jest dodawany, gdy moduł niezależny od domeny jest ładowany do domeny aplikacji, a później domena aplikacji jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="9c39b-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="9c39b-175">Wpis dziennika nie może być zwolniony do czasu zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="9c39b-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="9c39b-176">Niektóre debugery włączają rejestrowanie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9c39b-176">Some debuggers automatically turn on logging.</span></span>  
  
#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="9c39b-177">Aby włączyć niestandardową ścieżkę dziennika</span><span class="sxs-lookup"><span data-stu-id="9c39b-177">To enable a custom log path</span></span>  
  
1.  <span data-ttu-id="9c39b-178">Wybierz **Włącz dziennik niestandardowy ścieżki** przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-178">Select the **Enable custom log path** option button.</span></span>  
  
2.  <span data-ttu-id="9c39b-179">Wprowadź ścieżkę do **ścieżki dziennika niestandardowego** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="9c39b-179">Enter the path into the **Custom log path** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c39b-180">[Podgląd dziennika powiązań zestawów (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) używa pamięci podręcznej programu Internet Explorer (IE) do przechowywania dziennika powiązania.</span><span class="sxs-lookup"><span data-stu-id="9c39b-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="9c39b-181">Z powodu sporadycznych uszkodzenia w pamięci podręcznej programu Internet Explorer [Podgląd dziennika powiązań zestawów (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) można czasami przestanie być wyświetlana nowe dzienniki powiązania w oknie Przeglądanie.</span><span class="sxs-lookup"><span data-stu-id="9c39b-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="9c39b-182">W wyniku tego uszkodzenia infrastruktura powiązań .NET (fusion) nie może zapisywać w dzienniku powiązań ani z niego odczytywać.</span><span class="sxs-lookup"><span data-stu-id="9c39b-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="9c39b-183">(Ten problem nie wystąpi, jeśli używana jest niestandardowa ścieżka dziennika).  Aby naprawić uszkodzenie i umożliwić programowi fusion ponowne wyświetlanie dzienników powiązań, należy wyczyścić pamięć podręczną programu IE poprzez usunięcie tymczasowych plików internetowych w oknie Opcji internetowych programu IE.</span><span class="sxs-lookup"><span data-stu-id="9c39b-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>  
>   
>  <span data-ttu-id="9c39b-184">Jeśli niezarządzanych aplikacji obsługuje środowisko uruchomieniowe języka wspólnego zaimplementowanie `IHostAssemblyManager` i `IHostAssemblyStore` interfejsów, wpisy dziennika nie mogą być przechowywane w pamięci podręcznej wininet.</span><span class="sxs-lookup"><span data-stu-id="9c39b-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="9c39b-185">Aby wyświetlić wpisy dziennika dla hostów niestandardowych, które implementują te interfejsy, należy określić alternatywną ścieżkę dziennika.</span><span class="sxs-lookup"><span data-stu-id="9c39b-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="9c39b-186">Aby włączyć rejestrowanie dla aplikacji działających w kontenerze aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9c39b-186">To enable logging for apps running in the Windows app container</span></span>  
  
1.  <span data-ttu-id="9c39b-187">Należy włączyć niestandardową ścieżkę dziennika, jak opisano w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="9c39b-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="9c39b-188">Domyślnie aplikacje, które są uruchomione w kontenerze aplikacji systemu Windows mają ograniczony dostęp do dysku twardego.</span><span class="sxs-lookup"><span data-stu-id="9c39b-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="9c39b-189">Katalog, który zostanie określony, będzie miał dostęp do odczytu i zapisu dla wszystkich aplikacji z kontenera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c39b-189">The directory you specify will have read/write access for all apps in the app container.</span></span>  
  
2.  <span data-ttu-id="9c39b-190">Wybierz **włączyć rejestrowanie bez ramek** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="9c39b-190">Select the **Enable immersive logging** check box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9c39b-191">To pole jest włączone tylko w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9c39b-191">This box is enabled only on Windows 8 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c39b-192">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c39b-192">See Also</span></span>  
 <xref:System.TypeLoadException>  
 [<span data-ttu-id="9c39b-193">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="9c39b-193">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="9c39b-194">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="9c39b-194">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="9c39b-195">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9c39b-195">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="9c39b-196">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="9c39b-196">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)