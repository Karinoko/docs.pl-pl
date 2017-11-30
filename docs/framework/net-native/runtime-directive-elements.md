---
title: "Elementy dyrektyw środowiska uruchomieniowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3143c6b78749f3339e7e7195b551b5a5c31fad12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="83260-102">Elementy dyrektyw środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="83260-102">Runtime Directive Elements</span></span>
<span data-ttu-id="83260-103">Format pliku dyrektyw (rd.xml) środowiska uruchomieniowego obsługuje następujące elementy dyrektyw środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="83260-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="83260-104">Zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) reprezentacji hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="83260-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="83260-105">\<Aplikacji ></span><span class="sxs-lookup"><span data-stu-id="83260-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="83260-106">Zastosowanie zasad wykonywania odbicia do wszystkich typów, używany przez aplikację i służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83260-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="83260-107">To jest elementem podrzędnym [ \<dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="83260-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="83260-108">\<Zestaw ></span><span class="sxs-lookup"><span data-stu-id="83260-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="83260-109">Stosuje runnntime zasady do wszystkich typów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="83260-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="83260-110">To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-111">\<AttributeImplies ></span><span class="sxs-lookup"><span data-stu-id="83260-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="83260-112">Jeśli jego zawierający [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) dyrektywa jest atrybutu, elementy kodu, do których zastosowano ten atrybut ma zastosowanie zasad wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83260-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="83260-113">\<Dyrektywy ></span><span class="sxs-lookup"><span data-stu-id="83260-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="83260-114">W każdym pliku dyrektyw środowiska uruchomieniowego dla elementu głównego [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83260-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="83260-115">Jego elementy podrzędne są [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="83260-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="83260-116">\<Zdarzenie ></span><span class="sxs-lookup"><span data-stu-id="83260-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="83260-117">Zastosowanie zasad wykonywania na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="83260-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="83260-118">To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-119">\<Pole ></span><span class="sxs-lookup"><span data-stu-id="83260-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="83260-120">Zastosowanie zasad wykonywania do pola.</span><span class="sxs-lookup"><span data-stu-id="83260-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="83260-121">To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-122">\<GenericParameter ></span><span class="sxs-lookup"><span data-stu-id="83260-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="83260-123">Zastosowanie zasad wykonywania na typ parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="83260-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="83260-124">\<ImpliesType ></span><span class="sxs-lookup"><span data-stu-id="83260-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="83260-125">W przypadku zasad wykonywania na typ, że zasady zostały zastosowane do typu zawierającego lub metody.</span><span class="sxs-lookup"><span data-stu-id="83260-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="83260-126">\<Biblioteka ></span><span class="sxs-lookup"><span data-stu-id="83260-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="83260-127">Dotyczy wszystkich typów w zestawie zasad wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83260-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="83260-128">To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-129">\<Metoda ></span><span class="sxs-lookup"><span data-stu-id="83260-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="83260-130">Zastosowanie zasad wykonywania do metody.</span><span class="sxs-lookup"><span data-stu-id="83260-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="83260-131">To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-132">\<MethodInstantiation ></span><span class="sxs-lookup"><span data-stu-id="83260-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="83260-133">Stosuje zasady środowiska uruchomieniowego do skonstruowanego metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="83260-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="83260-134">To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-135">\<Namespace ></span><span class="sxs-lookup"><span data-stu-id="83260-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="83260-136">Zastosowanie zasad wykonywania dla wszystkich typów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="83260-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="83260-137">\<Parametr ></span><span class="sxs-lookup"><span data-stu-id="83260-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="83260-138">Zastosowanie zasad wykonywania na typ argumentu przekazanego do metody.</span><span class="sxs-lookup"><span data-stu-id="83260-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="83260-139">\<Właściwość ></span><span class="sxs-lookup"><span data-stu-id="83260-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="83260-140">Zastosowanie zasad wykonywania na właściwość.</span><span class="sxs-lookup"><span data-stu-id="83260-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="83260-141">To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.</span><span class="sxs-lookup"><span data-stu-id="83260-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="83260-142">\<Subtypes ></span><span class="sxs-lookup"><span data-stu-id="83260-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="83260-143">Zastosowanie zasad wykonywania dla wszystkich klas dziedziczony z typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="83260-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="83260-144">\<Typ ></span><span class="sxs-lookup"><span data-stu-id="83260-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="83260-145">Zastosowanie zasad wykonywania do typu.</span><span class="sxs-lookup"><span data-stu-id="83260-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="83260-146">\<TypeInstantiation ></span><span class="sxs-lookup"><span data-stu-id="83260-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="83260-147">Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="83260-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="83260-148">\<TypeParameter ></span><span class="sxs-lookup"><span data-stu-id="83260-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="83260-149">Zastosowanie zasad wykonywania na typ reprezentowany przez <xref:System.Type> argument przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="83260-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83260-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83260-150">See Also</span></span>  
 [<span data-ttu-id="83260-151">Dokumentacja pliku RD.XML konfiguracji</span><span class="sxs-lookup"><span data-stu-id="83260-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)