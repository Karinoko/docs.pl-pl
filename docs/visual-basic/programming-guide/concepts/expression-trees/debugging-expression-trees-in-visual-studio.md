---
title: "Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff1bee9c3c3fdeafab24368d2c7e8376d4ff7b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="ad938-102">Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad938-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="ad938-103">Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad938-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="ad938-104">Aby uzyskać szybki przegląd struktury drzewa wyrażenia, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="ad938-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="ad938-105">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ad938-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="ad938-106">Aby lepiej reprezentuje zawartość drzewa wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad938-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="ad938-107">Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="ad938-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="ad938-108">Aby otworzyć wizualizatora drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ad938-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="ad938-109">Kliknij ikonę lupy, który jest wyświetlany obok pozycji `DebugView` właściwości drzewo wyrażeń w **etykietek danych**, **czujki** okna, **automatycznych** okna, lub **Zmiennych lokalnych** okna.</span><span class="sxs-lookup"><span data-stu-id="ad938-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="ad938-110">Zostanie wyświetlona lista wizualizatorów.</span><span class="sxs-lookup"><span data-stu-id="ad938-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="ad938-111">Kliknij pozycję Wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="ad938-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="ad938-112">Każdy typ wyrażenia jest wyświetlany w wizualizatora, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="ad938-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="ad938-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="ad938-113">ParameterExpressions</span></span>  
 <span data-ttu-id="ad938-114"><xref:System.Linq.Expressions.ParameterExpression>nazwy zmiennych są wyświetlane przy użyciu symbolu "$" na początku.</span><span class="sxs-lookup"><span data-stu-id="ad938-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="ad938-115">Jeśli parametr nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="ad938-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="ad938-117">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="ad938-118">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="ad938-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="ad938-119">ConstantExpressions</span></span>  
 <span data-ttu-id="ad938-120">Dla <xref:System.Linq.Expressions.ConstantExpression> obiektów, które reprezentują wartości całkowite, ciągi, i `null`, jest wyświetlana wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="ad938-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-121">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="ad938-122">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="ad938-123">10</span><span class="sxs-lookup"><span data-stu-id="ad938-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="ad938-124">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="ad938-125">10D</span><span class="sxs-lookup"><span data-stu-id="ad938-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="ad938-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="ad938-126">BlockExpression</span></span>  
 <span data-ttu-id="ad938-127">Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiektu różni się od typu ostatniego wyrażenia w bloku, jest wyświetlany w `DebugInfo` właściwości w nawiasy (\< i >).</span><span class="sxs-lookup"><span data-stu-id="ad938-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="ad938-128">W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiekt nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="ad938-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-129">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="ad938-130">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="ad938-131">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="ad938-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="ad938-132">LambdaExpression</span></span>  
 <span data-ttu-id="ad938-133"><xref:System.Linq.Expressions.LambdaExpression>obiekty są wyświetlane wraz z ich typy delegowane.</span><span class="sxs-lookup"><span data-stu-id="ad938-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="ad938-134">Jeśli wyrażenie lambda nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Lambda1` lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="ad938-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-135">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="ad938-136">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="ad938-137">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="ad938-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="ad938-138">LabelExpression</span></span>  
 <span data-ttu-id="ad938-139">Jeśli określono wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest wyświetlana przed <xref:System.Linq.Expressions.LabelTarget> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad938-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="ad938-140">`.Label` Token wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="ad938-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="ad938-141">`.LabelTarget` Docelowego obiektu docelowego, aby przejść do wskazuje token.</span><span class="sxs-lookup"><span data-stu-id="ad938-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="ad938-142">Jeśli etykieta nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="ad938-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="ad938-144">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="ad938-145">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="ad938-146">Operatory zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="ad938-146">Checked Operators</span></span>  
 <span data-ttu-id="ad938-147">Operatory zaznaczone są wyświetlane ze znakiem "#" przed operatora.</span><span class="sxs-lookup"><span data-stu-id="ad938-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="ad938-148">Na przykład operator dodawania zaznaczenia jest wyświetlany jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="ad938-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ad938-149">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ad938-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="ad938-150">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="ad938-151">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="ad938-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="ad938-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad938-152">See Also</span></span>  
 [<span data-ttu-id="ad938-153">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad938-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="ad938-154">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ad938-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="ad938-155">Utwórz niestandardowe Wizualizatory</span><span class="sxs-lookup"><span data-stu-id="ad938-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)