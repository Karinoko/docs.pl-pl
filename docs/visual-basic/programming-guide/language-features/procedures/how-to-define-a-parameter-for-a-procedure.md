---
title: 'Porady: definiowanie parametru dla procedury (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="939bb-102">Porady: definiowanie parametru dla procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="939bb-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="939bb-103">A *parametru* umożliwia kod wywołujący przekazać wartości do procedury, gdy wywołuje ona.</span><span class="sxs-lookup"><span data-stu-id="939bb-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="939bb-104">Każdy parametr dla procedury zadeklarować zadeklarować zmiennej, określając jej nazwę i typ danych tak samo.</span><span class="sxs-lookup"><span data-stu-id="939bb-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="939bb-105">Można także określić mechanizm przekazywania i określa, czy parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="939bb-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="939bb-106">Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="939bb-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="939bb-107">Aby zdefiniować parametr procedury</span><span class="sxs-lookup"><span data-stu-id="939bb-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="939bb-108">W deklaracji procedury Dodaj nazwę parametru do listy parametrów procedury, oddzielając go od innych parametrów przecinkami.</span><span class="sxs-lookup"><span data-stu-id="939bb-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="939bb-109">Określ typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="939bb-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="939bb-110">Postępuj zgodnie z nazwy parametru `As` klauzuli, aby określić typ danych.</span><span class="sxs-lookup"><span data-stu-id="939bb-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="939bb-111">Zdecyduj, mechanizm przekazywania, dla parametru.</span><span class="sxs-lookup"><span data-stu-id="939bb-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="939bb-112">Zazwyczaj należy przekazać parametr wg wartości, chyba że chcesz procedury, aby można było zmienić jego wartość w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="939bb-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="939bb-113">Poprzedź nazwę parametru z [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) Aby określić mechanizm przekazywania.</span><span class="sxs-lookup"><span data-stu-id="939bb-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="939bb-114">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="939bb-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="939bb-115">Jeśli parametr jest opcjonalny, poprzedź mechanizm przekazywania z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) i postępuj zgodnie z typem danych parametru znakiem równości (`=`) i wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="939bb-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="939bb-116">W poniższym przykładzie zdefiniowano konturu `Sub` procedury z trzema parametrami.</span><span class="sxs-lookup"><span data-stu-id="939bb-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="939bb-117">Wymagane są dwa pierwsze i trzeci jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="939bb-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="939bb-118">Deklaracji parametrów są rozdzielane na liście parametrów przecinkami.</span><span class="sxs-lookup"><span data-stu-id="939bb-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="939bb-119">Pierwszy parametr akceptuje `customer` obiektu, a `updateCustomer` można bezpośrednio zaktualizować zmiennej przekazany do `c` ponieważ argument jest przekazywany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="939bb-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="939bb-120">Procedury nie można zmienić wartości dwa ostatnie argumenty, ponieważ są one przekazywane [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="939bb-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="939bb-121">Jeśli kod wywołujący nie dostarcza wartość `level` parametru [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ustawia ją na wartość domyślną równą 0.</span><span class="sxs-lookup"><span data-stu-id="939bb-121">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="939bb-122">Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off`, `As` klauzuli jest opcjonalny, gdy Definiowanie parametru.</span><span class="sxs-lookup"><span data-stu-id="939bb-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="939bb-123">Jednak jeśli korzysta z żadnych jeden parametr `As` klauzuli wszystkich z nich należy użyć go.</span><span class="sxs-lookup"><span data-stu-id="939bb-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="939bb-124">Jeśli typ sprawdzania przełącznika `On`, `As` klauzula jest wymagany dla każdej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="939bb-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="939bb-125">Określanie typów danych dla wszystkich elementów programowania nosi nazwę *silne wpisywanie*.</span><span class="sxs-lookup"><span data-stu-id="939bb-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="939bb-126">Podczas ustawiania `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wymusza silne wpisywanie.</span><span class="sxs-lookup"><span data-stu-id="939bb-126">When you set `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforces strong typing.</span></span> <span data-ttu-id="939bb-127">Jest to zdecydowanie zalecane, z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="939bb-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="939bb-128">Umożliwia obsługę funkcji IntelliSense na parametry i zmienne.</span><span class="sxs-lookup"><span data-stu-id="939bb-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="939bb-129">Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich jako typu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="939bb-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="939bb-130">Umożliwia kompilatorowi sprawdzania typu.</span><span class="sxs-lookup"><span data-stu-id="939bb-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="939bb-131">Dzięki temu catch instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="939bb-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="939bb-132">Przechwytuje również wywołania metod, w obiektach, które nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="939bb-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="939bb-133">Wynikiem szybsze wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="939bb-133">It results in faster execution of your code.</span></span> <span data-ttu-id="939bb-134">Powodem tego jest to, że jeśli nie określisz typu danych dla elementu programistycznego, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora przypisuje go `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="939bb-134">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="939bb-135">Skompilowany kod może być konieczne Konwertuj i z powrotem między `Object` a innymi typami danych, co zmniejsza wydajność.</span><span class="sxs-lookup"><span data-stu-id="939bb-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939bb-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="939bb-136">See Also</span></span>  
 [<span data-ttu-id="939bb-137">Procedury</span><span class="sxs-lookup"><span data-stu-id="939bb-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="939bb-138">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="939bb-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="939bb-139">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="939bb-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="939bb-140">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="939bb-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="939bb-141">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="939bb-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="939bb-142">Procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="939bb-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="939bb-143">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="939bb-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="939bb-144">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="939bb-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="939bb-145">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="939bb-145">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)