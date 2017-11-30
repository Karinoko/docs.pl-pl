---
title: "Udostępnianie składników COM programowi.NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26efd43a05252e657626063d7dd04b1020dace18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="5534a-102">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5534a-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="5534a-103">Ta sekcja zawiera podsumowanie procesu potrzebne do udostępnienia istniejących składnika modelu COM z kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="5534a-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="5534a-104">Aby uzyskać informacje na temat pisania serwerów COM to ściśle zintegrowane z programu .NET Framework, zobacz [projektowania współdziałanie](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span><span class="sxs-lookup"><span data-stu-id="5534a-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689).</span></span>  
  
 <span data-ttu-id="5534a-105">Istniejące składniki COM są cenne zasoby pozostają dostępne w zarządzanym kodzie jako biznesowym warstwy środkowej aplikacje lub funkcje izolowanym.</span><span class="sxs-lookup"><span data-stu-id="5534a-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="5534a-106">Składnik idealne ma podstawowego zestawu międzyoperacyjnego i ściśle zgodne ze standardami programowania narzucone przez COM.</span><span class="sxs-lookup"><span data-stu-id="5534a-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="5534a-107">Aby udostępnić składników modelu COM aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5534a-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="5534a-108">[Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5534a-108">[Import a type library as an assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="5534a-109">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy COM.</span><span class="sxs-lookup"><span data-stu-id="5534a-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="5534a-110">Istnieje kilka sposobów można uzyskać zestawu zawierającego typów COM zaimportowana jako metadanych.</span><span class="sxs-lookup"><span data-stu-id="5534a-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="5534a-111">[Tworzenie typów COM w kodzie zarządzanym](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span><span class="sxs-lookup"><span data-stu-id="5534a-111">[Create COM types in managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
     <span data-ttu-id="5534a-112">Można sprawdzić typów COM, aktywować wystąpień i wywołania metod w obiekcie COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5534a-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="5534a-113">[Kompilowanie projektu międzyoperacyjnego](../../../docs/framework/interop/compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="5534a-113">[Compile an interop project](../../../docs/framework/interop/compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="5534a-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Zapewnia kilka języków zgodne z wspólnego języka specyfikacji (ze specyfikacją CLS), łącznie z kompilatorów [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++.</span><span class="sxs-lookup"><span data-stu-id="5534a-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="5534a-115">[Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="5534a-115">[Deploy an interop application](../../../docs/framework/interop/deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="5534a-116">Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), podpisany zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5534a-116">Interop applications are best deployed as [strong-named](../../../docs/framework/app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5534a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5534a-117">See Also</span></span>  
 [<span data-ttu-id="5534a-118">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="5534a-118">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="5534a-119">Zagadnienia dotyczące projektowania dla współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5534a-119">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [<span data-ttu-id="5534a-120">Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer COM</span><span class="sxs-lookup"><span data-stu-id="5534a-120">COM Interop Sample: .NET Client and COM Server</span></span>](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="5534a-121">Niezależność od języka i elementy niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="5534a-121">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="5534a-122">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="5534a-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)