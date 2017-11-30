---
title: "let — Powiązania (F#)"
description: "Dowiedz się, jak używać F # \"let\" powiązanie, co umożliwia skojarzenie identyfikatora z wartości lub funkcji."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a><span data-ttu-id="d87c2-104">let — Powiązania</span><span class="sxs-lookup"><span data-stu-id="d87c2-104">let Bindings</span></span>

<span data-ttu-id="d87c2-105">A *powiązania* kojarzy identyfikator z wartości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="d87c2-105">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="d87c2-106">Możesz użyć `let` — słowo kluczowe, aby powiązać nazwę wartości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="d87c2-106">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d87c2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d87c2-107">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="d87c2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d87c2-108">Remarks</span></span>

<span data-ttu-id="d87c2-109">`let` Słowo kluczowe jest używane w wyrażenia, aby zdefiniować wartości lub wartości funkcji dla jednego lub więcej nazw powiązania.</span><span class="sxs-lookup"><span data-stu-id="d87c2-109">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="d87c2-110">Najprostsza forma `let` wyrażenie wiąże nazwę prostą wartością w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d87c2-110">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="d87c2-111">Jeśli wyrażenie z identyfikatorem oddzielić przy użyciu nowego wiersza, musi wcięcie każdego wiersza wyrażenia, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="d87c2-111">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="d87c2-112">Zamiast tylko nazwę wzorca, który zawiera nazwy można określić, na przykład spójnej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d87c2-112">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="d87c2-113">*Treść wyrażenia* jest wyrażeniem, w którym są używane nazwy.</span><span class="sxs-lookup"><span data-stu-id="d87c2-113">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="d87c2-114">Wyrażenie treści pojawia się w oddzielnej linii, wcięcia wiersza się dokładnie z pierwszego znaku w `let` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="d87c2-114">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="d87c2-115">A `let` powiązania mogą być wyświetlane na poziomie modułu w definicji typu klasy lub w zakresach lokalnego, taki jak definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="d87c2-115">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="d87c2-116">A `let` powiązania na najwyższym poziomie w module lub w typie klasy musi mieć wyrażenie treści, ale na innych poziomach zakresu, wymagane jest wyrażenie treści.</span><span class="sxs-lookup"><span data-stu-id="d87c2-116">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="d87c2-117">Nazwy powiązane są użyteczne po punkcie definicji, ale nie w dowolnym momencie przed `let` powiązania pojawia się, jak przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d87c2-117">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a><span data-ttu-id="d87c2-118">Powiązania funkcji</span><span class="sxs-lookup"><span data-stu-id="d87c2-118">Function Bindings</span></span>

<span data-ttu-id="d87c2-119">Powiązania funkcji zgodne z regułami dotyczącymi powiązania wartości, z wyjątkiem tego powiązania funkcji obejmują nazwy funkcji i parametrów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d87c2-119">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="d87c2-120">Ogólnie rzecz biorąc parametry są wzorców, takich jak wzorzec spójnej kolekcji:</span><span class="sxs-lookup"><span data-stu-id="d87c2-120">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="d87c2-121">A `let` powiązanie wyrażenie daje w wyniku wartość ostatniego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d87c2-121">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="d87c2-122">W związku z tym w poniższym przykładzie kodu wartość `result` jest obliczana na podstawie `100 * function3 (1, 2)`, która daje w wyniku `300`.</span><span class="sxs-lookup"><span data-stu-id="d87c2-122">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="d87c2-123">Aby uzyskać więcej informacji, zobacz [funkcji](index.md).</span><span class="sxs-lookup"><span data-stu-id="d87c2-123">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="d87c2-124">Adnotacje typu</span><span class="sxs-lookup"><span data-stu-id="d87c2-124">Type Annotations</span></span>

<span data-ttu-id="d87c2-125">Można określić typy parametrów, umieszczając dwukropka (:), a następnie nazwę typu, wszystkie ujęty w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="d87c2-125">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="d87c2-126">Można również określić typ wartości zwracanej przez dołączenie dwukropek i typ po ostatnim parametrem.</span><span class="sxs-lookup"><span data-stu-id="d87c2-126">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="d87c2-127">Adnotacje pełny typ dla `function1`, z liczb całkowitych jako typy parametrów, zostaną wyświetlone następujące.</span><span class="sxs-lookup"><span data-stu-id="d87c2-127">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="d87c2-128">Jeśli nie ma żadnych jawnych parametrów typu, wnioskowanie o typie służy do określania typami parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d87c2-128">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="d87c2-129">Może to obejmować automatyczne uogólnianie typ parametru, aby wartość była ogólna.</span><span class="sxs-lookup"><span data-stu-id="d87c2-129">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="d87c2-130">Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md) i [wnioskowanie o typie](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="d87c2-130">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="d87c2-131">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="d87c2-131">let Bindings in Classes</span></span>

<span data-ttu-id="d87c2-132">A `let` powiązania może występować w typie klasy, ale nie w strukturze lub typ rekordu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-132">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="d87c2-133">Aby użyć let powiązania w typie klasy, klasy musi mieć konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d87c2-133">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="d87c2-134">Parametry Konstruktora musi występować po nazwie typu w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="d87c2-134">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="d87c2-135">A `let` powiązania w typie klasy definiuje pól prywatnych i członków dla tego typu klasy, wraz z `do` powiązania w typie, formularzy kod podstawowego konstruktora dla typu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-135">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="d87c2-136">W poniższych przykładach kodu pokazano klasy `MyClass` z pól prywatnych `field1` i `field2`.</span><span class="sxs-lookup"><span data-stu-id="d87c2-136">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="d87c2-137">Zakresy z `field1` i `field2` są ograniczone do typu, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="d87c2-137">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="d87c2-138">Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasy](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="d87c2-138">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="d87c2-139">Parametrów typu w let — powiązania</span><span class="sxs-lookup"><span data-stu-id="d87c2-139">Type Parameters in let Bindings</span></span>

<span data-ttu-id="d87c2-140">A `let` powiązanie na poziomie modułu, typu lub wyrażenie do obliczenia mogą zawierać jawnych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-140">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="d87c2-141">Let powiązania w wyrażeniu, takich jak w definicji funkcji, nie może mieć parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-141">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="d87c2-142">Aby uzyskać więcej informacji, zobacz [ogólne](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d87c2-142">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="d87c2-143">Atrybuty let — powiązania</span><span class="sxs-lookup"><span data-stu-id="d87c2-143">Attributes on let Bindings</span></span>

<span data-ttu-id="d87c2-144">Atrybuty można zastosować do najwyższego poziomu `let` powiązania w module, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d87c2-144">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="d87c2-145">Zakres i dostępności powiązania Let</span><span class="sxs-lookup"><span data-stu-id="d87c2-145">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="d87c2-146">Zakres jednostka zadeklarowana z powiązaniem let jest ograniczony do części zawierający zakres (na przykład funkcji, modułu, plik lub klasy) po wyświetleniu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d87c2-146">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="d87c2-147">W związku z tym można powiedzieć, że powiązanie let wprowadza nazwę do zakresu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-147">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="d87c2-148">W module wartość let wiązaniem lub funkcja jest dostępna dla klientów modułu tak długo, jak moduł jest niedostępny, ponieważ powiązania let w module są skompilowane w publicznych funkcji modułu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-148">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="d87c2-149">Z kolei powiązania let w klasach są prywatne do klasy.</span><span class="sxs-lookup"><span data-stu-id="d87c2-149">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="d87c2-150">Zwykle funkcje w modułach musi być kwalifikowana przez nazwę modułu, gdy jest używany przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="d87c2-150">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="d87c2-151">Na przykład, jeśli moduł `Module1` ma funkcję `function1`, użytkownicy będą określać `Module1.function1` do odwoływania się do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d87c2-151">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="d87c2-152">Użytkownicy modułu może używać deklaracja importu, aby udostępnić funkcje w ramach tego modułu do użytku nie jest kwalifikowana przez nazwę modułu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-152">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="d87c2-153">W przykładzie wymienionym powyżej użytkowników modułu można otworzyć w takim przypadku moduł za pomocą polecenia Otwórz deklaracji importu `Module1` , a następnie odwoływać się do `function1` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d87c2-153">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="d87c2-154">Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które udostępniają musi być kwalifikowana nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-154">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="d87c2-155">Na przykład moduł F # listy ma tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d87c2-155">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="d87c2-156">Aby uzyskać więcej informacji dotyczących modułów i kontroli dostępu, zobacz [modułów](../modules.md) i [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="d87c2-156">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d87c2-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d87c2-157">See Also</span></span>

[<span data-ttu-id="d87c2-158">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d87c2-158">Functions</span></span>](index.md)

[<span data-ttu-id="d87c2-159">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="d87c2-159">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)