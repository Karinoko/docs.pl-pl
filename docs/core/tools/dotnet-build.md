---
title: polecenie kompilacji DotNet
description: Dotnet kompilacji polecenia kompilacji w projekt i wszystkie jego zależności.
ms.date: 12/04/2018
ms.openlocfilehash: 1e5e05d51f98394b2b77e3a8fc645cf9712b0a0f
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169713"
---
# <a name="dotnet-build"></a>Kompilacja DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet build` -Kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet build` Polecenie kompiluje projekt i jego zależności do zestawu plików binarnych. Pliki binarne obejmują kodu projektu w plikach języka pośredniego (IL) z *.dll* plików symboli i rozszerzenia, które są używane do debugowania za pomocą *.pdb* rozszerzenia. Plik JSON zależności (*\*. deps.json*) jest generowany, znajduje się wykaz zależności aplikacji. A  *\*. runtimeconfig.json* generowany jest plik, który określa udostępnionego środowiska uruchomieniowego i jego wersję aplikacji.

Jeśli projekt zawiera zależności innych firm, takich jak biblioteki z pakietów NuGet, jest rozwiązany z pamięcią podręczną programu NuGet i nie są dostępne w skompilowanych danych wyjściowych projektu. Mając to na uwadze, wynikiem `dotnet build` nie jest gotowa do przeniesienia do innego komputera do uruchomienia. Jest to w przeciwieństwie do zachowania programu .NET Framework w budynku, które projekt wykonywalny (aplikacji) generuje dane wyjściowe, który jest możliwy do uruchomienia na dowolnym komputerze, gdzie .NET Framework jest zainstalowana. Aby podobnie środowisko z platformą .NET Core, musisz użyć [publikowania dotnet](dotnet-publish.md) polecenia. Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).

Kompilowanie wymaga *project.assets.json* pliku, który znajduje się wykaz zależności aplikacji. Plik jest tworzony, gdy [ `dotnet restore` ](dotnet-restore.md) jest wykonywany. Bez pliku zasobów w miejscu narzędzi nie można rozpoznać zestawy odwołań, co powoduje błędy. Za pomocą programu .NET Core 1.x SDK wymagane do uruchamiania jawnie `dotnet restore` przed uruchomieniem `dotnet build`. Począwszy od programu .NET Core 2.0 SDK, `dotnet restore` uruchamia się domyślnie po uruchomieniu `dotnet build`. Jeśli chcesz wyłączyć niejawne przywracania, podczas uruchamiania polecenia kompilacji, można przekazać `--no-restore` opcji.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Projekt jest wykonywalny lub nie jest określana przez `<OutputType>` właściwość w pliku projektu. Poniższy przykład przedstawia projekt, który generuje kod wykonywalny:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby wygenerować bibliotekę, Pomiń `<OutputType>` właściwości. Główną różnicą w skompilowanych danych wyjściowych jest, że biblioteki DLL IL nie zawiera punkty wejścia i nie można wykonać.

### <a name="msbuild"></a>MSBuild

`dotnet build` używa programu MSBuild do kompilowania projektu, więc obsługują równoległych oraz przyrostowe kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).

Oprócz jej opcji `dotnet build` polecenie akceptuje opcje programu MSBuild `-p` do ustawiania właściwości lub `-l` do definiowania rejestrator. Aby uzyskać więcej informacji o tych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Lub możesz również użyć [dotnet msbuild](dotnet-msbuild.md) polecenia.

Uruchamianie `dotnet build` jest odpowiednikiem `dotnet msbuild -restore -target:Build`.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do kompilacji. Jeśli nie określono pliku projektu lub rozwiązania, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się w jednym *proj* lub *sln* i używa tego pliku.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonego [framework](../../standard/frameworks.md). Struktura musi być zdefiniowany w [pliku projektu](csproj.md).

* **`--force`**

  Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--no-dependencies`**

  Ignoruje odwołania do projektu do projektu (P2P) i tylko kompilacje określonym katalogu głównym projektu.

* **`--no-incremental`**

  Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej. Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymusza czyste odbudowania tego wykresu zależności projektu.

* **`--no-restore`**

  Nie jest wykonywana niejawna przywracania, podczas kompilacji.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w której chcesz umieścić skompilowane pliki binarne. Musisz również zdefiniować `--framework` po określeniu tej opcji. Jeśli nie zostanie określony, domyślna ścieżka to `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowe środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Określa sufiks wersji znak gwiazdki (`*`) w polu wersja pliku projektu. Format jest zgodny wskazówki wersji NuGet.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonego [framework](../../standard/frameworks.md). Struktura musi być zdefiniowany w [pliku projektu](csproj.md).

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`--no-dependencies`**

  Ignoruje odwołania do projektu do projektu (P2P) i tylko kompilacje określonym katalogu głównym projektu.

* **`--no-incremental`**

  Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej. Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymusza czyste odbudowania tego wykresu zależności projektu.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w której chcesz umieścić skompilowane pliki binarne. Musisz również zdefiniować `--framework` po określeniu tej opcji.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowe środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Określa sufiks wersji znak gwiazdki (`*`) w polu wersja pliku projektu. Format jest zgodny wskazówki wersji NuGet.

---

## <a name="examples"></a>Przykłady

* Tworzenie projektu i jego zależności:

  ```console
  dotnet build
  ```

* Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

  ```console
  dotnet build --configuration Release
  ```

* Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 16.04):

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* Skompiluj projekt, a następnie użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Skompilować projekt i ustawić 1.2.3.4 wersji jako parametr kompilacji:

  ```console
  dotnet build -p:Version=1.2.3.4
  ```