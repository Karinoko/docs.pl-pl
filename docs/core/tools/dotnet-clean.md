---
title: polecenie - .NET Core interfejsu wiersza polecenia czyszczenia DotNet
description: "Polecenie Wyczyść dotnet czyści bieżącego katalogu."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4836f07ec1a8b59c343b4d0181587e602f61d45e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-clean"></a><span data-ttu-id="7158e-103">Wyczyść DotNet</span><span class="sxs-lookup"><span data-stu-id="7158e-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7158e-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7158e-104">Name</span></span>

<span data-ttu-id="7158e-105">`dotnet clean`-Czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="7158e-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7158e-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="7158e-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7158e-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="7158e-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7158e-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7158e-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7158e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7158e-109">Description</span></span>

<span data-ttu-id="7158e-110">`dotnet clean` Polecenie czyści dane wyjściowe ostatniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="7158e-111">Jest zaimplementowany jako [docelowy programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniane w czasie uruchomienia polecenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="7158e-112">Tylko dane wyjściowe tworzone podczas kompilacji zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="7158e-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="7158e-113">Zarówno pośredni (*obj*) i pliku wyjściowego (*bin*) foldery zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="7158e-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="7158e-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7158e-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7158e-115">Aby wyczyścić projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7158e-115">The MSBuild project to clean.</span></span> <span data-ttu-id="7158e-116">Jeśli nie określono pliku projektu, MSBuild wyszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="7158e-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="7158e-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="7158e-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7158e-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="7158e-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7158e-119">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-119">Defines the build configuration.</span></span> <span data-ttu-id="7158e-120">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7158e-120">The default value is `Debug`.</span></span> <span data-ttu-id="7158e-121">Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7158e-122">[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="7158e-123">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="7158e-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="7158e-124">Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="7158e-125">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7158e-126">Katalog, w którym są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="7158e-127">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="7158e-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7158e-128">Czyści folderze wyjściowym określonym środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7158e-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="7158e-129">Ten element jest używany podczas [niezależne wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.</span><span class="sxs-lookup"><span data-stu-id="7158e-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7158e-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7158e-131">Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="7158e-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7158e-132">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="7158e-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7158e-133">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-133">Defines the build configuration.</span></span> <span data-ttu-id="7158e-134">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7158e-134">The default value is `Debug`.</span></span> <span data-ttu-id="7158e-135">Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7158e-136">[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="7158e-137">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="7158e-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="7158e-138">Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="7158e-139">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7158e-140">Katalog, w którym są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7158e-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="7158e-141">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="7158e-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7158e-142">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7158e-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7158e-143">Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="7158e-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="7158e-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7158e-144">Examples</span></span>

<span data-ttu-id="7158e-145">Czyszczenie kompilacji domyślnego projektu:</span><span class="sxs-lookup"><span data-stu-id="7158e-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="7158e-146">Wyczyść projekt utworzony przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="7158e-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`