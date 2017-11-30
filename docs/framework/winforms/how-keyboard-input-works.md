---
title: "Działanie wprowadzania z klawiatury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f45d01da6f9a851a0e51f9d614e84a3fba91e4d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-keyboard-input-works"></a><span data-ttu-id="350f2-102">Działanie wprowadzania z klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-102">How Keyboard Input Works</span></span>
<span data-ttu-id="350f2-103">Formularze systemu Windows przetwarza wprowadzanie z klawiatury przez wywoływanie zdarzeń klawiatury w odpowiedzi na komunikaty systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="350f2-103">Windows Forms processes keyboard input by raising keyboard events in response to Windows messages.</span></span> <span data-ttu-id="350f2-104">Większość aplikacji Windows Forms przetworzyć klawiatury wyłącznie przez obsługi zdarzenia klawiatury.</span><span class="sxs-lookup"><span data-stu-id="350f2-104">Most Windows Forms applications process keyboard input exclusively by handling the keyboard events.</span></span> <span data-ttu-id="350f2-105">Jednak należy zrozumieć, jak komunikaty klawiatury działają, można wdrożyć bardziej zaawansowanych scenariuszy wejście klawiatury, takie jak przechwytywaniu kluczy przed dotarciem formantu.</span><span class="sxs-lookup"><span data-stu-id="350f2-105">However, you need to understand how keyboard messages work so you can implement more advanced keyboard-input scenarios, such as intercepting keys before they reach a control.</span></span> <span data-ttu-id="350f2-106">W tym temacie opisano typy danych klucza, że program Windows Forms rozpoznaje i omówiono sposób kierowania komunikaty klawiatury.</span><span class="sxs-lookup"><span data-stu-id="350f2-106">This topic describes the types of key data that Windows Forms recognizes and provides an overview of how keyboard messages are routed.</span></span> <span data-ttu-id="350f2-107">Aby uzyskać informacje o zdarzeniach klawiatury, zobacz [zdarzenia klawiatury przy użyciu](../../../docs/framework/winforms/using-keyboard-events.md).</span><span class="sxs-lookup"><span data-stu-id="350f2-107">For information about keyboard events, see [Using Keyboard Events](../../../docs/framework/winforms/using-keyboard-events.md).</span></span>  
  
## <a name="types-of-keys"></a><span data-ttu-id="350f2-108">Typy kluczy</span><span class="sxs-lookup"><span data-stu-id="350f2-108">Types of Keys</span></span>  
 <span data-ttu-id="350f2-109">Formularze systemu Windows identyfikuje klawiatury jako klucz wirtualny kody, które są reprezentowane przez operatora testu koniunkcji <xref:System.Windows.Forms.Keys> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="350f2-109">Windows Forms identifies keyboard input as virtual-key codes that are represented by the bitwise <xref:System.Windows.Forms.Keys> enumeration.</span></span> <span data-ttu-id="350f2-110">Z <xref:System.Windows.Forms.Keys> wyliczenia, można połączyć serii naciśniętego kluczy w pojedynczej wartości.</span><span class="sxs-lookup"><span data-stu-id="350f2-110">With the <xref:System.Windows.Forms.Keys> enumeration, you can combine a series of pressed keys to result in a single value.</span></span> <span data-ttu-id="350f2-111">Te wartości odpowiada wartości dołączone do wiadomości WM_KEYDOWN i WM_SYSKEYDOWN systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="350f2-111">These values correspond to the values that accompany the WM_KEYDOWN and WM_SYSKEYDOWN Windows messages.</span></span> <span data-ttu-id="350f2-112">Obsługa, można wykrywać większości fizycznych naciśnięć klawiszy <xref:System.Windows.Forms.Control.KeyDown> lub <xref:System.Windows.Forms.Control.KeyUp> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="350f2-112">You can detect most physical key presses by handling the <xref:System.Windows.Forms.Control.KeyDown> or <xref:System.Windows.Forms.Control.KeyUp> events.</span></span> <span data-ttu-id="350f2-113">Klawisze są podzbiorem <xref:System.Windows.Forms.Keys> wyliczenie i odpowiadają wartościom dołączone do wiadomości WM_CHAR i WM_SYSCHAR systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="350f2-113">Character keys are a subset of the <xref:System.Windows.Forms.Keys> enumeration and correspond to the values that accompany the WM_CHAR and WM_SYSCHAR Windows messages.</span></span> <span data-ttu-id="350f2-114">Kombinacja klawiszy naciśniętego powoduje znak, można wykryć znak Obsługa <xref:System.Windows.Forms.Control.KeyPress> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="350f2-114">If the combination of pressed keys results in a character, you can detect the character by handling the <xref:System.Windows.Forms.Control.KeyPress> event.</span></span> <span data-ttu-id="350f2-115">Alternatywnie można użyć <xref:Microsoft.VisualBasic.Devices.Keyboard>, uwidocznione przez interfejs programowania Visual Basic, do odnajdywania, zostały naciśnięte klawisze i wysyłania kluczy.</span><span class="sxs-lookup"><span data-stu-id="350f2-115">Alternatively, you can use <xref:Microsoft.VisualBasic.Devices.Keyboard>, exposed by Visual Basic programming interface, to discover which keys were pressed and send keys.</span></span> <span data-ttu-id="350f2-116">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do klawiatury](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).</span><span class="sxs-lookup"><span data-stu-id="350f2-116">For more information, see [Accessing the Keyboard](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).</span></span>  
  
## <a name="order-of-keyboard-events"></a><span data-ttu-id="350f2-117">Kolejność zdarzeń klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-117">Order of Keyboard Events</span></span>  
 <span data-ttu-id="350f2-118">Jak wymienionymi wcześniej, istnieją 3 klawiatury zdarzenia powiązane, które mogą wystąpić w formancie.</span><span class="sxs-lookup"><span data-stu-id="350f2-118">As listed previously, there are 3 keyboard related events that can occur on a control.</span></span> <span data-ttu-id="350f2-119">Poniższa sekwencja zawiera kolejność zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="350f2-119">The following sequence shows the general order of the events:</span></span>  
  
1.  <span data-ttu-id="350f2-120">Użytkownik wypchnięcia "" klucza, klucz jest wstępnie przetworzony, wysyłane, a <xref:System.Windows.Forms.Control.KeyDown> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="350f2-120">The user pushes the "a" key, the key is preprocessed, dispatched, and a <xref:System.Windows.Forms.Control.KeyDown> event occurs.</span></span>  
  
2.  <span data-ttu-id="350f2-121">Użytkownik ma klucz "", klucz jest wstępnie przetworzony, wysyłane, a <xref:System.Windows.Forms.Control.KeyPress> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="350f2-121">The user holds the "a" key, the key is preprocessed, dispatched, and a <xref:System.Windows.Forms.Control.KeyPress> event occurs.</span></span>  
  
     <span data-ttu-id="350f2-122">To zdarzenie występuje wiele razy, użytkownik posiada klucza.</span><span class="sxs-lookup"><span data-stu-id="350f2-122">This event occurs multiple times as the user holds a key.</span></span>  
  
3.  <span data-ttu-id="350f2-123">Wersje użytkownika "" klucz jest wstępnie przetworzony, wysyłane i <xref:System.Windows.Forms.Control.KeyUp> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="350f2-123">The user releases the "a" key, the key is preprocessed, dispatched and a <xref:System.Windows.Forms.Control.KeyUp> event occurs.</span></span>  
  
## <a name="preprocessing-keys"></a><span data-ttu-id="350f2-124">Przetwarzanie wstępne kluczy</span><span class="sxs-lookup"><span data-stu-id="350f2-124">Preprocessing Keys</span></span>  
 <span data-ttu-id="350f2-125">Podobnie jak inne komunikaty, komunikaty klawiatury są przetwarzane w <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="350f2-125">Like other messages, keyboard messages are processed in the <xref:System.Windows.Forms.Control.WndProc%2A> method of a form or control.</span></span> <span data-ttu-id="350f2-126">Jednak przed klawiatury wiadomości są przetwarzane, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metoda wywołuje jedną lub kilka metod, które może zostać zastąpiona w celu obsługi znaków specjalnych klucze i klucze fizycznych.</span><span class="sxs-lookup"><span data-stu-id="350f2-126">However, before keyboard messages are processed, the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method calls one or more methods that can be overridden to handle special character keys and physical keys.</span></span> <span data-ttu-id="350f2-127">Można zastąpić te metody wykrywania i filtrowania określonych kluczy przed komunikaty są przetwarzane przez formant.</span><span class="sxs-lookup"><span data-stu-id="350f2-127">You can override these methods to detect and filter certain keys before the messages are processed by the control.</span></span> <span data-ttu-id="350f2-128">W poniższej tabeli przedstawiono akcję, która jest wykonywana i powiązanej metody, która występuje, w kolejności, że metoda występuje.</span><span class="sxs-lookup"><span data-stu-id="350f2-128">The following table shows the action that is being performed and the related method that occurs, in the order that the method occurs.</span></span>  
  
### <a name="preprocessing-for-a-keydown-event"></a><span data-ttu-id="350f2-129">Przetwarzanie wstępne zdarzenia KeyDown</span><span class="sxs-lookup"><span data-stu-id="350f2-129">Preprocessing for a KeyDown event</span></span>  
  
|<span data-ttu-id="350f2-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="350f2-130">Action</span></span>|<span data-ttu-id="350f2-131">Pokrewne — metoda</span><span class="sxs-lookup"><span data-stu-id="350f2-131">Related method</span></span>|<span data-ttu-id="350f2-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="350f2-132">Notes</span></span>|  
|------------|--------------------|-----------|  
|<span data-ttu-id="350f2-133">Sprawdź, czy klucz polecenia, takich jak akceleratora lub menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="350f2-133">Check for a command key such as an accelerator or menu shortcut.</span></span>|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|<span data-ttu-id="350f2-134">Ta metoda przetwarza klucz polecenia, który ma pierwszeństwo przed regularne kluczy.</span><span class="sxs-lookup"><span data-stu-id="350f2-134">This method processes a command key, which takes precedence over regular keys.</span></span> <span data-ttu-id="350f2-135">Jeśli ta metoda zwraca `true`, nie jest wysyłany komunikat klucza i klucza zdarzenie nie występuje.</span><span class="sxs-lookup"><span data-stu-id="350f2-135">If this method returns `true`, the key message is not dispatched and a key event does not occur.</span></span> <span data-ttu-id="350f2-136">Jeśli zmienna zwraca `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> nosi nazwę`.`</span><span class="sxs-lookup"><span data-stu-id="350f2-136">If it returns `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> is called`.`</span></span>|  
|<span data-ttu-id="350f2-137">Sprawdź, czy specjalny klucz, który wymaga przetwarzania wstępnego lub należy wywołać klucz normalne znaki <xref:System.Windows.Forms.Control.KeyDown> zdarzeń i być wysyłane do formantu.</span><span class="sxs-lookup"><span data-stu-id="350f2-137">Check for a special key that requires preprocessing or a normal character key that should raise a <xref:System.Windows.Forms.Control.KeyDown> event and be dispatched to a control.</span></span>|<xref:System.Windows.Forms.Control.IsInputKey%2A>|<span data-ttu-id="350f2-138">Jeśli metoda zwraca `true`, oznacza to zwykły znak jest formantu i <xref:System.Windows.Forms.Control.KeyDown> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="350f2-138">If the method returns `true`, it means the control is a regular character and a <xref:System.Windows.Forms.Control.KeyDown> event is raised.</span></span> <span data-ttu-id="350f2-139">Jeśli `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="350f2-139">If `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> is called.</span></span> <span data-ttu-id="350f2-140">**Uwaga:** w celu zapewnienia formantu pobiera klucz lub kombinację klawiszy, może obsługiwać <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i zestaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` dla klucza lub kluczy ma.</span><span class="sxs-lookup"><span data-stu-id="350f2-140">**Note:**  To ensure a control gets a key or combination of keys, you can handle the <xref:System.Windows.Forms.Control.PreviewKeyDown> event and set <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> of the <xref:System.Windows.Forms.PreviewKeyDownEventArgs> to `true` for the key or keys you want.</span></span>|  
|<span data-ttu-id="350f2-141">Sprawdź, czy klucz nawigacji (ESC, karta, Return lub klawiszy strzałek).</span><span class="sxs-lookup"><span data-stu-id="350f2-141">Check for a navigation key (ESC, TAB, Return, or arrow keys).</span></span>|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|<span data-ttu-id="350f2-142">Ta metoda przetwarza fizycznych klucz, który wykorzystuje funkcje specjalne w formancie, takie jak przełączanie fokus między formantem a jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="350f2-142">This method processes a physical key that employs special functionality within the control, such as switching focus between the control and its parent.</span></span> <span data-ttu-id="350f2-143">Jeśli bezpośredniej kontroli nie obsługuje klucza, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> jest wywoływana w kontrolce nadrzędnej i tak dalej do formantu najwyższego poziomu w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="350f2-143">If the immediate control does not handle the key, the <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> is called on the parent control and so on to the topmost control in the hierarchy.</span></span> <span data-ttu-id="350f2-144">Jeśli ta metoda zwraca `true`, przetwarzania wstępnego została zakończona i nie jest generowane zdarzenie klucza.</span><span class="sxs-lookup"><span data-stu-id="350f2-144">If this method returns `true`, preprocessing is complete and a key event is not generated.</span></span> <span data-ttu-id="350f2-145">Jeśli zmienna zwraca `false`, <xref:System.Windows.Forms.Control.KeyDown> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="350f2-145">If it returns `false`, a <xref:System.Windows.Forms.Control.KeyDown> event occurs.</span></span>|  
  
### <a name="preprocessing-for-a-keypress-event"></a><span data-ttu-id="350f2-146">Przetwarzanie wstępne zdarzenia KeyPress</span><span class="sxs-lookup"><span data-stu-id="350f2-146">Preprocessing for a KeyPress Event</span></span>  
  
|<span data-ttu-id="350f2-147">Akcja</span><span class="sxs-lookup"><span data-stu-id="350f2-147">Action</span></span>|<span data-ttu-id="350f2-148">Pokrewne — metoda</span><span class="sxs-lookup"><span data-stu-id="350f2-148">Related method</span></span>|<span data-ttu-id="350f2-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="350f2-149">Notes</span></span>|  
|------------|--------------------|-----------|  
|<span data-ttu-id="350f2-150">Sprawdź, czy klucz jest normalne znaki, który ma zostać przetworzony przez formant</span><span class="sxs-lookup"><span data-stu-id="350f2-150">Check to see the key is a normal character that should be processed by the control</span></span>|<xref:System.Windows.Forms.Control.IsInputChar%2A>|<span data-ttu-id="350f2-151">Jeśli znak jest normalne znaki, ta metoda zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> zdarzenia i dalsze przetwarzanie wstępne występuje.</span><span class="sxs-lookup"><span data-stu-id="350f2-151">If the character is a normal character, this method returns `true`, the <xref:System.Windows.Forms.Control.KeyPress> event is raised and no further preprocessing occurs.</span></span> <span data-ttu-id="350f2-152">W przeciwnym razie <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="350f2-152">Otherwise <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> will be called.</span></span>|  
|<span data-ttu-id="350f2-153">Sprawdź, czy znak jest wartość (takich jak & OK na przycisku)</span><span class="sxs-lookup"><span data-stu-id="350f2-153">Check to see if the character is a mnemonic (such as &OK on a button)</span></span>|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|<span data-ttu-id="350f2-154">Ta metoda jest podobna do <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, zostanie wywołana w górę hierarchii formantu.</span><span class="sxs-lookup"><span data-stu-id="350f2-154">This method, similar to <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, will be called up the control hierarchy.</span></span> <span data-ttu-id="350f2-155">Jeśli formant jest kontenerem, sprawdza klawiszy skrótu wywołując <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> na siebie i jej kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="350f2-155">If the control is a container control, it checks for mnemonics by calling <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> on itself and its child controls.</span></span> <span data-ttu-id="350f2-156">Jeśli <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> zwraca `true`, <xref:System.Windows.Forms.Control.KeyPress> zdarzenie nie występuje.</span><span class="sxs-lookup"><span data-stu-id="350f2-156">If <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> returns `true`, a <xref:System.Windows.Forms.Control.KeyPress> event does not occur.</span></span>|  
  
## <a name="processing-keyboard-messages"></a><span data-ttu-id="350f2-157">Przetwarzanie komunikatów klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-157">Processing Keyboard Messages</span></span>  
 <span data-ttu-id="350f2-158">Po reach komunikaty klawiatury <xref:System.Windows.Forms.Control.WndProc%2A> metody formularza lub kontrolki, są przetwarzane przez zestaw metod, które mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="350f2-158">After keyboard messages reach the <xref:System.Windows.Forms.Control.WndProc%2A> method of a form or control, they are processed by a set of methods that can be overridden.</span></span> <span data-ttu-id="350f2-159">Każda z tych metod zwraca <xref:System.Boolean> wartość określającą, czy komunikat klawiatury zostały przetworzone i używane przez formant.</span><span class="sxs-lookup"><span data-stu-id="350f2-159">Each of these methods returns a <xref:System.Boolean> value specifying whether the keyboard message has been processed and consumed by the control.</span></span> <span data-ttu-id="350f2-160">Jeśli zwraca jedną z metod `true`, następnie wiadomość jest uznawany za obsługiwany, i nie zostanie przekazany do podstawowej formantu lub jego element nadrzędny dla dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="350f2-160">If one of the methods returns `true`, then the message is considered handled, and it is not passed to the control's base or parent for further processing.</span></span> <span data-ttu-id="350f2-161">W przeciwnym razie wiadomość pozostaje w kolejce wiadomości i mogą być przetwarzane w innej metody w podstawowej lub nadrzędnej formantu.</span><span class="sxs-lookup"><span data-stu-id="350f2-161">Otherwise, the message stays in the message queue and may be processed in another method in the control's base or parent.</span></span> <span data-ttu-id="350f2-162">W poniższej tabeli przedstawiono metody, które przetwarzają komunikaty klawiatury.</span><span class="sxs-lookup"><span data-stu-id="350f2-162">The following table presents the methods that process keyboard messages.</span></span>  
  
|<span data-ttu-id="350f2-163">Metoda</span><span class="sxs-lookup"><span data-stu-id="350f2-163">Method</span></span>|<span data-ttu-id="350f2-164">Uwagi</span><span class="sxs-lookup"><span data-stu-id="350f2-164">Notes</span></span>|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|<span data-ttu-id="350f2-165">Ta metoda przetwarza wszystkie komunikaty klawiatury, które są odbierane przez <xref:System.Windows.Forms.Control.WndProc%2A> metody formantu.</span><span class="sxs-lookup"><span data-stu-id="350f2-165">This method processes all keyboard messages that are received by the <xref:System.Windows.Forms.Control.WndProc%2A> method of the control.</span></span>|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|<span data-ttu-id="350f2-166">Ta metoda wysyła wiadomość klawiatury do kontrolki nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="350f2-166">This method sends the keyboard message to the control's parent.</span></span> <span data-ttu-id="350f2-167">Jeśli <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> zwraca `true`, nie klucza zostanie wygenerowane zdarzenie, w przeciwnym razie <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="350f2-167">If <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> returns `true`, no key event is generated, otherwise <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> is called.</span></span>|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|<span data-ttu-id="350f2-168">Ta metoda zgłasza <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="350f2-168">This method raises the <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp> events, as appropriate.</span></span>|  
  
## <a name="overriding-keyboard-methods"></a><span data-ttu-id="350f2-169">Zastępowanie metody klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-169">Overriding Keyboard Methods</span></span>  
 <span data-ttu-id="350f2-170">Istnieje wiele metod zastępowanie, gdy wiadomość klawiatury jest wstępnie przetworzony i przetwarzania; Jednak niektóre metody są znacznie lepszą opcji od innych.</span><span class="sxs-lookup"><span data-stu-id="350f2-170">There are many methods available for overriding when a keyboard message is preprocessed and processed; however, some methods are much better choices than others.</span></span> <span data-ttu-id="350f2-171">Poniższa tabela zawiera zadania, które można wykonywać i najlepszy sposób, aby zastąpić metody klawiatury.</span><span class="sxs-lookup"><span data-stu-id="350f2-171">Following table shows tasks you might want to accomplish and the best way to override the keyboard methods.</span></span> <span data-ttu-id="350f2-172">Aby uzyskać więcej informacji na zastępowanie metod, zobacz [zastępowanie właściwości i metod w klasach pochodnych](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).</span><span class="sxs-lookup"><span data-stu-id="350f2-172">For more information on overriding methods, see [Overriding properties and methods in derived classes](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).</span></span>  
  
|<span data-ttu-id="350f2-173">Zadanie</span><span class="sxs-lookup"><span data-stu-id="350f2-173">Task</span></span>|<span data-ttu-id="350f2-174">Metoda</span><span class="sxs-lookup"><span data-stu-id="350f2-174">Method</span></span>|  
|----------|------------|  
|<span data-ttu-id="350f2-175">Przechwytywać klucza nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyDown> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="350f2-175">Intercept a navigation key and raise a <xref:System.Windows.Forms.Control.KeyDown> event.</span></span> <span data-ttu-id="350f2-176">Na przykład chcesz kartę i wrócić do obsługi w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="350f2-176">For example you want TAB and Return to be handled in a text box.</span></span>|<span data-ttu-id="350f2-177">Zastąpienie <xref:System.Windows.Forms.Control.IsInputKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="350f2-177">Override <xref:System.Windows.Forms.Control.IsInputKey%2A>.</span></span> <span data-ttu-id="350f2-178">**Uwaga:** Alternatywnie można obsługiwać <xref:System.Windows.Forms.Control.PreviewKeyDown> zdarzeń i zestaw <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> z <xref:System.Windows.Forms.PreviewKeyDownEventArgs> do `true` dla klucza lub kluczy ma.</span><span class="sxs-lookup"><span data-stu-id="350f2-178">**Note:**  Alternatively, you can handle the <xref:System.Windows.Forms.Control.PreviewKeyDown> event and set <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> of the <xref:System.Windows.Forms.PreviewKeyDownEventArgs> to `true` for the key or keys you want.</span></span>|  
|<span data-ttu-id="350f2-179">Wykonaj specjalne obsługi danych wejściowych lub nawigacji w formancie.</span><span class="sxs-lookup"><span data-stu-id="350f2-179">Perform special input or navigation handling on a control.</span></span> <span data-ttu-id="350f2-180">Na przykład chcesz użycie klawiszy strzałek w formancie z listy, aby zmienić wybrany element.</span><span class="sxs-lookup"><span data-stu-id="350f2-180">For example, you want the use of arrow keys in your list control to change the selected item.</span></span>|<span data-ttu-id="350f2-181">Zastąpienie<xref:System.Windows.Forms.Control.ProcessDialogKey%2A></span><span class="sxs-lookup"><span data-stu-id="350f2-181">Override <xref:System.Windows.Forms.Control.ProcessDialogKey%2A></span></span>|  
|<span data-ttu-id="350f2-182">Przechwytywać klucza nawigacji i podnieść <xref:System.Windows.Forms.Control.KeyPress> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="350f2-182">Intercept a navigation key and raise a <xref:System.Windows.Forms.Control.KeyPress> event.</span></span> <span data-ttu-id="350f2-183">Na przykład w formancie pole pokrętła ma się, że wiele Strzałka musi nacisnąć, aby przyspieszyć przez kolejne elementy.</span><span class="sxs-lookup"><span data-stu-id="350f2-183">For example in a spin-box control you want multiple arrow key presses to accelerate progression through the items.</span></span>|<span data-ttu-id="350f2-184">Zastąpienie <xref:System.Windows.Forms.Control.IsInputChar%2A>.</span><span class="sxs-lookup"><span data-stu-id="350f2-184">Override <xref:System.Windows.Forms.Control.IsInputChar%2A>.</span></span>|  
|<span data-ttu-id="350f2-185">Specjalne obsługi danych wejściowych lub nawigacji podczas wykonywania <xref:System.Windows.Forms.Control.KeyPress> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="350f2-185">Perform special input or navigation handling during a <xref:System.Windows.Forms.Control.KeyPress> event.</span></span> <span data-ttu-id="350f2-186">Na przykład na liście kontroli, przytrzymując klawisz "r" pomija między elementami, które zaczynają się od litery r.</span><span class="sxs-lookup"><span data-stu-id="350f2-186">For example, in a list control holding down the "r" key skips between items that begin with the letter r.</span></span>|<span data-ttu-id="350f2-187">Zastąpienie<xref:System.Windows.Forms.Control.ProcessDialogChar%2A></span><span class="sxs-lookup"><span data-stu-id="350f2-187">Override <xref:System.Windows.Forms.Control.ProcessDialogChar%2A></span></span>|  
|<span data-ttu-id="350f2-188">Wykonaj niestandardowy skrót klawiszowy Obsługa; na przykład chcesz obsługiwać symboli na przyciskach rysowanych przez właściciela zawarte w pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="350f2-188">Perform custom mnemonic handling; for example, you want to handle mnemonics on owner-drawn buttons contained in a toolbar.</span></span>|<span data-ttu-id="350f2-189">Zastąpienie <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.</span><span class="sxs-lookup"><span data-stu-id="350f2-189">Override <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="350f2-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="350f2-190">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [<span data-ttu-id="350f2-191">My.Computer.Keyboard — obiekt</span><span class="sxs-lookup"><span data-stu-id="350f2-191">My.Computer.Keyboard Object</span></span>](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [<span data-ttu-id="350f2-192">Uzyskiwanie dostępu do klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-192">Accessing the Keyboard</span></span>](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [<span data-ttu-id="350f2-193">Używanie zdarzeń klawiatury</span><span class="sxs-lookup"><span data-stu-id="350f2-193">Using Keyboard Events</span></span>](../../../docs/framework/winforms/using-keyboard-events.md)