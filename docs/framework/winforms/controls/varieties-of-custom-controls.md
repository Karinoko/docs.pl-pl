---
title: "Różne typy formantów niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a8d858228630147e1fbcdfab6a52fba5a63a566
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="varieties-of-custom-controls"></a><span data-ttu-id="3d843-102">Różne typy formantów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3d843-102">Varieties of Custom Controls</span></span>
<span data-ttu-id="3d843-103">Z programu .NET Framework mogą tworzyć i wdrożyć nowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3d843-103">With the .NET Framework, you can develop and implement new controls.</span></span> <span data-ttu-id="3d843-104">Można rozszerzyć funkcjonalność kontrolki użytkownika znanych także jako istniejących formantów przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="3d843-104">You can extend the functionality of the familiar user control as well as existing controls through inheritance.</span></span> <span data-ttu-id="3d843-105">Można również napisać formantów niestandardowych, które własnych narysowania.</span><span class="sxs-lookup"><span data-stu-id="3d843-105">You can also write custom controls that perform their own painting.</span></span>  
  
 <span data-ttu-id="3d843-106">Przy wyborze, jakiego rodzaju formantu, aby utworzyć może być mylące.</span><span class="sxs-lookup"><span data-stu-id="3d843-106">Deciding which kind of control to create can be confusing.</span></span> <span data-ttu-id="3d843-107">W tym temacie omówiono różnice między różne rodzaje formantów, z którego może dziedziczyć i dostarcza informacji o wybieraniu określonego typu formantu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3d843-107">This topic highlights the differences among the various kinds of controls from which you can inherit, and provides you with information about how to choose a particular kind of control for your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d843-108">Aby uzyskać informacji o tworzeniu formant do użycia w formularzach sieci Web, zobacz [tworzenia kontrolek serwera ASP.NET niestandardowe](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="3d843-108">For information about authoring a control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="base-control-class"></a><span data-ttu-id="3d843-109">Klasa podstawowa sterowania</span><span class="sxs-lookup"><span data-stu-id="3d843-109">Base Control Class</span></span>  
 <span data-ttu-id="3d843-110"><xref:System.Windows.Forms.Control> Klasa jest klasą bazową dla formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-110">The <xref:System.Windows.Forms.Control> class is the base class for Windows Forms controls.</span></span> <span data-ttu-id="3d843-111">Zapewnia infrastruktury wymaganej do wyświetlania w aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-111">It provides the infrastructure required for visual display in Windows Forms applications.</span></span>  
  
 <span data-ttu-id="3d843-112"><xref:System.Windows.Forms.Control> Klasa wykonuje następujące zadania w celu zapewnienia wyświetlania w aplikacji formularzy systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="3d843-112">The <xref:System.Windows.Forms.Control> class performs the following tasks to provide visual display in Windows Forms applications:</span></span>  
  
-   <span data-ttu-id="3d843-113">Przedstawia uchwytu okna.</span><span class="sxs-lookup"><span data-stu-id="3d843-113">Exposes a window handle.</span></span>  
  
-   <span data-ttu-id="3d843-114">Zarządza rozsyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3d843-114">Manages message routing.</span></span>  
  
-   <span data-ttu-id="3d843-115">Zapewnia zdarzenia klawiatury i myszy oraz wiele innych zdarzeń interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d843-115">Provides mouse and keyboard events, and many other user interface events.</span></span>  
  
-   <span data-ttu-id="3d843-116">Udostępnia funkcje zaawansowane układu.</span><span class="sxs-lookup"><span data-stu-id="3d843-116">Provides advanced layout features.</span></span>  
  
-   <span data-ttu-id="3d843-117">Zawiera wiele właściwości specyficzne dla wyświetlania, takie jak <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, i <xref:System.Windows.Forms.Control.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d843-117">Contains many properties specific to visual display, such as <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, and <xref:System.Windows.Forms.Control.Width%2A>.</span></span>  
  
-   <span data-ttu-id="3d843-118">Zapewnia bezpieczeństwo i obsługa wątkowości niezbędne dla formantu formularzy systemu Windows do działania jako formant ActiveX Microsoft®.</span><span class="sxs-lookup"><span data-stu-id="3d843-118">Provides the security and threading support necessary for a Windows Forms control to act as a Microsoft® ActiveX® control.</span></span>  
  
 <span data-ttu-id="3d843-119">Ponieważ duża część infrastruktury jest dostarczany przez klasę podstawową, jest stosunkowo łatwa do opracowywania własnych formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-119">Because so much of the infrastructure is provided by the base class, it is relatively easy to develop your own Windows Forms controls.</span></span>  
  
## <a name="kinds-of-controls"></a><span data-ttu-id="3d843-120">Typy formantów</span><span class="sxs-lookup"><span data-stu-id="3d843-120">Kinds of Controls</span></span>  
 <span data-ttu-id="3d843-121">Formularze systemu Windows obsługuje trzy rodzaje kontrolki użytkownika: *złożonego*, *rozszerzonej*, i *niestandardowych*.</span><span class="sxs-lookup"><span data-stu-id="3d843-121">Windows Forms supports three kinds of user-defined controls: *composite*, *extended*, and *custom*.</span></span> <span data-ttu-id="3d843-122">W poniższych sekcjach opisano każdy rodzaj kontroli i nadaj zalecenia dotyczące wybierania rodzaj do użycia w projektach.</span><span class="sxs-lookup"><span data-stu-id="3d843-122">The following sections describe each kind of control and give recommendations for choosing the kind to use in your projects.</span></span>  
  
### <a name="composite-controls"></a><span data-ttu-id="3d843-123">Formanty złożone</span><span class="sxs-lookup"><span data-stu-id="3d843-123">Composite Controls</span></span>  
 <span data-ttu-id="3d843-124">Formantu złożonego jest kolekcją hermetyzowane w wspólnego kontenera formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-124">A composite control is a collection of Windows Forms controls encapsulated in a common container.</span></span> <span data-ttu-id="3d843-125">Tego rodzaju kontroli jest czasami nazywany *kontrolki użytkownika*.</span><span class="sxs-lookup"><span data-stu-id="3d843-125">This kind of control is sometimes called a *user control*.</span></span> <span data-ttu-id="3d843-126">Formanty zawarte są nazywane *formanty składników*.</span><span class="sxs-lookup"><span data-stu-id="3d843-126">The contained controls are called *constituent controls*.</span></span>  
  
 <span data-ttu-id="3d843-127">Formantu złożonego zawiera wszystkie funkcje dostępu do właściwych skojarzone z poszczególnymi zawartych w niej formanty formularzy systemu Windows i umożliwia selektywne ujawnia i powiąż ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d843-127">A composite control holds all of the inherent functionality associated with each of the contained Windows Forms controls and enables you to selectively expose and bind their properties.</span></span> <span data-ttu-id="3d843-128">Formantu złożonego za zapewnia także dużą domyślnie za pomocą klawiatury funkcje z nie dodatkowych nakład pracy ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d843-128">A composite control also provides a great deal of default keyboard handling functionality with no extra development effort on your part.</span></span>  
  
 <span data-ttu-id="3d843-129">Na przykład formantu złożonego mogą być zbudowane do wyświetlania danych adresów klienta z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3d843-129">For example, a composite control could be built to display customer address data from a database.</span></span> <span data-ttu-id="3d843-130">Ten formant może obejmować <xref:System.Windows.Forms.DataGridView> formantu, aby wyświetlić pola bazy danych, <xref:System.Windows.Forms.BindingSource> do obsługi powiązania ze źródłem danych, a <xref:System.Windows.Forms.BindingNavigator> formantu, aby przechodzić.</span><span class="sxs-lookup"><span data-stu-id="3d843-130">This control could include a <xref:System.Windows.Forms.DataGridView> control to display the database fields, a <xref:System.Windows.Forms.BindingSource> to handle binding to a data source, and a <xref:System.Windows.Forms.BindingNavigator> control to move through the records.</span></span> <span data-ttu-id="3d843-131">Można selektywnie ujawnić właściwości powiązań danych, a można spakować i ponowne użycie kontroli całego od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d843-131">You could selectively expose data binding properties, and you could package and reuse the entire control from application to application.</span></span> <span data-ttu-id="3d843-132">Na przykład tego rodzaju formantu złożonego zobacz [porady: zastosowanie atrybutów w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3d843-132">For an example of this kind of composite control, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="3d843-133">Do tworzenia złożonych kontrolek, pochodzi z <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d843-133">To author a composite control, derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="3d843-134"><xref:System.Windows.Forms.UserControl> Klasy podstawowej zapewnia routing klawiatury podrzędne kontrolki i umożliwia formantów podrzędnych z działa jako grupa.</span><span class="sxs-lookup"><span data-stu-id="3d843-134">The <xref:System.Windows.Forms.UserControl> base class provides keyboard routing for child controls and enables child controls to work as a group.</span></span> <span data-ttu-id="3d843-135">Aby uzyskać więcej informacji, zobacz [opracowywanie złożonego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d843-135">For more information, see [Developing a Composite Windows Forms Control](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span></span>  
  
 <span data-ttu-id="3d843-136">**Zalecenia**</span><span class="sxs-lookup"><span data-stu-id="3d843-136">**Recommendation**</span></span>  
  
 <span data-ttu-id="3d843-137">Dziedzicz <xref:System.Windows.Forms.UserControl> klasy, jeśli:</span><span class="sxs-lookup"><span data-stu-id="3d843-137">Inherit from the <xref:System.Windows.Forms.UserControl> class if:</span></span>  
  
-   <span data-ttu-id="3d843-138">Chcesz połączyć funkcji kilku formantów formularzy systemu Windows w pojedynczą jednostkę wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="3d843-138">You want to combine the functionality of several Windows Forms controls into a single reusable unit.</span></span>  
  
### <a name="extended-controls"></a><span data-ttu-id="3d843-139">Formanty rozszerzone</span><span class="sxs-lookup"><span data-stu-id="3d843-139">Extended Controls</span></span>  
 <span data-ttu-id="3d843-140">Formant dziedziczony może pochodzić od dowolnego istniejącego formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-140">You can derive an inherited control from any existing Windows Forms control.</span></span> <span data-ttu-id="3d843-141">Z tej metody można zachować wszystkie funkcje związane z formantu formularzy systemu Windows, a następnie rozszerzają te funkcje, dodając niestandardowe właściwości, metody lub innych funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d843-141">With this approach, you can retain all of the inherent functionality of a Windows Forms control, and then extend that functionality by adding custom properties, methods, or other features.</span></span> <span data-ttu-id="3d843-142">Po wybraniu tej opcji można zastąpić logiki malowanie kontrolki podstawowej i następnie rozszerzają jego interfejs użytkownika przez zmianę jego wyglądu.</span><span class="sxs-lookup"><span data-stu-id="3d843-142">With this option, you can override the base control's paint logic, and then extend its user interface by changing its appearance.</span></span>  
  
 <span data-ttu-id="3d843-143">Na przykład można utworzyć formantu pochodną <xref:System.Windows.Forms.Button> formant, który śledzi, ile razy użytkownik kliknął przycisk go.</span><span class="sxs-lookup"><span data-stu-id="3d843-143">For example, you can create a control derived from the <xref:System.Windows.Forms.Button> control that tracks how many times a user has clicked it.</span></span>  
  
 <span data-ttu-id="3d843-144">W niektórych formantów można również dodać niestandardowe wygląd graficznego interfejsu użytkownika formantu przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="3d843-144">In some controls, you can also add a custom appearance to the graphical user interface of your control by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span> <span data-ttu-id="3d843-145">Dla przycisku rozszerzonej śledzący kliknięć, można zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metodę do wywołania Podstawowa implementacja <xref:System.Windows.Forms.Control.OnPaint%2A>, a następnie narysuj liczba kliknij w jednym narożniku <xref:System.Windows.Forms.Button> obszaru klienckiego formantu.</span><span class="sxs-lookup"><span data-stu-id="3d843-145">For an extended button that tracks clicks, you can override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to call the base implementation of <xref:System.Windows.Forms.Control.OnPaint%2A>, and then draw the click count in one corner of the <xref:System.Windows.Forms.Button> control's client area.</span></span>  
  
 <span data-ttu-id="3d843-146">**Zalecenia**</span><span class="sxs-lookup"><span data-stu-id="3d843-146">**Recommendation**</span></span>  
  
 <span data-ttu-id="3d843-147">Dziedziczenie z formantu formularzy systemu Windows, jeśli:</span><span class="sxs-lookup"><span data-stu-id="3d843-147">Inherit from a Windows Forms control if:</span></span>  
  
-   <span data-ttu-id="3d843-148">Większość funkcji, które są potrzebne już jest identyczny z istniejącego formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-148">Most of the functionality you need is already identical to an existing Windows Forms control.</span></span>  
  
-   <span data-ttu-id="3d843-149">Nie trzeba niestandardowego graficznego interfejsu użytkownika lub projektowania nowego graficznego interfejsu użytkownika dla istniejącego formantu.</span><span class="sxs-lookup"><span data-stu-id="3d843-149">You do not need a custom graphical user interface, or you want to design a new graphical user interface for an existing control.</span></span>  
  
### <a name="custom-controls"></a><span data-ttu-id="3d843-150">Formanty niestandardowe</span><span class="sxs-lookup"><span data-stu-id="3d843-150">Custom Controls</span></span>  
 <span data-ttu-id="3d843-151">Innym sposobem tworzenia formantu jest utworzenie jednego z początku przez dziedziczenie z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="3d843-151">Another way to create a control is to create one substantially from the beginning by inheriting from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="3d843-152"><xref:System.Windows.Forms.Control> Klasa udostępnia wszystkie podstawowe funkcje wymagane przez funkcje kontroli, łącznie z myszy i klawiatury obsługi zdarzeń, ale nie funkcje sterowania lub interfejsu graficznego.</span><span class="sxs-lookup"><span data-stu-id="3d843-152">The <xref:System.Windows.Forms.Control> class provides all of the basic functionality required by controls, including mouse and keyboard handling events, but no control-specific functionality or graphical interface.</span></span>  
  
 <span data-ttu-id="3d843-153">Tworzenie formantu przez dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga dużo więcej myśl i nakładu pracy niż dziedziczenie z <xref:System.Windows.Forms.UserControl> lub formant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-153">Creating a control by inheriting from the <xref:System.Windows.Forms.Control> class requires much more thought and effort than inheriting from <xref:System.Windows.Forms.UserControl> or an existing Windows Forms control.</span></span> <span data-ttu-id="3d843-154">Ponieważ wiele implementacji pozostanie dla Ciebie, formantu może mieć większą elastyczność niż formantu złożonego lub rozszerzone i można dostosować zgodnie z potrzebami dokładną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="3d843-154">Because a great deal of implementation is left for you, your control can have greater flexibility than a composite or extended control, and you can tailor your control to suit your exact needs.</span></span>  
  
 <span data-ttu-id="3d843-155">Aby zaimplementować kontrolkę niestandardową, należy napisać kod <xref:System.Windows.Forms.Control.OnPaint%2A> zdarzeń formantu, jak również żadnego kodu właściwych dla funkcji należy.</span><span class="sxs-lookup"><span data-stu-id="3d843-155">To implement a custom control, you must write code for the <xref:System.Windows.Forms.Control.OnPaint%2A> event of the control, as well as any feature-specific code you need.</span></span> <span data-ttu-id="3d843-156">Możesz też przesłonić <xref:System.Windows.Forms.Control.WndProc%2A> metody i obsługi komunikatów systemu windows bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="3d843-156">You can also override the <xref:System.Windows.Forms.Control.WndProc%2A> method and handle windows messages directly.</span></span> <span data-ttu-id="3d843-157">Jest to najbardziej wydajny sposób można utworzyć formantu, ale aby skutecznie użyć tej metody, należy zapoznać się z interfejsu API Microsoft Win32®.</span><span class="sxs-lookup"><span data-stu-id="3d843-157">This is the most powerful way to create a control, but to use this technique effectively, you need to be familiar with the Microsoft Win32® API.</span></span>  
  
 <span data-ttu-id="3d843-158">Przykładem formant niestandardowy jest formant zegara, który stanowi duplikat wygląd i zachowanie zegar analogowy.</span><span class="sxs-lookup"><span data-stu-id="3d843-158">An example of a custom control is a clock control that duplicates the appearance and behavior of an analog clock.</span></span> <span data-ttu-id="3d843-159">Niestandardowe rysowania jest wywoływane w celu spowodować ręce zegara, aby przenieść w odpowiedzi na <xref:System.Windows.Forms.Timer.Tick> zdarzenia z wewnętrznego <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="3d843-159">Custom painting is invoked to cause the hands of the clock to move in response to <xref:System.Windows.Forms.Timer.Tick> events from an internal <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="3d843-160">Aby uzyskać więcej informacji, zobacz [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d843-160">For more information, see [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span></span>  
  
 <span data-ttu-id="3d843-161">**Zalecenia**</span><span class="sxs-lookup"><span data-stu-id="3d843-161">**Recommendation**</span></span>  
  
 <span data-ttu-id="3d843-162">Dziedzicz <xref:System.Windows.Forms.Control> klasy, jeśli:</span><span class="sxs-lookup"><span data-stu-id="3d843-162">Inherit from the <xref:System.Windows.Forms.Control> class if:</span></span>  
  
-   <span data-ttu-id="3d843-163">Chcesz podać niestandardowy graficzną reprezentację formantu.</span><span class="sxs-lookup"><span data-stu-id="3d843-163">You want to provide a custom graphical representation of your control.</span></span>  
  
-   <span data-ttu-id="3d843-164">Należy wdrożyć funkcji niestandardowych, który nie jest dostępny za pośrednictwem standardowych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="3d843-164">You need to implement custom functionality that is not available through standard controls.</span></span>  
  
### <a name="activex-controls"></a><span data-ttu-id="3d843-165">Kontrolki ActiveX</span><span class="sxs-lookup"><span data-stu-id="3d843-165">ActiveX Controls</span></span>  
 <span data-ttu-id="3d843-166">Mimo że infrastruktury formularzy systemu Windows została zoptymalizowana do hosta formanty formularzy systemu Windows, można nadal używać formantów ActiveX.</span><span class="sxs-lookup"><span data-stu-id="3d843-166">Although the Windows Forms infrastructure has been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="3d843-167">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d843-167">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="3d843-168">Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów ActiveX do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3d843-168">For more information, see [How to: Add ActiveX Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).</span></span>  
  
### <a name="windowless-controls"></a><span data-ttu-id="3d843-169">Formanty bez okien</span><span class="sxs-lookup"><span data-stu-id="3d843-169">Windowless Controls</span></span>  
 <span data-ttu-id="3d843-170">Obsługa technologii ActiveX the Microsoft Visual Basic® 6.0and *bez okien* kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3d843-170">The Microsoft Visual Basic® 6.0and ActiveX technologies support *windowless* controls.</span></span> <span data-ttu-id="3d843-171">Formanty niepowiązane z oknami nie są obsługiwane w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3d843-171">Windowless controls are not supported in Windows Forms.</span></span>  
  
## <a name="custom-design-experience"></a><span data-ttu-id="3d843-172">Środowisko projektowania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="3d843-172">Custom Design Experience</span></span>  
 <span data-ttu-id="3d843-173">Jeśli musisz wdrożyć niestandardowe środowisko czasu projektowania, można tworzyć własne projektanta.</span><span class="sxs-lookup"><span data-stu-id="3d843-173">If you need to implement a custom design-time experience, you can author your own designer.</span></span> <span data-ttu-id="3d843-174">W przypadku złożonych kontrolek pochodzi z niestandardowej klasy projektanta <xref:System.Windows.Forms.Design.ParentControlDesigner> lub <xref:System.Windows.Forms.Design.DocumentDesigner> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d843-174">For composite controls, derive your custom designer class from the <xref:System.Windows.Forms.Design.ParentControlDesigner> or the <xref:System.Windows.Forms.Design.DocumentDesigner> classes.</span></span> <span data-ttu-id="3d843-175">Rozszerzone i niestandardowych formantów, pochodzi z niestandardowej klasy projektanta <xref:System.Windows.Forms.Design.ControlDesigner> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d843-175">For extended and custom controls, derive your custom designer class from the <xref:System.Windows.Forms.Design.ControlDesigner> class.</span></span>  
  
 <span data-ttu-id="3d843-176">Użyj <xref:System.ComponentModel.DesignerAttribute> do skojarzenia z z projektantem formantu.</span><span class="sxs-lookup"><span data-stu-id="3d843-176">Use the <xref:System.ComponentModel.DesignerAttribute> to associate your control with your designer.</span></span> <span data-ttu-id="3d843-177">Aby uzyskać więcej informacji, zobacz [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) i [porady: Tworzenie funkcji systemu Windows formularze kontroli czy ma korzystać z czasu projektowania](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).</span><span class="sxs-lookup"><span data-stu-id="3d843-177">For more information, see [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) and [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d843-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d843-178">See Also</span></span>  
 [<span data-ttu-id="3d843-179">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3d843-179">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="3d843-180">Porady: Tworzenie formantu formularzy systemu Windows proste</span><span class="sxs-lookup"><span data-stu-id="3d843-180">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="3d843-181">Tworzenie formantu formularzy systemu Windows złożone</span><span class="sxs-lookup"><span data-stu-id="3d843-181">Developing a Composite Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [<span data-ttu-id="3d843-182">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="3d843-182">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="3d843-183">Porady: Tworzenie formantu formularzy systemu Windows wykorzystującego funkcje czasu projektowania</span><span class="sxs-lookup"><span data-stu-id="3d843-183">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)