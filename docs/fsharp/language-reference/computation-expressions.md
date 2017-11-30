---
title: "Wyrażenia obliczeń (F#)"
description: "Dowiedz się, jak utworzyć wygodny składnię pisanie obliczenia w F # można sekwencjonowania i łączyć, używając konstrukcji przepływu sterowania i powiązania."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: 15ba2e167efc1d295d81439dcf85bc7272e05265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="computation-expressions"></a><span data-ttu-id="1022c-104">Wyrażenia obliczeń</span><span class="sxs-lookup"><span data-stu-id="1022c-104">Computation Expressions</span></span>

<span data-ttu-id="1022c-105">Wyrażenia obliczeń w języku F # zapewniają wygodną składni zapisywania obliczenia, które mogą być sekwencjonowania i łączyć, używając konstrukcji przepływu sterowania i powiązania.</span><span class="sxs-lookup"><span data-stu-id="1022c-105">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="1022c-106">One może służyć do zapewnienia wygodny składnię *monady*, funkcjonalności funkcji programowania, który może służyć do zarządzania danych, sterowania i efekty uboczne w programach funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="1022c-106">They can be used to provide a convenient syntax for *monads*, a functional programming feature that can be used to manage data, control, and side effects in functional programs.</span></span>


## <a name="built-in-workflows"></a><span data-ttu-id="1022c-107">Wbudowanych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="1022c-107">Built-in Workflows</span></span>
<span data-ttu-id="1022c-108">Wyrażenia sekwencji są przykładem wyrażenie do obliczenia są asynchroniczne przepływy pracy i wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="1022c-108">Sequence expressions are an example of a computation expression, as are asynchronous workflows and query expressions.</span></span> <span data-ttu-id="1022c-109">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia zapytania](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1022c-109">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

<span data-ttu-id="1022c-110">Niektóre funkcje są wspólne dla wyrażenia sekwencji i asynchroniczne przepływy pracy i zilustrowania podstawowa składnia wyrażenia obliczenia:</span><span class="sxs-lookup"><span data-stu-id="1022c-110">Certain features are common to both sequence expressions and asynchronous workflows and illustrate the basic syntax for a computation expression:</span></span>

```fsharp
builder-name { expression }
```

<span data-ttu-id="1022c-111">Poprzednie składni Określa, że podane wyrażenie jest wyrażenie do obliczenia typu określony przez *nazwa konstruktora*.</span><span class="sxs-lookup"><span data-stu-id="1022c-111">The previous syntax specifies that the given expression is a computation expression of a type specified by *builder-name*.</span></span> <span data-ttu-id="1022c-112">Wyrażenia obliczeń może być wbudowane przepływu pracy, takich jak `seq` lub `async`, lub może być coś należy zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="1022c-112">The computation expression can be a built-in workflow, such as `seq` or `async`, or it can be something you define.</span></span> <span data-ttu-id="1022c-113">*Nazwa konstruktora* jest identyfikator wystąpienia specjalny typ znany jako *typu konstruktora*.</span><span class="sxs-lookup"><span data-stu-id="1022c-113">The *builder-name* is the identifier for an instance of a special type known as the *builder type*.</span></span> <span data-ttu-id="1022c-114">Typ konstruktora jest typu klasy, który definiuje specjalne metody rządzących sposób fragmentów wyrażenie obliczeń, są połączone, oznacza to, że kod tej kontrolki jak wykonuje wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1022c-114">The builder type is a class type that defines special methods that govern the way the fragments of the computation expression are combined, that is, code that controls how the expression executes.</span></span> <span data-ttu-id="1022c-115">Innym sposobem opisano konstruktora klasy jest powiedzieć umożliwia dostosowywanie operacji konstrukcji wiele F #, takich jak pętle i powiązania.</span><span class="sxs-lookup"><span data-stu-id="1022c-115">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

<span data-ttu-id="1022c-116">W wyrażeniach obliczeń dwa formularze są dostępne dla niektórych typowych konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="1022c-116">In computation expressions, two forms are available for some common language constructs.</span></span> <span data-ttu-id="1022c-117">Konstrukcje variant można wywołać za pomocą!</span><span class="sxs-lookup"><span data-stu-id="1022c-117">You can invoke the variant constructs by using a !</span></span> <span data-ttu-id="1022c-118">(bang) sufiks na niektórych słów kluczowych, takich jak `let!`, `do!`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1022c-118">(bang) suffix on certain keywords, such as `let!`, `do!`, and so on.</span></span> <span data-ttu-id="1022c-119">Formach specjalne spowodować, że pewne funkcje zdefiniowana w klasie konstruktora zastąpić zwykłe zachowanie wbudowane te operacje.</span><span class="sxs-lookup"><span data-stu-id="1022c-119">These special forms cause certain functions defined in the builder class to replace the ordinary built-in behavior of these operations.</span></span> <span data-ttu-id="1022c-120">Formularze przypominać `yield!` formę `yield` — słowo kluczowe, które jest używane w wyrażeniach sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1022c-120">These forms resemble the `yield!` form of the `yield` keyword that is used in sequence expressions.</span></span> <span data-ttu-id="1022c-121">Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="1022c-121">For more information, see [Sequences](sequences.md).</span></span>


## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="1022c-122">Tworzenie nowego typu — wyrażenie obliczeń</span><span class="sxs-lookup"><span data-stu-id="1022c-122">Creating a New Type of Computation Expression</span></span>
<span data-ttu-id="1022c-123">Można zdefiniować właściwości wyrażenia obliczenia tworzenie konstruktora klasy, a niektóre specjalne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="1022c-123">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="1022c-124">Konstruktor klasy można opcjonalnie zdefiniować metody wymienionych w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1022c-124">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="1022c-125">W poniższej tabeli opisano metody, których można użyć w klasie konstruktora przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1022c-125">The following table describes methods that can be used in a workflow builder class.</span></span>


|<span data-ttu-id="1022c-126">**— Metoda**</span><span class="sxs-lookup"><span data-stu-id="1022c-126">**Method**</span></span>|<span data-ttu-id="1022c-127">**Typowy podpisy**</span><span class="sxs-lookup"><span data-stu-id="1022c-127">**Typical signature(s)**</span></span>|<span data-ttu-id="1022c-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1022c-128">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="1022c-129">Wywołuje się dla `let!` i `do!` w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-129">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="1022c-130">Opakowuje wyrażenie do obliczenia w funkcji.</span><span class="sxs-lookup"><span data-stu-id="1022c-130">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="1022c-131">Wywołuje się dla `return` w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-131">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1022c-132">Wywołuje się dla `return!` w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-132">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="1022c-133">`M<'T> -> M<'T>`lub</span><span class="sxs-lookup"><span data-stu-id="1022c-133">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="1022c-134">Wykonuje wyrażenie do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-134">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="1022c-135">`M<'T> * M<'T> -> M<'T>`lub</span><span class="sxs-lookup"><span data-stu-id="1022c-135">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="1022c-136">Wywołuje się do sekwencjonowania w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-136">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="1022c-137">`seq<'T> * ('T -> M<'U>) -> M<'U>`lub</span><span class="sxs-lookup"><span data-stu-id="1022c-137">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="1022c-138">Wywołuje się dla `for...do` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-138">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="1022c-139">Wywołuje się dla `try...finally` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-139">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="1022c-140">Wywołuje się dla `try...with` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-140">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="1022c-141">Wywołuje się dla `use` powiązania w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-141">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="1022c-142">Wywołuje się dla `while...do` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-142">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="1022c-143">Wywołuje się dla `yield` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-143">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="1022c-144">Wywołuje się dla `yield!` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-144">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="1022c-145">Wywoływana dla pustego `else` gałęzi elementu `if...then` wyrażenia w wyrażeniach obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-145">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
<span data-ttu-id="1022c-146">Wiele metod w klasie konstruktora użycia i zwracać `M<'T>` konstrukcji, która jest zazwyczaj oddzielnie zdefiniowanego typu, która charakteryzuje typu obliczenia łączonych, na przykład, `Async<'T>` dla Asynchroniczne przepływy pracy i `Seq<'T>` dla przepływów pracy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1022c-146">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="1022c-147">Podpisy tych metod umożliwiały można łączyć i zagnieżdżone ze sobą, tak, aby przepływ pracy obiektu zwróconego z jednego konstrukcji mogą zostać przekazane do następnego.</span><span class="sxs-lookup"><span data-stu-id="1022c-147">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="1022c-148">Kompilator po przeanalizowaniu wyrażenie do obliczenia konwertuje wyrażenie na serię zagnieżdżonych wywołań funkcji przy użyciu metod w powyższej tabeli i kodu w wyrażeniu obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-148">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="1022c-149">Zagnieżdżone wyrażenia ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="1022c-149">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="1022c-150">W kodzie powyżej wywołań `Run` i `Delay` są pomijane, jeśli nie są zdefiniowane w klasie Konstruktor wyrażeń obliczeń.</span><span class="sxs-lookup"><span data-stu-id="1022c-150">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="1022c-151">Treść wyrażenia obliczeń, w tym miejscu jest oznaczona jako `{| cexpr |}`, przetłumaczyć wywołania metody konstruktora klasy obejmujące przez tłumaczeń opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1022c-151">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="1022c-152">Wyrażenia obliczeń `{| cexpr |}` jest zdefiniowane cyklicznie zgodnie z tymi tłumaczeń gdzie `expr` wyrażenie F # i `cexpr` jest wyrażenie do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-152">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="1022c-153">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="1022c-153">Expression</span></span>|<span data-ttu-id="1022c-154">Translacja</span><span class="sxs-lookup"><span data-stu-id="1022c-154">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}<code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}<code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="1022c-155">W poprzedniej tabeli `other-expr` opisuje wyrażenie, które w przeciwnym razie nie jest wyszczególniony w tabeli.</span><span class="sxs-lookup"><span data-stu-id="1022c-155">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="1022c-156">Konstruktor klasy nie trzeba zaimplementować wszystkie metody i obsługują wszystkie tłumaczeń wymienione w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1022c-156">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="1022c-157">Tych konstrukcji, które nie są zaimplementowane nie są dostępne w wyrażeniach obliczeń tego typu.</span><span class="sxs-lookup"><span data-stu-id="1022c-157">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="1022c-158">Na przykład, jeśli nie chcesz obsługiwać `use` — słowo kluczowe w Twojej wyrażenia obliczeń, można pominąć definicji `Use` w klasie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1022c-158">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="1022c-159">Poniższy przykład kodu pokazuje — wyrażenie obliczeń hermetyzujący obliczenia serie kroków, które mogą być obliczane krok naraz.</span><span class="sxs-lookup"><span data-stu-id="1022c-159">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="1022c-160">Typ Unii Suma rozłączna — A `OkOrException`, koduje stanu błędu wyrażenia obliczonego w do tej pory.</span><span class="sxs-lookup"><span data-stu-id="1022c-160">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="1022c-161">Ten kod przedstawiono kilka typowych wzorców, które można używać w sieci wyrażenia obliczeń, takich jak implementacje umożliwiającego niektóre metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1022c-161">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="1022c-162">Wyrażenie do obliczenia ma odpowiedni typ, który zwraca wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-162">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="1022c-163">Typ źródłowy może reprezentować obliczona wynik lub opóźnione obliczeń, który może być wykonana lub może zapewnić sposób iterację pewien typ kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1022c-163">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="1022c-164">W poprzednim przykładzie, typ podstawowy został **ostatecznie**.</span><span class="sxs-lookup"><span data-stu-id="1022c-164">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="1022c-165">Wyrażenia sekwencji jest typem podstawowym <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1022c-165">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1022c-166">Wyrażenia zapytania jest typem podstawowym <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1022c-166">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1022c-167">Asychronous przepływu pracy, jest typem podstawowym [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="1022c-167">For an asychronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="1022c-168">`Async` Obiekt reprezentuje pracy do wykonania można obliczyć wyniku.</span><span class="sxs-lookup"><span data-stu-id="1022c-168">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="1022c-169">Na przykład wywołać [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) wykonać obliczenia i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="1022c-169">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="1022c-170">Operacje niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1022c-170">Custom Operations</span></span>
<span data-ttu-id="1022c-171">Można zdefiniować niestandardowe operacja na wyrażeniu obliczenia i Użyj niestandardowej operacji jako operator w wyrażeniu obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-171">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="1022c-172">Na przykład operator zapytania można uwzględnić w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="1022c-172">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="1022c-173">Podczas definiowania niestandardowych operacji, należy zdefiniować wydajność i metod w wyrażeniu obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-173">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="1022c-174">Aby zdefiniować operacja niestandardowa, umieść ją w klasie konstruktora dla wyrażenia obliczeń, a następnie Zastosuj [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="1022c-174">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="1022c-175">Ten atrybut ma ciąg jako argument, czyli nazwa do użycia w ramach operacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1022c-175">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="1022c-176">Ta nazwa wchodzi w zakres na początku otwierający nawias klamrowy wyrażenia obliczenia.</span><span class="sxs-lookup"><span data-stu-id="1022c-176">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="1022c-177">W związku z tym nie można używać identyfikatorów, które mają taką samą nazwę jak operacja niestandardowa w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="1022c-177">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="1022c-178">Na przykład, takich jak należy unikać użycia identyfikatorów `all` lub `last` w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="1022c-178">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

## <a name="see-also"></a><span data-ttu-id="1022c-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1022c-179">See Also</span></span>
[<span data-ttu-id="1022c-180">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="1022c-180">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1022c-181">Asynchroniczne przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="1022c-181">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="1022c-182">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="1022c-182">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="1022c-183">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="1022c-183">Query Expressions</span></span>](query-expressions.md)