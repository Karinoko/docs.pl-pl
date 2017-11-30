---
title: Przestrzenie nazw (F#)
description: "Dowiedz się, jak przestrzeń nazw F # umożliwia organizowanie kodu w obszarach związanych z nimi funkcji umożliwiając dołączyć nazwę do grupowania elementów programu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: 4378afebe6fd0d9317f734457576dc75d7488bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces"></a><span data-ttu-id="e86bb-104">Namespaces</span><span class="sxs-lookup"><span data-stu-id="e86bb-104">Namespaces</span></span>

<span data-ttu-id="e86bb-105">Przestrzeń nazw umożliwia organizowanie kodu w obszarach związanych z nimi funkcji umożliwiając dołączyć nazwę do grupowania elementów programu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="e86bb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e86bb-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="e86bb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e86bb-107">Remarks</span></span>
<span data-ttu-id="e86bb-108">Jeśli chcesz umieścić kodu w przestrzeni nazw, pierwszej deklaracji w pliku musi zadeklarować przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="e86bb-109">Zawartość cały plik stanie się część obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="e86bb-110">Przestrzenie nazw nie może bezpośrednio zawierać wartości i funkcje.</span><span class="sxs-lookup"><span data-stu-id="e86bb-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="e86bb-111">Zamiast tego funkcje i wartości muszą być uwzględnione w modułach i moduły znajdują się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="e86bb-112">Przestrzenie nazw może zawierać typów modułów.</span><span class="sxs-lookup"><span data-stu-id="e86bb-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="e86bb-113">Przestrzenie nazw mogą być deklarowane jawnie ze słowem kluczowym przestrzeni nazw lub niejawnie przy deklarowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="e86bb-114">Aby jawnie zadeklarować przestrzeni nazw, użyj słowa kluczowego przestrzeni nazw i nazwa przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="e86bb-115">Poniższy przykład przedstawia plik kodu, który deklaruje elementy widget typu i moduł zawarte w tej przestrzeni nazw z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="e86bb-116">Jeśli jeden moduł całą zawartość pliku, można również zadeklarować przestrzeni nazw niejawnie za pomocą `module` — słowo kluczowe i podanie nowej nazwy przestrzeni nazw w nazwie FQDN modułu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="e86bb-117">W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeni nazw `Widgets` i moduł `WidgetsModule`, który zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="e86bb-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="e86bb-118">Następujący kod jest odpowiednikiem poprzedniego kodu, ale modułem jest deklaracja modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e86bb-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="e86bb-119">W takim przypadku przestrzeni nazw musi znajdować się w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="e86bb-120">Jeśli wymagane jest więcej niż jeden moduł, w tym samym pliku, w jedną lub kilka przestrzeni nazw, należy użyć deklaracji modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e86bb-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="e86bb-121">Użycie deklaracji lokalnej modułu, nie można użyć kwalifikowaną przestrzeni nazw w deklaracjach modułów.</span><span class="sxs-lookup"><span data-stu-id="e86bb-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="e86bb-122">Poniższy kod przedstawia plik, który ma deklaracja przestrzeni nazw i dwa deklaracjach modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e86bb-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="e86bb-123">W takim przypadku moduły znajdują się bezpośrednio w przestrzeni nazw; Brak nie niejawnie tworzonych moduł, który ma taką samą nazwę jak plik.</span><span class="sxs-lookup"><span data-stu-id="e86bb-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="e86bb-124">Każdy inny kod w pliku, takich jak `do` powiązanie, jest w przestrzeni nazw, ale nie w wewnętrzne moduły, dlatego należy do elementu członkowskiego moduł kwalifikowania `widgetFunction` przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="e86bb-125">Dane wyjściowe w tym przykładzie ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="e86bb-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="e86bb-126">Aby uzyskać więcej informacji, zobacz [modułów](modules.md).</span><span class="sxs-lookup"><span data-stu-id="e86bb-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="e86bb-127">Zagnieżdżone przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="e86bb-127">Nested Namespaces</span></span>
<span data-ttu-id="e86bb-128">Podczas tworzenia zagnieżdżonych przestrzeni nazw, należy je pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="e86bb-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="e86bb-129">W przeciwnym razie można utworzyć nowej przestrzeni nazw najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="e86bb-130">Wcięcie jest ignorowany w deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="e86bb-131">Poniższy przykład pokazuje, jak można zadeklarować zagnieżdżonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="e86bb-132">Przestrzenie nazw w plikach i zestawy</span><span class="sxs-lookup"><span data-stu-id="e86bb-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="e86bb-133">Przestrzenie nazw może obejmować wiele plików z jednego projektu lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e86bb-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="e86bb-134">Termin *fragmentu przestrzeni nazw* opisuje część przestrzeni nazw, która znajduje się w jednym pliku.</span><span class="sxs-lookup"><span data-stu-id="e86bb-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="e86bb-135">Przestrzenie nazw może obejmować wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="e86bb-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="e86bb-136">Na przykład `System` przestrzeń nazw obejmuje całą .NET Framework, która obejmuje wiele zestawów i zawiera wiele zagnieżdżonych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="e86bb-137">Namespace globalne</span><span class="sxs-lookup"><span data-stu-id="e86bb-137">Global Namespace</span></span>
<span data-ttu-id="e86bb-138">Użyj wstępnie zdefiniowanych nazw `global` umieścić nazwy w przestrzeni nazw .NET najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="e86bb-139">Umożliwia także globalny ma dotyczyć odwołanie obszaru nazw .NET najwyższego poziomu, na przykład, aby rozwiązać konflikty nazw z innych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

##

<span data-ttu-id="e86bb-140">F # 4.1 wprowadzono pojęcie przestrzeni nazw, który umożliwia się wzajemnie rekursywne wszystkich zawartych w niej kodu.</span><span class="sxs-lookup"><span data-stu-id="e86bb-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="e86bb-141">Odbywa się za pośrednictwem `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="e86bb-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="e86bb-142">Użycie `namespace rec` można zlikwidować niektóre problemy, które nie jest możliwość napisać kod wzajemnie referencyjnej między typami i modułów.</span><span class="sxs-lookup"><span data-stu-id="e86bb-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="e86bb-143">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="e86bb-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="e86bb-144">Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie.</span><span class="sxs-lookup"><span data-stu-id="e86bb-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="e86bb-145">Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.</span><span class="sxs-lookup"><span data-stu-id="e86bb-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="e86bb-146">To nie jest możliwe do wyrażenia w języku F #, jeśli usunięto `rec` — słowo kluczowe z `MutualReferences` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e86bb-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="e86bb-147">Ta funkcja jest również dostępny do najwyższego poziomu [modułów](modules.md) w F # 4.1 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="e86bb-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="e86bb-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e86bb-148">See Also</span></span>
[<span data-ttu-id="e86bb-149">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="e86bb-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e86bb-150">Moduły</span><span class="sxs-lookup"><span data-stu-id="e86bb-150">Modules</span></span>](modules.md)

[<span data-ttu-id="e86bb-151">1009-F # RFC FS - Zezwalaj modułów i typy referencyjne wzajemnie przez szerszego zakresu w plikach</span><span class="sxs-lookup"><span data-stu-id="e86bb-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)