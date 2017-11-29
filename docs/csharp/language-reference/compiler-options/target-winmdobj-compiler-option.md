---
title: '-docelowych: winmdobj (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f690591b79159a0196a1637903f2cc53442976e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinmdobj-c-compiler-options"></a><span data-ttu-id="57a96-102">/target:winmdobj (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="57a96-102">/target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="57a96-103">Jeśli używasz **/target: winmdobj** — opcja kompilatora, kompilator tworzy plik pośredni .winmdobj, który można przekonwertować na plik binarny (.winmd) środowiska wykonawczego systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a96-103">If you use the **/target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="57a96-104">Plik winmd, następnie mogą być używane przez programy JavaScript i C++, oprócz programów zarządzanych języka.</span><span class="sxs-lookup"><span data-stu-id="57a96-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a96-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="57a96-105">Syntax</span></span>  
  
```console  
/target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="57a96-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57a96-106">Remarks</span></span>  
 <span data-ttu-id="57a96-107">**Winmdobj** ustawienie sygnały kompilatora, że moduł pośredniego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="57a96-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="57a96-108">Program Visual Studio kompiluje biblioteki klas C# jako plik .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="57a96-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="57a96-109">Plik .winmdobj można następnie przekazywani za pośrednictwem <xref:Microsoft.Build.Tasks.WinMDExp> wyeksportować narzędzie w celu utworzenia pliku metadanych (.winmd) systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a96-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="57a96-110">Plik winmd zawiera kod z oryginalnej biblioteki i metadanych WinMD, które jest używane przez JavaScript lub C++ i środowiska wykonawczego systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a96-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="57a96-111">Dane wyjściowe pliku, który ma być kompilowana przy użyciu **/target: winmdobj** — opcja kompilatora jest przeznaczony do użytku tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; sam plik .winmdobj nie jest przywoływany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="57a96-111">The output of a file that’s compiled by using the **/target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="57a96-112">Jeśli nie używasz [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.</span><span class="sxs-lookup"><span data-stu-id="57a96-112">Unless you use the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="57a96-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="57a96-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="57a96-114">Jeśli określono opcję/target: winmdobj w wierszu polecenia, wszystkie pliki, aż do następnego **/out** lub [/target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) opcji są używane do tworzenia programu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a96-114">If you specify the /target:winmdobj option at a command prompt, all files until the next **/out** or [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="57a96-115">Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57a96-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="57a96-116">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="57a96-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="57a96-117">Wybierz **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="57a96-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="57a96-118">W **Output typu** wybierz **pliku WinMD**.</span><span class="sxs-lookup"><span data-stu-id="57a96-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="57a96-119">**Pliku WinMD** opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57a96-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="57a96-120">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="57a96-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57a96-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="57a96-121">Example</span></span>  
 <span data-ttu-id="57a96-122">Następujące polecenie kompiluje `filename.cs` do pliku pośredniego .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="57a96-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc /target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="57a96-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57a96-123">See Also</span></span>  
 [<span data-ttu-id="57a96-124">/ TARGET (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="57a96-124">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="57a96-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="57a96-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)