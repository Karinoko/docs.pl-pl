---
title: "Porady: wiązanie danych do systemu Windows Presentation Foundation elementów (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f0ff1bed93d534dea3a407f4923e13856d761d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a><span data-ttu-id="d087c-102">Porady: wiązanie danych do systemu Windows Presentation Foundation elementów (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="d087c-102">How to: Bind Data to Windows Presentation Foundation Elements (WCF Data Services)</span></span>
<span data-ttu-id="d087c-103">Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać Windows Presentation Foundation (WPF) elementów, takich jak <xref:System.Windows.Controls.ListBox>"lub <xref:System.Windows.Controls.ComboBox> na wystąpienie <xref:System.Data.Services.Client.DataServiceCollection%601>, który obsługuje zdarzenia wygenerowane przez formanty, aby zachować <xref:System.Data.Services.Client.DataServiceContext> zsynchronizowany ze zmianami wprowadzone dane w formantach.</span><span class="sxs-lookup"><span data-stu-id="d087c-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can bind Windows Presentation Foundation (WPF) elements such as a <xref:System.Windows.Controls.ListBox>``or <xref:System.Windows.Controls.ComboBox> to an instance of <xref:System.Data.Services.Client.DataServiceCollection%601>, which handles the events raised by the controls to keep the <xref:System.Data.Services.Client.DataServiceContext> synchronized with changes made to data in the controls.</span></span> <span data-ttu-id="d087c-104">Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d087c-104">For more information, see [Binding Data to Controls](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d087c-105">Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas.</span><span class="sxs-lookup"><span data-stu-id="d087c-105">The example in this topic uses the Northwind sample data service and autogenerated client data service classes.</span></span> <span data-ttu-id="d087c-106">Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d087c-106">This service and the client data classes are created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d087c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d087c-107">Example</span></span>  
 <span data-ttu-id="d087c-108">Poniższy przykład pochodzi ze strony CodeBehind dla strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="d087c-108">The following example is from the code-behind page for an Extensible Application Markup Language (XAML) page that defines the `SalesOrders` window in WPF.</span></span> <span data-ttu-id="d087c-109">Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów filtrowane według kraju.</span><span class="sxs-lookup"><span data-stu-id="d087c-109">When the window is loaded, a <xref:System.Data.Services.Client.DataServiceCollection%601> is created based on the result of a query that returns customers, filtered by country.</span></span> <span data-ttu-id="d087c-110">Wszystkie strony tego wyniku stronicowanych zostały załadowane oraz powiązane zamówienia i są powiązane z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> czyli formant układu głównego okna WPF.</span><span class="sxs-lookup"><span data-stu-id="d087c-110">All of the pages of this paged result are loaded, along with the related orders, and are bound to the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.StackPanel> that is the root layout control for the WPF window.</span></span> <span data-ttu-id="d087c-111">Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d087c-111">For more information, see [Loading Deferred Content](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).</span></span>  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a><span data-ttu-id="d087c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d087c-112">Example</span></span>  
 <span data-ttu-id="d087c-113">Definiuje następujące XAML `SalesOrders` okna na platformie WPF w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d087c-113">The following XAML defines the `SalesOrders` window in WPF for the previous example.</span></span>  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a><span data-ttu-id="d087c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d087c-114">Example</span></span>  
 <span data-ttu-id="d087c-115">Poniższy przykład pochodzi ze strony CodeBehind dla strony Extensible Application Markup Language (XAML), który definiuje `SalesOrders` okna na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="d087c-115">The following example is from the code-behind page for an Extensible Application Markup Language (XAML) page that defines the `SalesOrders` window in WPF.</span></span> <span data-ttu-id="d087c-116">Po załadowaniu okna <xref:System.Data.Services.Client.DataServiceCollection%601> jest tworzony na podstawie wyniku zapytania, które zwraca klientów z powiązane obiekty filtrowane według kraju.</span><span class="sxs-lookup"><span data-stu-id="d087c-116">When the window is loaded, a <xref:System.Data.Services.Client.DataServiceCollection%601> is created based on the result of a query that returns customers with related objects, filtered by country.</span></span> <span data-ttu-id="d087c-117">Ten wynik jest powiązany z <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.StackPanel> czyli formant układu głównego okna WPF.</span><span class="sxs-lookup"><span data-stu-id="d087c-117">This result is bound to the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.StackPanel> that is the root layout control for the WPF window.</span></span>  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a><span data-ttu-id="d087c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d087c-118">Example</span></span>  
 <span data-ttu-id="d087c-119">Definiuje następujące XAML `SalesOrders` okna na platformie WPF w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d087c-119">The following XAML defines the `SalesOrders` window in WPF for the previous example.</span></span>  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]