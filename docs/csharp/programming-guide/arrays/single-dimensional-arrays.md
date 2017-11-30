---
title: "Tablice jednowymiarowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fed9042ba37164927bb8073bc669fafeb5d40598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="bae00-102">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bae00-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="bae00-103">Można zadeklarować tablicy jednowymiarowej pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bae00-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 <span data-ttu-id="bae00-104">Ta tablica zawiera elementy z `array[0]` do `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="bae00-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="bae00-105">[Nowe](../../../csharp/language-reference/keywords/new.md) operator jest używany do utworzenia tablicy i zainicjować elementów tablicy do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="bae00-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="bae00-106">W tym przykładzie wszystkie elementy tablicy są inicjowane od zera.</span><span class="sxs-lookup"><span data-stu-id="bae00-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="bae00-107">Tablica, która przechowuje elementy parametry mogą być deklarowane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="bae00-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="bae00-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bae00-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="bae00-109">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="bae00-109">Array Initialization</span></span>  
 <span data-ttu-id="bae00-110">Można zainicjować tablicy po deklaracji, w którym to przypadku specyfikator rangi nie jest potrzebna, ponieważ jest już podana przez liczbę elementów na liście inicjowania.</span><span class="sxs-lookup"><span data-stu-id="bae00-110">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="bae00-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bae00-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 <span data-ttu-id="bae00-112">W ten sam sposób można zainicjować tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="bae00-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="bae00-113">Oto deklarację tablicy ciągów której każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="bae00-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 <span data-ttu-id="bae00-114">Podczas inicjowania tablicy po deklaracji, można użyć następujących skrótów klawiaturowych:</span><span class="sxs-lookup"><span data-stu-id="bae00-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 <span data-ttu-id="bae00-115">Można zadeklarować zmiennej tablicowej bez inicjowania, ale muszą używać `new` operator podczas przypisywania tablicą do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bae00-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="bae00-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bae00-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 <span data-ttu-id="bae00-117">C# 3.0 wprowadzono niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="bae00-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="bae00-118">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bae00-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="bae00-119">Typ wartości i tablic typu odwołania</span><span class="sxs-lookup"><span data-stu-id="bae00-119">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="bae00-120">Należy wziąć pod uwagę następujące oświadczenie tablicy:</span><span class="sxs-lookup"><span data-stu-id="bae00-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 <span data-ttu-id="bae00-121">Wynik tej instrukcji jest zależny od tego, czy `SomeType` jest typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="bae00-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="bae00-122">Jeśli jest to typ wartości, instrukcja tworzy tablicę 10 elementów, z których każdy ma typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="bae00-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="bae00-123">Jeśli `SomeType` jest typem referencyjnym instrukcji tworzy tablicę 10 elementów, z których każdy jest ustawiana na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="bae00-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="bae00-124">Aby uzyskać więcej informacji na temat typów wartości i typy referencyjne, zobacz [typów](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="bae00-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae00-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bae00-125">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="bae00-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bae00-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bae00-127">Tablice</span><span class="sxs-lookup"><span data-stu-id="bae00-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="bae00-128">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="bae00-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="bae00-129">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="bae00-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)