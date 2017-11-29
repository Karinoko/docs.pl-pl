---
title: 'Porady: tworzenie procedury (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a44918b7a1426d215cee0ff2981f5763432a48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="4079e-102">Porady: tworzenie procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4079e-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="4079e-103">Umieść procedurę między początkową instrukcji deklaracji (`Sub` lub `Function`) i końcowej instrukcji deklaracji (`End Sub` lub `End Function`).</span><span class="sxs-lookup"><span data-stu-id="4079e-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="4079e-104">Kod wszystkie procedury znajduje się między te instrukcje.</span><span class="sxs-lookup"><span data-stu-id="4079e-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="4079e-105">Procedury nie może zawierać innej procedury, więc jego instrukcje początkowy i końcowy musi znajdować się poza innej procedury.</span><span class="sxs-lookup"><span data-stu-id="4079e-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="4079e-106">Jeśli masz kod, który wykonuje to samo zadanie w różnych miejscach, możesz zapisać zadania raz jako procedura i wywołać go z różnych miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4079e-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="4079e-107">Aby utworzyć procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="4079e-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="4079e-108">Poza innej procedury należy użyć `Sub` instrukcji, a następnie `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4079e-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="4079e-109">W `Sub` instrukcji, wykonaj `Sub` — słowo kluczowe z nazwą procedury ponownie z listą parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="4079e-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="4079e-110">Umieść instrukcji kodu procedury między `Sub` i `End Sub` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="4079e-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="4079e-111">Aby utworzyć procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="4079e-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="4079e-112">Poza innej procedury należy użyć `Function` instrukcji, a następnie `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4079e-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="4079e-113">W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedurą, a następnie z listą parametrów w nawiasy, a następnie `As` klauzuli określający typ danych wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="4079e-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="4079e-114">Umieść instrukcji kodu procedury między `Function` i `End Function` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="4079e-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="4079e-115">Użyj `Return` instrukcji, aby zwrócić wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="4079e-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="4079e-116">Aby połączyć nowe procedury z stare, powtarzających się bloki kodu</span><span class="sxs-lookup"><span data-stu-id="4079e-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="4079e-117">Upewnij się, że zdefiniujesz nowe procedury w miejscu, gdzie poprzedni kod ma do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="4079e-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="4079e-118">W bloku kodu stare, powtarzane, Zastąp instrukcji, które wykonują powtarzających się zadań z jednej instrukcji, która wywołuje `Sub` lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="4079e-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="4079e-119">Jeśli procedura jest `Function` zwracającego wartość, upewnij się, że instrukcji wywołujący wykonuje akcję z zwracanej wartości, takich jak przechowywanie ich w zmiennej, w przeciwnym razie wartość zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="4079e-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4079e-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="4079e-120">Example</span></span>  
 <span data-ttu-id="4079e-121">Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="4079e-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4079e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4079e-122">See Also</span></span>  
 [<span data-ttu-id="4079e-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="4079e-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="4079e-124">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="4079e-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="4079e-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="4079e-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="4079e-126">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="4079e-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="4079e-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="4079e-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="4079e-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="4079e-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="4079e-129">Procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="4079e-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="4079e-130">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="4079e-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="4079e-131">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="4079e-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="4079e-132">Programowanie zorientowane obiektowo</span><span class="sxs-lookup"><span data-stu-id="4079e-132">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)