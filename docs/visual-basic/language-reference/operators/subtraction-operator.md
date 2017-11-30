---
title: "- — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ffb7c96fe95e73dc857a15608df94ed8468f9df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="1c047-102">- — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c047-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="1c047-103">Zwraca różnicę dwóch wyrażeń liczbowych lub wartość ujemną wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1c047-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c047-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c047-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="1c047-105">Części</span><span class="sxs-lookup"><span data-stu-id="1c047-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="1c047-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="1c047-106">Required.</span></span> <span data-ttu-id="1c047-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="1c047-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1c047-108">Wymagany, chyba że `–` operator jest obliczenie wartości ujemnej.</span><span class="sxs-lookup"><span data-stu-id="1c047-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="1c047-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="1c047-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="1c047-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="1c047-110">Result</span></span>  
 <span data-ttu-id="1c047-111">Wynik jest różnica między `expression1` i `expression2`, lub o zanegowaną wartość `expression1`.</span><span class="sxs-lookup"><span data-stu-id="1c047-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="1c047-112">Typ danych wyniku jest odpowiednie dla typów dane typu liczbowego `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="1c047-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1c047-113">Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1c047-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1c047-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="1c047-114">Supported Types</span></span>  
 <span data-ttu-id="1c047-115">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="1c047-115">All numeric types.</span></span> <span data-ttu-id="1c047-116">Obejmuje to typy bez znaku i zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c047-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c047-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c047-117">Remarks</span></span>  
 <span data-ttu-id="1c047-118">W pierwsze użycie składnią pokazana wcześniej `–` operator jest *binarne* operator arytmetyczny odejmowania różnicę między dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1c047-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="1c047-119">W drugim użycia składnią pokazana wcześniej `–` operator jest *jednoargumentowy* operator negacji ujemną wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1c047-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="1c047-120">W tym sensie negacji składa się z cofania znak `expression1` tak, że wynik jest dodatnią Jeśli `expression1` jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="1c047-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="1c047-121">Jeśli wyrażenie zwraca [nic](../../../visual-basic/language-reference/nothing.md), `–` operator traktuje ją jako zero.</span><span class="sxs-lookup"><span data-stu-id="1c047-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c047-122">`–` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1c047-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1c047-123">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz, jego zachowanie ponownie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="1c047-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="1c047-124">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1c047-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c047-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c047-125">Example</span></span>  
 <span data-ttu-id="1c047-126">W poniższym przykładzie użyto `–` operatora, aby obliczyć i zwraca różnicę dwóch liczb, a następnie, aby odwrócić liczbą.</span><span class="sxs-lookup"><span data-stu-id="1c047-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="1c047-127">Po wykonaniu tych instrukcji `binaryResult` zawiera 124.45 i `unaryResult` zawiera –334.90.</span><span class="sxs-lookup"><span data-stu-id="1c047-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c047-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c047-128">See Also</span></span>  
 <span data-ttu-id="1c047-129">[-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="1c047-129">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span></span>  
 [<span data-ttu-id="1c047-130">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c047-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1c047-131">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1c047-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1c047-132">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c047-132">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)