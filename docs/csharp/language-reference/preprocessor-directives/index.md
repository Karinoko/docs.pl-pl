---
title: Dyrektywy preprocesora C#
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6378c8df794a4ee75e7b5ca283b18b228ba46383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="0148b-102">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="0148b-102">C# preprocessor directives</span></span>
<span data-ttu-id="0148b-103">Ta sekcja zawiera informacje o następujących dyrektywy preprocesora C#:</span><span class="sxs-lookup"><span data-stu-id="0148b-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="0148b-104">#if</span><span class="sxs-lookup"><span data-stu-id="0148b-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="0148b-105">#else</span><span class="sxs-lookup"><span data-stu-id="0148b-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="0148b-106">#elif</span><span class="sxs-lookup"><span data-stu-id="0148b-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="0148b-107">#endif</span><span class="sxs-lookup"><span data-stu-id="0148b-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="0148b-108">#define</span><span class="sxs-lookup"><span data-stu-id="0148b-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="0148b-109">#undef</span><span class="sxs-lookup"><span data-stu-id="0148b-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="0148b-110">#warning</span><span class="sxs-lookup"><span data-stu-id="0148b-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="0148b-111">#error</span><span class="sxs-lookup"><span data-stu-id="0148b-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="0148b-112">#line</span><span class="sxs-lookup"><span data-stu-id="0148b-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="0148b-113">#region</span><span class="sxs-lookup"><span data-stu-id="0148b-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="0148b-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="0148b-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="0148b-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="0148b-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="0148b-116">Ostrzeżenie #pragma</span><span class="sxs-lookup"><span data-stu-id="0148b-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="0148b-117">sumy kontrolnej #pragma</span><span class="sxs-lookup"><span data-stu-id="0148b-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="0148b-118">Zobacz tematy, aby uzyskać dodatkowe informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="0148b-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="0148b-119">Mimo że kompilator nie ma oddzielne preprocesora, dyrektywy opisane w tej sekcji są przetwarzane, jak w przypadku jednego.</span><span class="sxs-lookup"><span data-stu-id="0148b-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="0148b-120">Są one używane do pomocy w kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="0148b-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="0148b-121">W przeciwieństwie do dyrektywy C i C++ nie można użyć tych dyrektywy do tworzenia makr.</span><span class="sxs-lookup"><span data-stu-id="0148b-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="0148b-122">Dyrektywy preprocesora musi być tylko instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="0148b-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="0148b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0148b-123">See also</span></span>
 [<span data-ttu-id="0148b-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0148b-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0148b-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0148b-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)