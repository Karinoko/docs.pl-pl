---
title: "Jak utworzyć dodatek, który zwraca interfejs użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd6956f1934f8594a941b57066cc2d4d6214a9a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="915ac-102">Jak utworzyć dodatek, który zwraca interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="915ac-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="915ac-103">W tym przykładzie przedstawiono sposób tworzenia dodatku, który zwraca [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja autonomiczna.</span><span class="sxs-lookup"><span data-stu-id="915ac-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="915ac-104">Dodatek zwraca [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czyli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="915ac-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="915ac-105">Zawartość kontrolki użytkownika jest pojedynczy przycisku, po kliknięciu wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="915ac-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="915ac-106">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Aplikacja autonomiczna obsługuje dodatek i wyświetla kontrolki użytkownika (zwracanym przez dodatek) jako zawartość okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="915ac-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="915ac-107">**Wymagania wstępne**</span><span class="sxs-lookup"><span data-stu-id="915ac-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="915ac-108">W tym przykładzie wyróżniono [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzeń [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, Włącz w tym scenariuszu, która przyjmuje następujące:</span><span class="sxs-lookup"><span data-stu-id="915ac-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="915ac-109">Znajomość [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dodatku modelu, w tym potoku dodatku i rozwoju hosta.</span><span class="sxs-lookup"><span data-stu-id="915ac-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="915ac-110">Jeśli znasz tych pojęć, zobacz [dodatki i rozszerzalność](../../../../docs/framework/add-ins/index.md).</span><span class="sxs-lookup"><span data-stu-id="915ac-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="915ac-111">Samouczek przedstawiający implementacji potoku, dodatek i aplikacji hosta, zobacz [wskazówki: tworzenie aplikacji rozszerzalnej](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span><span class="sxs-lookup"><span data-stu-id="915ac-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="915ac-112">Znajomość [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozszerzenia do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, który można znaleźć tutaj: [omówienie Add-Ins WPF](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span><span class="sxs-lookup"><span data-stu-id="915ac-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="915ac-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="915ac-113">Example</span></span>  
 <span data-ttu-id="915ac-114">Aby utworzyć dodatku, który zwraca [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wymaga określonego kodu dla każdego segmentu potoku dodatku i aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="915ac-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="915ac-115">Implementowanie kontraktu segmentów potoku</span><span class="sxs-lookup"><span data-stu-id="915ac-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="915ac-116">Metoda musi być zdefiniowany przez kontraktu dla zwracania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], a jego wartości zwracanej musi być typu <xref:System.AddIn.Contract.INativeHandleContract>.</span><span class="sxs-lookup"><span data-stu-id="915ac-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="915ac-117">Wskazuje na `GetAddInUI` metody `IWPFAddInContract` kontraktu w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="915ac-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="915ac-118">Implementowanie segmentów potoku dodatku widoku</span><span class="sxs-lookup"><span data-stu-id="915ac-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="915ac-119">Ponieważ dodatek implementuje [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] zapewnia jako podklasy <xref:System.Windows.FrameworkElement>, metoda odpowiadająca widoku Dodaj `IWPFAddInView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="915ac-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="915ac-120">Poniższy kod przedstawia widok dodatku kontraktu implementowany jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="915ac-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="915ac-121">Implementowanie segmentów potoku Dodaj strony karty</span><span class="sxs-lookup"><span data-stu-id="915ac-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="915ac-122">Zwraca metodę kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale dodatek zwraca <xref:System.Windows.FrameworkElement> (jak określono w widoku dodatku).</span><span class="sxs-lookup"><span data-stu-id="915ac-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="915ac-123">W rezultacie <xref:System.Windows.FrameworkElement> muszą zostać skonwertowane do <xref:System.AddIn.Contract.INativeHandleContract> przed przekroczeniem granic izolacji.</span><span class="sxs-lookup"><span data-stu-id="915ac-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="915ac-124">To zadanie jest wykonywane przez karty Dodaj w stronie przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="915ac-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="915ac-125">Implementowanie segmentów potoku widoku hosta</span><span class="sxs-lookup"><span data-stu-id="915ac-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="915ac-126">Ponieważ aplikacja hosta będzie wyświetlana <xref:System.Windows.FrameworkElement>, metoda w widoku hosta, które są powiązane z `IWPFAddInHostView.GetAddInUI` musi zwracać wartość typu <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="915ac-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="915ac-127">Poniższy kod przedstawia widok hosta kontraktu implementowany jako interfejs.</span><span class="sxs-lookup"><span data-stu-id="915ac-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="915ac-128">Implementowanie segmentów potoku karty po stronie hosta</span><span class="sxs-lookup"><span data-stu-id="915ac-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="915ac-129">Zwraca metodę kontraktu <xref:System.AddIn.Contract.INativeHandleContract>, ale oczekuje aplikacji hosta <xref:System.Windows.FrameworkElement> (jak określono w widoku hosta).</span><span class="sxs-lookup"><span data-stu-id="915ac-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="915ac-130">W rezultacie <xref:System.AddIn.Contract.INativeHandleContract> muszą zostać skonwertowane do <xref:System.Windows.FrameworkElement> po przekroczeniu granic izolacji.</span><span class="sxs-lookup"><span data-stu-id="915ac-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="915ac-131">To zadanie jest wykonywane przez adaptery po stronie hosta przez wywołanie metody <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="915ac-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="915ac-132">Implementowanie dodatku</span><span class="sxs-lookup"><span data-stu-id="915ac-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="915ac-133">Dodaj w stronie karty i dodatku Widok utworzony, dodatek (`WPFAddIn1.AddIn`) musi implementować `IWPFAddInView.GetAddInUI` metodę, aby zwrócić <xref:System.Windows.FrameworkElement> obiektu ( <xref:System.Windows.Controls.UserControl> w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="915ac-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="915ac-134">Implementacja <xref:System.Windows.Controls.UserControl>, `AddInUI`, przedstawiono w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="915ac-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="915ac-135">Implementacja `IWPFAddInView.GetAddInUI` przez dodatek musi zwrócić nowe wystąpienie klasy `AddInUI`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="915ac-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="915ac-136">Wdrażanie aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="915ac-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="915ac-137">Adaptery po stronie hosta i widoku hosta utworzony, można użyć aplikacji hosta [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modelu dodatku, aby otworzyć potoku, uzyskać widoku hosta dodatku, i wywołanie `IWPFAddInHostView.GetAddInUI` metody.</span><span class="sxs-lookup"><span data-stu-id="915ac-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="915ac-138">Te kroki przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="915ac-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="915ac-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="915ac-139">See Also</span></span>  
 [<span data-ttu-id="915ac-140">Dodatki i rozszerzalność</span><span class="sxs-lookup"><span data-stu-id="915ac-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="915ac-141">Omówienie dodatków WPF</span><span class="sxs-lookup"><span data-stu-id="915ac-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)