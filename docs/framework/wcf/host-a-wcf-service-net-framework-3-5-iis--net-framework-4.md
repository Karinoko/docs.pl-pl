---
title: "Instrukcje: Hostowanie usługi WCF napisanej dla platformy .NET Framework 3.5 w usługach IIS działających na platformie .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e2c9dbf92ddaf1c23cb09184f046cb536717015
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a><span data-ttu-id="a0a47-102">Instrukcje: Hostowanie usługi WCF napisanej dla platformy .NET Framework 3.5 w usługach IIS działających na platformie .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="a0a47-102">How to: Host a WCF Service Written with .NET Framework 3.5 in IIS Running Under .NET Framework 4</span></span>
<span data-ttu-id="a0a47-103">Odnośnie do hostowania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] napisany za pomocą usługi [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] na uruchomionej maszynie [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], mogą wystąpić <xref:System.ServiceModel.ProtocolException> z następującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="a0a47-103">When hosting a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service written with [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] on a machine running [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], you may get a <xref:System.ServiceModel.ProtocolException> with the following text.</span></span>  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 <span data-ttu-id="a0a47-104">Lub Jeśli spróbujesz przejdź do pliku svc usługi może pojawić się Strona błędu z następującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="a0a47-104">Or if you try to browse to the service's .svc file you may see an error page with the following text.</span></span>  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 <span data-ttu-id="a0a47-105">Te błędy, ponieważ domena aplikacji, usługi IIS działają w ramach działa [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] i oczekuje, że usługa WCF uruchamiana [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0a47-105">These errors occur because the application domain IIS is running within is running [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] and the WCF service is expecting to run under [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="a0a47-106">W tym temacie opisano zmiany wymagane do pobrania usługi do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a0a47-106">This topic explains the modifications required to get the service to run.</span></span>  
  
 <span data-ttu-id="a0a47-107">Znajdź następny <`compilers`> elementu i zmień opcję CompilerVersion dostawcy wartości 4.0.</span><span class="sxs-lookup"><span data-stu-id="a0a47-107">Next find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="a0a47-108">Domyślnie są dwa <`compiler`> elementy w obszarze <`compilers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a0a47-108">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="a0a47-109">Należy zaktualizować opcja dostawcy CompilerVersion zarówno, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0a47-109">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a><span data-ttu-id="a0a47-110">Dodaj atrybut targetFramework wymagane</span><span class="sxs-lookup"><span data-stu-id="a0a47-110">Add the required targetFramework attribute</span></span>  
  
1.  <span data-ttu-id="a0a47-111">Otwórz plik Web.config usługi i Wyszukaj <`compilation`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a0a47-111">Open the service's Web.config file and look for the <`compilation`> element.</span></span>  
  
2.  <span data-ttu-id="a0a47-112">Dodaj `targetFramework` atrybutu <`compilation`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0a47-112">Add the `targetFramework` attribute to the <`compilation`> element as shown in the following example.</span></span>  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  <span data-ttu-id="a0a47-113">Znajdź <`compilers`> elementu i zmień opcję CompilerVersion dostawcy wartości 4.0.</span><span class="sxs-lookup"><span data-stu-id="a0a47-113">Find the <`compilers`> element and change the CompilerVersion provider option to have a value of 4.0.</span></span> <span data-ttu-id="a0a47-114">Domyślnie są dwa <`compiler`> elementy w obszarze <`compilers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a0a47-114">By default, there are two <`compiler`> elements under the <`compilers`> element.</span></span> <span data-ttu-id="a0a47-115">Należy zaktualizować opcja dostawcy CompilerVersion zarówno, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0a47-115">You must update the CompilerVersion provider option for both as shown in the following example.</span></span>  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```