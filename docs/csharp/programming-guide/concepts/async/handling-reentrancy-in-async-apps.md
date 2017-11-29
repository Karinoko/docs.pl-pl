---
title: "Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a917f88d3d6105f836dc67ef8a9ec92efc300d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="29855-102">Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="29855-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="29855-103">Po dołączeniu kodu asynchroniczne w aplikacji należy wziąć pod uwagę i prawdopodobnie zapobiec ponowne wejście, który odwołuje się do ponownego wprowadzania operację asynchroniczną, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="29855-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="29855-104">Jeśli nie identyfikowania i obsługi możliwości ponownego rozpoczęcia, może spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="29855-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="29855-105">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="29855-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="29855-106">Rozpoznawanie Wielobieżność</span><span class="sxs-lookup"><span data-stu-id="29855-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="29855-107">Obsługa ponownego rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="29855-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="29855-108">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="29855-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="29855-109">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="29855-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="29855-110">Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="29855-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="29855-111">Przeglądanie i uruchamianie przykładową aplikację</span><span class="sxs-lookup"><span data-stu-id="29855-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="29855-112">Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="29855-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="29855-113"><a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie Wielobieżność</span><span class="sxs-lookup"><span data-stu-id="29855-113"><a name="BKMK_RecognizingReentrancy"></a> Recognizing Reentrancy</span></span>  
 <span data-ttu-id="29855-114">W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchronicznego aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które zostaną pobrane.</span><span class="sxs-lookup"><span data-stu-id="29855-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="29855-115">Synchroniczną wersję przykładu będzie odpowiadać taki sam sposób niezależnie od ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątku interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się aplikacja działa.</span><span class="sxs-lookup"><span data-stu-id="29855-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="29855-116">W aplikacji asynchroniczne jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i może ponownie operację asynchroniczną, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="29855-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="29855-117">W poniższym przykładzie przedstawiono oczekiwanych danych wyjściowych, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="29855-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="29855-118">Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiar w bajtach, w każdej lokacji.</span><span class="sxs-lookup"><span data-stu-id="29855-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="29855-119">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="29855-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="29855-120">Jednak jeśli użytkownik wybierze przycisk więcej niż raz, program obsługi zdarzeń jest wywoływany wielokrotnie i proces pobierania jest ponownie wprowadzić hasło zawsze.</span><span class="sxs-lookup"><span data-stu-id="29855-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="29855-121">W związku z tym kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przeplata wyniki, a całkowita liczba bajtów jest myląca.</span><span class="sxs-lookup"><span data-stu-id="29855-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="29855-122">Możesz przejrzeć kod, który generuje dane wyjściowe w tym przewijając na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="29855-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="29855-123">Możesz eksperymentować z kodem pobrać rozwiązanie na komputerze lokalnym, a następnie uruchamiając projekt WebsiteDownload lub przy użyciu kodu na końcu tego tematu, aby utworzyć własny projekt, aby uzyskać więcej informacji oraz instrukcje, zobacz [ Przeglądanie i uruchamianie aplikacji przykład](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="29855-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <span data-ttu-id="29855-124"><a name="BKMK_HandlingReentrancy"></a>Obsługa ponownego rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="29855-124"><a name="BKMK_HandlingReentrancy"></a> Handling Reentrancy</span></span>  
 <span data-ttu-id="29855-125">Wielobieżność na różne sposoby, w zależności od tego, co ma aplikację w celu może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="29855-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="29855-126">W tym temacie przedstawiono następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="29855-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="29855-127">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="29855-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="29855-128">Wyłącz **Start** przycisk podczas operacji jest uruchomiona, dzięki czemu użytkownik nie może przerwać go.</span><span class="sxs-lookup"><span data-stu-id="29855-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="29855-129">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="29855-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="29855-130">Anuluj wszelkie operacje, który jest nadal uruchomiona, gdy użytkownik wybierze **Start** przycisk ponownie, a następnie kontynuuj let najbardziej ostatnio żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="29855-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="29855-131">Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="29855-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="29855-132">Zezwalaj na wszystkie żądane operacje wykonywane asynchronicznie, ale koordynuje wyświetlania danych wyjściowych, aby jednocześnie i w kolejności zostaną wyświetlone wyniki z każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="29855-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <span data-ttu-id="29855-133"><a name="BKMK_DisableTheStartButton"></a>Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="29855-133"><a name="BKMK_DisableTheStartButton"></a> Disable the Start Button</span></span>  
 <span data-ttu-id="29855-134">Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku w górnej części `StartButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29855-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="29855-135">Następnie można ponownie włączyć za pomocą przycisku `finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="29855-135">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="29855-136">Poniższy kod przedstawia te zmiany, które są oznaczone ikoną z gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="29855-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="29855-137">Zmiany można dodać do kodu na końcu tego tematu, lub możesz pobrać Zakończono aplikację z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="29855-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="29855-138">Nazwa projektu jest DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="29855-138">The project name is DisableStartButton.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 <span data-ttu-id="29855-139">W wyniku zmian, przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobierania witryny sieci Web, więc nie można ponownie wprowadzić hasło procesu.</span><span class="sxs-lookup"><span data-stu-id="29855-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <span data-ttu-id="29855-140"><a name="BKMK_CancelAndRestart"></a>Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="29855-140"><a name="BKMK_CancelAndRestart"></a> Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="29855-141">Zamiast wyłączenie **Start** przycisku, można zachować aktywnego przycisku, ale, jeśli użytkownik wybierze ponownie, ten przycisk Anuluj operację, która jest już uruchomiona i kontynuowania operacji najbardziej ostatnio uruchomiono.</span><span class="sxs-lookup"><span data-stu-id="29855-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="29855-142">Aby uzyskać więcej informacji na temat anulowania, zobacz [Fine-Tuning Twoja aplikacja Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="29855-142">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="29855-143">Aby skonfigurować ten scenariusz, wprowadź następujące zmiany do podstawowego kodu, który znajduje się w [przeglądanie i uruchamianie aplikacji przykład](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="29855-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="29855-144">Możesz również pobrać Zakończono aplikacji z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="29855-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="29855-145">Nazwa tego projektu jest CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="29855-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="29855-146">Deklarowanie <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="29855-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="29855-147">W `StartButton_Click`, określić, czy operacja jest już przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="29855-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="29855-148">Jeśli wartość `cts` jest wartość null, nie jest operacja już aktywne.</span><span class="sxs-lookup"><span data-stu-id="29855-148">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="29855-149">Jeśli wartość nie jest pusta, zostaną anulowane operacja, która jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="29855-149">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="29855-150">Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="29855-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="29855-151">Na koniec `StartButton_Click`, bieżący proces zostanie zakończony, a więc ustaw wartość `cts` do wartości null.</span><span class="sxs-lookup"><span data-stu-id="29855-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="29855-152">Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="29855-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="29855-153">Dodatki są oznaczone gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="29855-153">The additions are marked with asterisks.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 <span data-ttu-id="29855-154">W `AccessTheWebAsync`, wprowadź następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="29855-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="29855-155">Dodawanie parametru do akceptowania token anulowania z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="29855-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="29855-156">Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metodę, aby pobrać witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.</span><span class="sxs-lookup"><span data-stu-id="29855-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="29855-157">Przed wywołaniem `DisplayResults` do wyświetlenia wyników dla poszczególnych witryn pobrany, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="29855-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="29855-158">Poniższy kod przedstawia te zmiany, które są oznaczone ikoną z gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="29855-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 <span data-ttu-id="29855-159">Jeśli wybierzesz **Start** przycisk kilka razy uruchomiona ta aplikacja powinna generować wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="29855-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="29855-160">Aby wyeliminować częściowej listy, usuń znaczniki komentarza pierwszego wiersza kodu w `StartButton_Click` do wyczyść pola tekstowego użytkownik uruchamia ponownie wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="29855-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <span data-ttu-id="29855-161"><a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="29855-161"><a name="BKMK_RunMultipleOperations"></a> Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="29855-162">W tym przykładzie trzeci jest najbardziej skomplikowanych, że operacja asynchroniczna za każdym razem, użytkownik zdecyduje się na uruchomieniu aplikacji **Start** przycisk, a wszystkie operacje uruchomienia aż do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="29855-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="29855-163">Żądanych operacji pobierania witryny sieci Web z listy asynchronicznie, ale dane wyjściowe z działania są prezentowane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="29855-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="29855-164">Oznacza to, że przeplatana rzeczywistego działania pobierania jako danych wyjściowych w [rozpoznawanie Wielobieżność](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pokazuje, ale lista wyników dla każdej grupy są przedstawione oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="29855-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="29855-165">Operacje udostępniania globalnym <xref:System.Threading.Tasks.Task>, `pendingWork`, która służy jako kontroler proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="29855-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="29855-166">W tym przykładzie można uruchomić wklejając zmian w kodzie w [kompilowania aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub można postępuj zgodnie z instrukcjami [pobieranie aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobierania go, a następnie uruchom projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="29855-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="29855-167">Następujące dane wyjściowe przedstawia wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="29855-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="29855-168">Etykieta litera, A, wskazuje, że wynik jest od momentu pierwszego **Start** przycisk zostanie wybrany.</span><span class="sxs-lookup"><span data-stu-id="29855-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="29855-169">Numery wyświetlić kolejność adresów URL na liście elementów docelowych pobierania.</span><span class="sxs-lookup"><span data-stu-id="29855-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="29855-170">Jeśli użytkownik zdecyduje się **Start** trzy razy przycisk, aplikacja generuje dane wyjściowe podobne następujące wiersze.</span><span class="sxs-lookup"><span data-stu-id="29855-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="29855-171">Wiersze informacji rozpoczynających się od krzyżyk podpisać śledzenia (#) postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29855-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="29855-172">Grupy B i C uruchomić przed zakończył grupy A, ale dane wyjściowe dla każdej grupy jest wyświetlany osobno.</span><span class="sxs-lookup"><span data-stu-id="29855-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="29855-173">Wszystkie dane wyjściowe dla grupy A występuje jako pierwszy, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grup w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności adresy URL są wyświetlane na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="29855-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="29855-174">Jednak nie można przewidzieć kolejność, w którym rzeczywistego wystąpienia pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="29855-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="29855-175">Po uruchomieniu wielu grup zadań pobierania, które generują one są wszystkie aktywne.</span><span class="sxs-lookup"><span data-stu-id="29855-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="29855-176">Nie można zakładać, że a – 1 zostaną pobrane przed b-1 i nie można zakładać, że a – 1 zostaną pobrane przed A-2.</span><span class="sxs-lookup"><span data-stu-id="29855-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="29855-177">Definicje globalnej</span><span class="sxs-lookup"><span data-stu-id="29855-177">Global Definitions</span></span>  
 <span data-ttu-id="29855-178">Przykładowy kod zawiera następujące dwa deklaracje globalne, które są widoczne na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="29855-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="29855-179">`Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i uniemożliwia dowolną grupę zakłócania pracy wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="29855-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="29855-180">Zmienna znak `group`, dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności etykiet.</span><span class="sxs-lookup"><span data-stu-id="29855-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="29855-181">Obsługi zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="29855-181">The Click Event Handler</span></span>  
 <span data-ttu-id="29855-182">Program obsługi zdarzeń, `StartButton_Click`, rośnie litery grupy za każdym razem, użytkownik wybierze **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="29855-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="29855-183">Następnie wywołań obsługi `AccessTheWebAsync` się uruchomić operacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="29855-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="29855-184">Metoda AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="29855-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="29855-185">W tym przykładzie dzieli `AccessTheWebAsync` do dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="29855-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="29855-186">Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="29855-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="29855-187">Metoda używa języka zapytanie zintegrowanym (LINQ query) i <xref:System.Linq.Enumerable.ToArray%2A> uruchomić wszystkie zadania pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="29855-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="29855-188">`AccessTheWebAsync`następnie wywołuje `FinishOneGroupAsync` poczekać na ukończenie każdego pobrania i wyświetlenia jej długość.</span><span class="sxs-lookup"><span data-stu-id="29855-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="29855-189">`FinishOneGroupAsync`Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="29855-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="29855-190">Czy wartość zapobiega przerwania przez inną operację przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="29855-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="29855-191">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="29855-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="29855-192">Ta metoda przełączanie po kolei zadania pobierania w grupie, oczekiwanie na każdym z nich, wyświetlanie długość pobrany witryny sieci Web i dodawanie długość do całkowitej.</span><span class="sxs-lookup"><span data-stu-id="29855-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="29855-193">Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzanie metody zakłócał operacja, która jest już w procesie wyświetlania lub już jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="29855-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="29855-194">Jeśli takie działanie jest w toku, wprowadzając operacji oczekiwania kolei.</span><span class="sxs-lookup"><span data-stu-id="29855-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
 <span data-ttu-id="29855-195">W tym przykładzie można uruchomić wklejając zmian w kodzie w [kompilowania aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub można postępuj zgodnie z instrukcjami [pobieranie aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobierania go, a następnie uruchom projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="29855-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="29855-196">Ważne</span><span class="sxs-lookup"><span data-stu-id="29855-196">Points of Interest</span></span>  
 <span data-ttu-id="29855-197">Wiersze informacji rozpoczynające się znakiem numeru (#) w danych wyjściowych wyjaśnienie, jak działa w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="29855-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="29855-198">Dane wyjściowe zawierają następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="29855-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="29855-199">Grupy można uruchomić podczas poprzedniej grupy są wyświetlane dane wyjściowe, ale nie jest przerywana wyświetlanie wynik poprzedniego grupy.</span><span class="sxs-lookup"><span data-stu-id="29855-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="29855-200">`pendingWork` Zadań ma wartość null na początku `FinishOneGroupAsync` tylko dla grupy A, które uruchamiane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="29855-200">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="29855-201">Grupy A jeszcze nie ukończone wyrażenie await, po osiągnięciu `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="29855-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="29855-202">W związku z tym kontroli nie zwróciła do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpił.</span><span class="sxs-lookup"><span data-stu-id="29855-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="29855-203">Następujące dwa wiersze zawsze występować razem w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="29855-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="29855-204">Ten kod nie przerywa pracy między uruchamiania operacji grupy `StartButton_Click` i przypisywanie zadań dla grupy w celu `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="29855-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="29855-205">Po wprowadzeniu grupy `StartButton_Click`, operacja nie wykona wyrażenie await do czasu operacji wejścia `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="29855-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="29855-206">W związku z tym żadnych innych operacji przejąć kontrolę podczas tego segmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="29855-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <span data-ttu-id="29855-207"><a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładową aplikację</span><span class="sxs-lookup"><span data-stu-id="29855-207"><a name="BKMD_SettingUpTheExample"></a> Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="29855-208">Aby lepiej zrozumieć przykładową aplikację, można go pobrać, kompilacji samodzielnie lub przejrzeć kod na końcu tego tematu bez stosowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29855-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29855-209">Do uruchomienia w przykładzie jako aplikację pulpitu systemu Windows Presentation Foundation (WPF), musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="29855-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <span data-ttu-id="29855-210"><a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="29855-210"><a name="BKMK_DownloadingTheApp"></a> Downloading the App</span></span>  
  
1.  <span data-ttu-id="29855-211">Pobierz skompresowany plik z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="29855-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="29855-212">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29855-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="29855-213">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="29855-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="29855-214">Przejdź do folderu, który przechowuje zdekompresowanych przykładowy kod, a następnie otwórz plik rozwiązania (sln).</span><span class="sxs-lookup"><span data-stu-id="29855-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="29855-215">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="29855-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="29855-216">Wybierz klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="29855-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <span data-ttu-id="29855-217"><a name="BKMK_BuildingTheApp"></a>Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="29855-217"><a name="BKMK_BuildingTheApp"></a> Building the App</span></span>  
 <span data-ttu-id="29855-218">W poniższej sekcji przedstawiono kod służący do kompilacji w przykładzie jako aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="29855-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="29855-219">Do utworzenia aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="29855-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="29855-220">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29855-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="29855-221">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="29855-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="29855-222">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="29855-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="29855-223">W **zainstalowane szablony** okienku rozwiń **Visual C#**, a następnie rozwiń węzeł **Windows**.</span><span class="sxs-lookup"><span data-stu-id="29855-223">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="29855-224">Lista typów projektów, wybranie **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="29855-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="29855-225">Nazwij projekt `WebsiteDownloadWPF`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="29855-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="29855-226">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="29855-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="29855-227">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="29855-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="29855-228">Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="29855-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="29855-229">W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="29855-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="29855-230">Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="29855-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="29855-231">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="29855-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="29855-232">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="29855-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="29855-233">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="29855-233">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    // Add the following using directives, and add a reference for System.Net.Http.  
    using System.Net.Http;  
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="29855-234">Wybierz klawiszy CTRL + F5, uruchom program, a następnie wybierz pozycję **Start** przycisk kilka razy.</span><span class="sxs-lookup"><span data-stu-id="29855-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="29855-235">Wprowadź zmiany z [Wyłącz przycisk Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Anuluj i ponownie uruchom operację](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub [uruchomić wiele operacji i kolejki danych wyjściowych](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do obsługi ponownego rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="29855-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29855-236">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29855-236">See Also</span></span>  
 [<span data-ttu-id="29855-237">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="29855-237">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="29855-238">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="29855-238">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)