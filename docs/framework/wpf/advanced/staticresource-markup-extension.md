---
title: "StaticResource — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="1a919-102">StaticResource — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="1a919-102">StaticResource Markup Extension</span></span>
<span data-ttu-id="1a919-103">Zawiera wartość dla każdego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu właściwości wyszukując odwołanie do zasobu już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="1a919-103">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="1a919-104">Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem wyszukiwanie czas ładowania, które będzie wyglądać na zasoby, które wcześniej zostały załadowane z poziomu znacznika bieżącego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony oraz innych źródeł aplikacji i wygeneruje tej wartości zasobu jako wartość właściwości w obiektach czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a919-104">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1a919-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="1a919-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1a919-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="1a919-106">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1a919-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="1a919-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="1a919-108">Klucz do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1a919-108">The key for the requested resource.</span></span> <span data-ttu-id="1a919-109">Ten klucz była początkowo przypisana przez [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasób został utworzony w znaczniku, czy podany jako `key` parametr podczas wywoływania metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Jeśli zasób został utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a919-109">This key was initially assigned by the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a919-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a919-110">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1a919-111">A `StaticResource` nie należy próbować do przodu odnieść się do zasobu, która jest zdefiniowana lexically dalsze w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.</span><span class="sxs-lookup"><span data-stu-id="1a919-111">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="1a919-112">Próby nie jest obsługiwany, a nawet, jeśli odniesienie nie powiedzie się, próby odwołaniem w przód będzie spowodować zmniejszenie wydajności czasu obciążenia podczas tabel skrótu wewnętrznego reprezentujące <xref:System.Windows.ResourceDictionary> są przeszukiwane.</span><span class="sxs-lookup"><span data-stu-id="1a919-112">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="1a919-113">Aby uzyskać najlepsze rezultaty należy dopasować kompozycji słownikach zasobów tak, aby uniknąć odwołania w przód.</span><span class="sxs-lookup"><span data-stu-id="1a919-113">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="1a919-114">Jeśli nie można uniknąć odwołaniem w przód, użyj [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1a919-114">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="1a919-115">Określony <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> powinien odpowiadać istniejącego zasobu, oznaczone symbolem [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) na określonym poziomie w ze strony, aplikacji, kompozycje dostępne kontrolki i zasobów zewnętrznych lub zasoby systemowe.</span><span class="sxs-lookup"><span data-stu-id="1a919-115">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="1a919-116">Wyszukiwanie zasobów występuje w podanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1a919-116">The resource lookup occurs in that order.</span></span> <span data-ttu-id="1a919-117">Aby uzyskać więcej informacji na temat zachowanie wyszukiwania zasobów dla statycznych i dynamicznych zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1a919-117">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="1a919-118">Klucz zasobu może być zdefiniowany w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="1a919-118">A resource key can be any string defined in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="1a919-119">Klucz zasobu można też inne typy obiektów, takich jak <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1a919-119">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="1a919-120">A <xref:System.Type> klucza jest niezbędne, aby jak formantów można wstawiony przez kompozycje, za pomocą klucza niejawne stylu.</span><span class="sxs-lookup"><span data-stu-id="1a919-120">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="1a919-121">Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1a919-121">For more information, see [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="1a919-122">Deklaracyjne alternatywnych środków odwołujące się do zasobu jest jako [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="1a919-122">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="1a919-123">Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="1a919-123">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="1a919-124">Token ciągu po `StaticResource` przypisany jako identyfikator ciągu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> wartości podstawowych <xref:System.Windows.StaticResourceExtension> rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="1a919-124">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="1a919-125">`StaticResource`można w składni elementu obiekt.</span><span class="sxs-lookup"><span data-stu-id="1a919-125">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="1a919-126">W takim przypadku określającą wartość <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwość jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="1a919-126">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="1a919-127">`StaticResource`można również w Określa użycie atrybutu pełne <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> właściwości jako właściwość = pary wartości:</span><span class="sxs-lookup"><span data-stu-id="1a919-127">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 <span data-ttu-id="1a919-128">Szczegółowe definicje są często przydatne w rozszerzeniach zawierających więcej niż jedną konfigurowalną właściwość albo gdy niektóre właściwości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1a919-128">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="1a919-129">Ponieważ `StaticResource` ma tylko jedną można ustawić właściwości, która jest wymagana, to użycie Pełne nie są typowe.</span><span class="sxs-lookup"><span data-stu-id="1a919-129">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="1a919-130">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.StaticResourceExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="1a919-130">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="1a919-131">`StaticResource`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="1a919-131">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="1a919-132">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="1a919-132">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="1a919-133">Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1a919-133">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="1a919-134">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1a919-134">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a919-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a919-135">See Also</span></span>  
 [<span data-ttu-id="1a919-136">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="1a919-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="1a919-137">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1a919-137">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="1a919-138">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="1a919-138">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="1a919-139">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="1a919-139">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="1a919-140">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="1a919-140">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)