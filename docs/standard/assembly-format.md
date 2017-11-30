---
title: Format pliku zestawu .NET
description: "Dowiedz się więcej o formacie pliku zestawu .NET, który jest używany do opisywania i zawierają aplikacji .NET i bibliotek."
keywords: .NET, .NET core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 797bd4a7c160feda69a3190d9e364b166a51c703
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="net-assembly-file-format"></a><span data-ttu-id="4e6b7-104">Format pliku zestawu .NET</span><span class="sxs-lookup"><span data-stu-id="4e6b7-104">.NET Assembly File Format</span></span>

<span data-ttu-id="4e6b7-105">.NET definiuje format pliku binarnego — "zestawu" — służy do pełni opisywania i zawierają programy .NET.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-105">.NET defines a binary file format - "assembly" - that is used to fully-describe and contain .NET programs.</span></span> <span data-ttu-id="4e6b7-106">Zestawy są używane do samych programów, a także wszelkich zależnych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-106">Assemblies are used for the programs themselves as well as any dependent libraries.</span></span> <span data-ttu-id="4e6b7-107">.NET program mogą być wykonywane co więcej zestawów, z nie innych wymaganych artefaktów, po wykonaniu odpowiednich .NET.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-107">A .NET program can be executed as one of more assemblies, with no other required artifacts, beyond the appropriate .NET implementation.</span></span> <span data-ttu-id="4e6b7-108">Natywnego zależności, w tym system operacyjny interfejsów API, są oddzielne problemu i nie są zawarte w formacie zestawu .NET, mimo że czasami są opisane w tym formacie (na przykład WinRT).</span><span class="sxs-lookup"><span data-stu-id="4e6b7-108">Native dependencies, including operating system APIs, are a separate concern and are not contained within the .NET assembly format, although are sometimes described with this format (for example, WinRT).</span></span>

> <span data-ttu-id="4e6b7-109">Każdy składnik interfejsu wiersza polecenia niesie metadanych dla deklaracji, implementacji i odwołuje się do określonego dla tego składnika.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-109">Each CLI component carries the metadata for declarations, implementations, and references specific to that component.</span></span> <span data-ttu-id="4e6b7-110">W związku z tym metadane specyficzne dla składnika jest określana jako składnik metadane, a wynikowy składnik jest nazywany można samoopisujące — z ECMA 335 I.9.1, składników i zestawów.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-110">Therefore, the component-specific metadata is referred to as component metadata, and the resulting component is said to be self-describing – from ECMA 335 I.9.1, Components and assemblies.</span></span>

<span data-ttu-id="4e6b7-111">Format w pełni jest określona i ujętą w standardzie ECMA-335.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-111">The format is fully specified and standardized as ECMA 335.</span></span> <span data-ttu-id="4e6b7-112">Użyj tego formatu, wszystkie kompilatory .NET i środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-112">All .NET compilers and runtimes use this format.</span></span> <span data-ttu-id="4e6b7-113">Obecność udokumentowanych i rzadko zaktualizowane format binarny został najważniejszych korzyści (raczej wymaganie) współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-113">The presence of a documented and infrequently updated binary format has been a major benefit (arguably a requirement) for interoperatibility.</span></span> <span data-ttu-id="4e6b7-114">Format ostatniej aktualizacji w sposób merytorycznych w 2005 (.NET 2.0), aby pomieścić ogólne i architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-114">The format was last updated in a substantive way in 2005 (.NET 2.0) to accommodate generics and processor architecture.</span></span>

<span data-ttu-id="4e6b7-115">Format jest funkcja Procesora i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-115">The format is CPU- and OS-agnostic.</span></span> <span data-ttu-id="4e6b7-116">Został on użyty jako część implementacji .NET, które odnoszą się do wielu procesorów i mikroukłady.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-116">It has been used as part of .NET implementations that target many chips and CPUs.</span></span> <span data-ttu-id="4e6b7-117">Gdy sam format ma dziedzictwa systemu Windows, jest implementable w dowolnym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-117">While the format itself has Windows heritage, it is implementable on any operating system.</span></span> <span data-ttu-id="4e6b7-118">Jego raczej najważniejszych wybór współdziałania systemu operacyjnego jest, że większość wartości są przechowywane w formacie little endian.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-118">It’s arguably most significant choice for OS interoperability is that most values are stored in little-endian format.</span></span> <span data-ttu-id="4e6b7-119">Nie ma określonego koligacji do rozmiaru wskaźnika maszyny (na przykład 32-bitowy, 64-bitowe).</span><span class="sxs-lookup"><span data-stu-id="4e6b7-119">It doesn’t have a specific affinity to machine pointer size (for example, 32-bit, 64-bit).</span></span>

<span data-ttu-id="4e6b7-120">Format zestawu .NET jest również bardzo opisowe informacje o strukturze danego programu lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-120">The .NET assembly format is also very descriptive about the structure of a given program or library.</span></span> <span data-ttu-id="4e6b7-121">Opisuje wewnętrznych składników zestawu, w szczególności: odwołania do zestawów i zdefiniowanych typów i ich wewnętrznej struktury.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-121">It describes the internal components of an assembly, specifically: assembly references and types defined and their internal structure.</span></span> <span data-ttu-id="4e6b7-122">Narzędzia i interfejsy API może odczytywać i przetwarzać te informacje do wyświetlania lub podjąć decyzje dotyczące programistyczny.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-122">Tools or APIs can read and process this information for display or to make programmatic decisions.</span></span>

## <a name="format"></a><span data-ttu-id="4e6b7-123">Format</span><span class="sxs-lookup"><span data-stu-id="4e6b7-123">Format</span></span>

<span data-ttu-id="4e6b7-124">Format binarny .NET zależy od systemu Windows [plik PE](http://en.wikipedia.org/wiki/Portable_Executable) format.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-124">The .NET binary format is based on the Windows [PE file](http://en.wikipedia.org/wiki/Portable_Executable) format.</span></span> <span data-ttu-id="4e6b7-125">W rzeczywistości bibliotek klas .NET są zgodność PEs systemu Windows i są wyświetlane na pierwszy rzut systemu Windows biblioteki dołączanej dynamicznie (dll) lub aplikacji pliki wykonywalne (exe).</span><span class="sxs-lookup"><span data-stu-id="4e6b7-125">In fact, .NET class libraries are conformant Windows PEs, and appear on first glance to be Windows dynamic link libraries (DLLs) or application executables (EXEs).</span></span> <span data-ttu-id="4e6b7-126">Jest to bardzo przydatne cecha w systemie Windows, w którym można udają natywne pliki binarne pliku wykonywalnego i wykonać niektóre taki sam sposób (na przykład ładowania systemu operacyjnego, narzędzia PE).</span><span class="sxs-lookup"><span data-stu-id="4e6b7-126">This is a very useful characteristic on Windows, where they can masquerade as native executable binaries and get some of the same treatment (for example, OS load, PE tools).</span></span>

![Nagłówki zestawu](./media/assembly-format/assembly-headers.png)

<span data-ttu-id="4e6b7-128">Nagłówki zestawu z ECMA 335 II.25.1, strukturę środowiska uruchomieniowego formatu pliku.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-128">Assembly Headers from ECMA 335 II.25.1, Structure of the runtime file format.</span></span>

## <a name="processing-the-assemblies"></a><span data-ttu-id="4e6b7-129">Przetwarzanie zestawów</span><span class="sxs-lookup"><span data-stu-id="4e6b7-129">Processing the Assemblies</span></span>

<span data-ttu-id="4e6b7-130">Istnieje możliwość zapisu do procesu zestawów narzędzia lub interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-130">It is possible to write tools or APIs to process assemblies.</span></span> <span data-ttu-id="4e6b7-131">Informacje o zestawie umożliwia podejmowanie decyzji programowych w czasie wykonywania, ponowne zapisywanie zestawów, zapewniając interfejsu API IntelliSense w edytorze i generowanie dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-131">Assembly information enables making programmatic decisions at runtime, re-writing assemblies, providing API IntelliSense in an editor and generating documentation.</span></span> <span data-ttu-id="4e6b7-132"><xref:System.Reflection?displayProperty=nameWithType>i [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) są dobrym przykładem narzędzia, które są często używane w tym celu.</span><span class="sxs-lookup"><span data-stu-id="4e6b7-132"><xref:System.Reflection?displayProperty=nameWithType> and [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) are good examples of tools that are frequently used for this purpose.</span></span>