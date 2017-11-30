---
title: "Wytyczne dotyczące kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9eea60dafef508748df53e23c211f5778250e7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-collections"></a><span data-ttu-id="18d0c-102">Wytyczne dotyczące kolekcji</span><span class="sxs-lookup"><span data-stu-id="18d0c-102">Guidelines for Collections</span></span>
<span data-ttu-id="18d0c-103">Dowolny typ zaprojektowany specjalnie w celu manipulowania grupy obiektów o pewne cechy wspólne mogą zostać uwzględnione w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-103">Any type designed specifically to manipulate a group of objects having some common characteristic can be considered a collection.</span></span> <span data-ttu-id="18d0c-104">Prawie zawsze jest ona odpowiednia dla takich typów do zaimplementowania <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>, więc w tej sekcji możemy tylko należy wziąć pod uwagę typy Implementowanie jedno lub oba te interfejsy można kolekcje.</span><span class="sxs-lookup"><span data-stu-id="18d0c-104">It is almost always appropriate for such types to implement <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601>, so in this section we only consider types implementing one or both of those interfaces to be collections.</span></span>  
  
 <span data-ttu-id="18d0c-105">**X nie** w publicznych interfejsach API za pomocą lekko typu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-105">**X DO NOT** use weakly typed collections in public APIs.</span></span>  
  
 <span data-ttu-id="18d0c-106">Typ wszystkich zwracanych wartości i parametry przedstawiające elementy kolekcji powinna być typu elementu dokładne, nie dowolnego z jego typów podstawowych (dotyczy to tylko publiczne elementy członkowskie kolekcji).</span><span class="sxs-lookup"><span data-stu-id="18d0c-106">The type of all return values and parameters representing collection items should be the exact item type, not any of its base types (this applies only to public members of the collection).</span></span>  
  
 <span data-ttu-id="18d0c-107">**X nie** użyj <xref:System.Collections.ArrayList> lub <xref:System.Collections.Generic.List%601> w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="18d0c-107">**X DO NOT** use <xref:System.Collections.ArrayList> or <xref:System.Collections.Generic.List%601> in public APIs.</span></span>  
  
 <span data-ttu-id="18d0c-108">Te typy są przeznaczone do użycia w wewnętrznej implementacji nie znajduje się w publicznych interfejsach API struktury danych.</span><span class="sxs-lookup"><span data-stu-id="18d0c-108">These types are data structures designed to be used in internal implementation, not in public APIs.</span></span> <span data-ttu-id="18d0c-109">`List<T>`jest zoptymalizowana pod kątem wydajności i zasilania kosztem czystości interfejsów API i elastyczność.</span><span class="sxs-lookup"><span data-stu-id="18d0c-109">`List<T>` is optimized for performance and power at the cost of cleanness of the APIs and flexibility.</span></span> <span data-ttu-id="18d0c-110">Na przykład, jeśli `List<T>`, nie kiedykolwiek będzie Aby otrzymywać powiadomienia, gdy kod klienta modyfikuje kolekcję.</span><span class="sxs-lookup"><span data-stu-id="18d0c-110">For example, if you return `List<T>`, you will not ever be able to receive notifications when client code modifies the collection.</span></span> <span data-ttu-id="18d0c-111">Ponadto `List<T>` udostępnia wiele elementów członkowskich, takich jak <xref:System.Collections.Generic.List%601.BinarySearch%2A>, które nie są przydatne lub mające zastosowanie w wielu scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="18d0c-111">Also, `List<T>` exposes many members, such as <xref:System.Collections.Generic.List%601.BinarySearch%2A>, that are not useful or applicable in many scenarios.</span></span> <span data-ttu-id="18d0c-112">W poniższych sekcjach dwóch opisano typy (abstrakcje) przeznaczony specjalnie do użytku w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="18d0c-112">The following two sections describe types (abstractions) designed specifically for use in public APIs.</span></span>  
  
 <span data-ttu-id="18d0c-113">**X nie** użyj `Hashtable` lub `Dictionary<TKey,TValue>` w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="18d0c-113">**X DO NOT** use `Hashtable` or `Dictionary<TKey,TValue>` in public APIs.</span></span>  
  
 <span data-ttu-id="18d0c-114">Te typy są przeznaczone do użycia w implementacji wewnętrznej struktury danych.</span><span class="sxs-lookup"><span data-stu-id="18d0c-114">These types are data structures designed to be used in internal implementation.</span></span> <span data-ttu-id="18d0c-115">Należy używać w publicznych interfejsach API <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, lub niestandardowy typ wdrażanie jednego lub obu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="18d0c-115">Public APIs should use <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, or a custom type implementing one or both of the interfaces.</span></span>  
  
 <span data-ttu-id="18d0c-116">**X nie** użyj <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, lub innego typu, który implementuje jednej z tych interfejsów, z wyjątkiem jako typ zwracany `GetEnumerator` metody.</span><span class="sxs-lookup"><span data-stu-id="18d0c-116">**X DO NOT** use <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, or any other type that implements either of these interfaces, except as the return type of a `GetEnumerator` method.</span></span>  
  
 <span data-ttu-id="18d0c-117">Typy zwracania wyliczenia z metod innych niż `GetEnumerator` nie można używać z `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-117">Types returning enumerators from methods other than `GetEnumerator` cannot be used with the `foreach` statement.</span></span>  
  
 <span data-ttu-id="18d0c-118">**X nie** implementować jednocześnie `IEnumerator<T>` i `IEnumerable<T>` do tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-118">**X DO NOT** implement both `IEnumerator<T>` and `IEnumerable<T>` on the same type.</span></span> <span data-ttu-id="18d0c-119">To samo dotyczy interfejsów nierodzajowe `IEnumerator` i `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-119">The same applies to the nongeneric interfaces `IEnumerator` and `IEnumerable`.</span></span>  
  
## <a name="collection-parameters"></a><span data-ttu-id="18d0c-120">Kolekcja parametrów</span><span class="sxs-lookup"><span data-stu-id="18d0c-120">Collection Parameters</span></span>  
 <span data-ttu-id="18d0c-121">**CZY ✓** używać jak specjalizowany najmniej typu jako parametr typu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-121">**✓ DO** use the least-specialized type possible as a parameter type.</span></span> <span data-ttu-id="18d0c-122">Większość elementów członkowskich, biorąc kolekcje, jak używać parametrów `IEnumerable<T>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-122">Most members taking collections as parameters use the `IEnumerable<T>` interface.</span></span>  
  
 <span data-ttu-id="18d0c-123">**X należy UNIKAĆ** przy użyciu <xref:System.Collections.Generic.ICollection%601> lub <xref:System.Collections.ICollection> jako parametr tylko w celu uzyskania dostępu `Count` właściwości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-123">**X AVOID** using <xref:System.Collections.Generic.ICollection%601> or <xref:System.Collections.ICollection> as a parameter just to access the `Count` property.</span></span>  
  
 <span data-ttu-id="18d0c-124">Zamiast tego Rozważ użycie `IEnumerable<T>` lub `IEnumerable` i dynamicznie sprawdzanie, czy obiekt implementuje `ICollection<T>` lub `ICollection`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-124">Instead, consider using `IEnumerable<T>` or `IEnumerable` and dynamically checking whether the object implements `ICollection<T>` or `ICollection`.</span></span>  
  
## <a name="collection-properties-and-return-values"></a><span data-ttu-id="18d0c-125">Kolekcja właściwości i wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="18d0c-125">Collection Properties and Return Values</span></span>  
 <span data-ttu-id="18d0c-126">**X nie** dostarczenie kolekcji można ustawić właściwości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-126">**X DO NOT** provide settable collection properties.</span></span>  
  
 <span data-ttu-id="18d0c-127">Użytkownicy mogą zastąpić zawartość kolekcji przez wyczyszczenie kolekcji najpierw, a następnie dodanie nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-127">Users can replace the contents of the collection by clearing the collection first and then adding the new contents.</span></span> <span data-ttu-id="18d0c-128">Jeśli zastąpienie całej kolekcji jest typowy scenariusz, rozważ podanie `AddRange` metody w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-128">If replacing the whole collection is a common scenario, consider providing the `AddRange` method on the collection.</span></span>  
  
 <span data-ttu-id="18d0c-129">**CZY ✓** użyj `Collection<T>` lub podklasa klasy of `Collection<T>` dla właściwości lub return wartości reprezentujące kolekcje odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-129">**✓ DO** use `Collection<T>` or a subclass of `Collection<T>` for properties or return values representing read/write collections.</span></span>  
  
 <span data-ttu-id="18d0c-130">Jeśli `Collection<T>` nie spełnia wymagań dotyczących niektórych (np. Kolekcja nie musi zawierać <xref:System.Collections.IList>), użyj kolekcji niestandardowej zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="18d0c-130">If `Collection<T>` does not meet some requirement (e.g., the collection must not implement <xref:System.Collections.IList>), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or <xref:System.Collections.Generic.IList%601>.</span></span>  
  
 <span data-ttu-id="18d0c-131">**CZY ✓** użyj <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podklasa klasy `ReadOnlyCollection<T>`, lub w rzadkich przypadkach `IEnumerable<T>` dla właściwości lub return wartości reprezentujące kolekcji tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-131">**✓ DO** use <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, a subclass of `ReadOnlyCollection<T>`, or in rare cases `IEnumerable<T>` for properties or return values representing read-only collections.</span></span>  
  
 <span data-ttu-id="18d0c-132">Ogólnie rzecz biorąc, preferowane `ReadOnlyCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-132">In general, prefer `ReadOnlyCollection<T>`.</span></span> <span data-ttu-id="18d0c-133">Jeśli go nie spełnia wymagań dotyczących niektórych (np. Kolekcja nie musi zawierać `IList`), użyj kolekcji niestandardowej zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub `IList<T>`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-133">If it does not meet some requirement (e.g., the collection must not implement `IList`), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or `IList<T>`.</span></span> <span data-ttu-id="18d0c-134">Implementowanie niestandardowych kolekcji tylko do odczytu, należy wdrożyć `ICollection<T>.ReadOnly` do zwróci wartość false.</span><span class="sxs-lookup"><span data-stu-id="18d0c-134">If you do implement a custom read-only collection, implement `ICollection<T>.ReadOnly` to return false.</span></span>  
  
 <span data-ttu-id="18d0c-135">W przypadkach, gdy masz pewność, że jedyny scenariusz, w coraz można obsługiwać jest tylko do przodu iteracji, możesz użyć `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-135">In cases where you are sure that the only scenario you will ever want to support is forward-only iteration, you can simply use `IEnumerable<T>`.</span></span>  
  
 <span data-ttu-id="18d0c-136">**ROZWAŻ ✓** za pomocą podklasy kolekcje podstawowej ogólne zamiast bezpośrednio przy użyciu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-136">**✓ CONSIDER** using subclasses of generic base collections instead of using the collections directly.</span></span>  
  
 <span data-ttu-id="18d0c-137">Dzięki temu lepsze nazwy i dodawania elementów członkowskich pomocnika, które nie występują na typy podstawowe kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-137">This allows for a better name and for adding helper members that are not present on the base collection types.</span></span> <span data-ttu-id="18d0c-138">Jest to szczególnie dotyczy wysokiego poziomu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="18d0c-138">This is especially applicable to high-level APIs.</span></span>  
  
 <span data-ttu-id="18d0c-139">**ROZWAŻ ✓** zwracanie podklasą `Collection<T>` lub `ReadOnlyCollection<T>` z bardzo często używanych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-139">**✓ CONSIDER** returning a subclass of `Collection<T>` or `ReadOnlyCollection<T>` from very commonly used methods and properties.</span></span>  
  
 <span data-ttu-id="18d0c-140">To umożliwi dodawanie metody pomocnicze lub zmień implementację kolekcji w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-140">This will make it possible for you to add helper methods or change the collection implementation in the future.</span></span>  
  
 <span data-ttu-id="18d0c-141">**ROZWAŻ ✓** przy użyciu kolekcji kluczem, jeśli elementy przechowywane w kolekcji ma unikatowy kluczy (nazwy, identyfikatory itp.).</span><span class="sxs-lookup"><span data-stu-id="18d0c-141">**✓ CONSIDER** using a keyed collection if the items stored in the collection have unique keys (names, IDs, etc.).</span></span> <span data-ttu-id="18d0c-142">Kolekcje zabezpieczone kluczami są kolekcjami, które mogą być indeksowane według zarówno całkowitą, jak i klucz i są zwykle implementowany przez dziedziczenie z `KeyedCollection<TKey,TItem>`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-142">Keyed collections are collections that can be indexed by both an integer and a key and are usually implemented by inheriting from `KeyedCollection<TKey,TItem>`.</span></span>  
  
 <span data-ttu-id="18d0c-143">Kolekcje zabezpieczone kluczami zazwyczaj ma większe udzielaniu pamięci i nie powinna być używana, jeśli obciążenie pamięci przeważa nad korzyści kluczy.</span><span class="sxs-lookup"><span data-stu-id="18d0c-143">Keyed collections usually have larger memory footprints and should not be used if the memory overhead outweighs the benefits of having the keys.</span></span>  
  
 <span data-ttu-id="18d0c-144">**X nie** zwracać wartości null z kolekcji właściwości lub metody zwracających kolekcje.</span><span class="sxs-lookup"><span data-stu-id="18d0c-144">**X DO NOT** return null values from collection properties or from methods returning collections.</span></span> <span data-ttu-id="18d0c-145">Zwraca pustą kolekcję lub pusta tablica, zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="18d0c-145">Return an empty collection or an empty array instead.</span></span>  
  
 <span data-ttu-id="18d0c-146">Ogólną zasadą jest null i pusty kolekcji (0 elementów) lub tablicą powinien być traktowany takie same.</span><span class="sxs-lookup"><span data-stu-id="18d0c-146">The general rule is that null and empty (0 item) collections or arrays should be treated the same.</span></span>  
  
### <a name="snapshots-versus-live-collections"></a><span data-ttu-id="18d0c-147">Migawki i kolekcje na żywo</span><span class="sxs-lookup"><span data-stu-id="18d0c-147">Snapshots Versus Live Collections</span></span>  
 <span data-ttu-id="18d0c-148">Kolekcje reprezentujący stan w pewnym momencie w czasie są nazywane kolekcje migawki.</span><span class="sxs-lookup"><span data-stu-id="18d0c-148">Collections representing a state at some point in time are called snapshot collections.</span></span> <span data-ttu-id="18d0c-149">Kolekcja zawierająca wiersze zwrócone w wyniku zapytania bazy danych będzie na przykład migawki.</span><span class="sxs-lookup"><span data-stu-id="18d0c-149">For example, a collection containing rows returned from a database query would be a snapshot.</span></span> <span data-ttu-id="18d0c-150">Kolekcje, które zawsze reprezentują bieżący stan są nazywane kolekcje na żywo.</span><span class="sxs-lookup"><span data-stu-id="18d0c-150">Collections that always represent the current state are called live collections.</span></span> <span data-ttu-id="18d0c-151">Na przykład kolekcja `ComboBox` elementów jest kolekcją na żywo.</span><span class="sxs-lookup"><span data-stu-id="18d0c-151">For example, a collection of `ComboBox` items is a live collection.</span></span>  
  
 <span data-ttu-id="18d0c-152">**X nie** zwrócić migawki kolekcji z właściwości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-152">**X DO NOT** return snapshot collections from properties.</span></span> <span data-ttu-id="18d0c-153">Właściwości powinny zwracać kolekcje na żywo.</span><span class="sxs-lookup"><span data-stu-id="18d0c-153">Properties should return live collections.</span></span>  
  
 <span data-ttu-id="18d0c-154">Metody pobierające właściwości powinny być bardzo prostą i wygodną operacji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-154">Property getters should be very lightweight operations.</span></span> <span data-ttu-id="18d0c-155">Zwracanie migawki wymaga tworzenie kopii wewnętrznej kolekcji w operacji O(n).</span><span class="sxs-lookup"><span data-stu-id="18d0c-155">Returning a snapshot requires creating a copy of an internal collection in an O(n) operation.</span></span>  
  
 <span data-ttu-id="18d0c-156">**CZY ✓** za pomocą kolekcji migawki lub na żywo `IEnumerable<T>` (lub jej podtyp) do reprezentowania kolekcje, które są volatile (tj., które można zmienić bez jawnie modyfikowania kolekcji).</span><span class="sxs-lookup"><span data-stu-id="18d0c-156">**✓ DO** use either a snapshot collection or a live `IEnumerable<T>` (or its subtype) to represent collections that are volatile (i.e., that can change without explicitly modifying the collection).</span></span>  
  
 <span data-ttu-id="18d0c-157">Ogólnie rzecz biorąc wszystkie kolekcje reprezentujący udostępnianego zasobu (np. pliki w katalogu) są nietrwałe.</span><span class="sxs-lookup"><span data-stu-id="18d0c-157">In general, all collections representing a shared resource (e.g., files in a directory) are volatile.</span></span> <span data-ttu-id="18d0c-158">Takie kolekcje są bardzo trudne lub niemożliwe do zaimplementowania jako kolekcje na żywo, chyba że implementacja jest po prostu wyliczający tylko do przodu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-158">Such collections are very difficult or impossible to implement as live collections unless the implementation is simply a forward-only enumerator.</span></span>  
  
## <a name="choosing-between-arrays-and-collections"></a><span data-ttu-id="18d0c-159">Wybór między tablicami i kolekcji</span><span class="sxs-lookup"><span data-stu-id="18d0c-159">Choosing Between Arrays and Collections</span></span>  
 <span data-ttu-id="18d0c-160">**CZY ✓** Preferuj kolekcji przed tablic.</span><span class="sxs-lookup"><span data-stu-id="18d0c-160">**✓ DO** prefer collections over arrays.</span></span>  
  
 <span data-ttu-id="18d0c-161">Kolekcje zapewniają większą kontrolę nad zawartością, można rozwijać, wraz z upływem czasu i są bardziej użyteczne.</span><span class="sxs-lookup"><span data-stu-id="18d0c-161">Collections provide more control over contents, can evolve over time, and are more usable.</span></span> <span data-ttu-id="18d0c-162">Ponadto używanie tablic w scenariuszach tylko do odczytu nie jest zalecane, ponieważ koszt Sklonowanie tablicy jest zaporowe.</span><span class="sxs-lookup"><span data-stu-id="18d0c-162">In addition, using arrays for read-only scenarios is discouraged because the cost of cloning the array is prohibitive.</span></span> <span data-ttu-id="18d0c-163">Użyteczność badania wykazały, że niektórzy deweloperzy bezpiecznie więcej za pomocą opartego na kolekcji interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="18d0c-163">Usability studies have shown that some developers feel more comfortable using collection-based APIs.</span></span>  
  
 <span data-ttu-id="18d0c-164">Jednak jeśli tworzysz API niskiego poziomu, może być lepiej używać różnych macierzy dla scenariuszy odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-164">However, if you are developing low-level APIs, it might be better to use arrays for read-write scenarios.</span></span> <span data-ttu-id="18d0c-165">Tablice mają mniejsze zużycie pamięci, co zmniejsza zestaw roboczy, a dostęp do elementów w tablicy trwa krócej, ponieważ jest zoptymalizowany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="18d0c-165">Arrays have a smaller memory footprint, which helps reduce the working set, and access to elements in an array is faster because it is optimized by the runtime.</span></span>  
  
 <span data-ttu-id="18d0c-166">**ROZWAŻ ✓** używanie tablic w niskiego poziomu interfejsów API do zminimalizowania zużycia pamięci i zmaksymalizować wydajność.</span><span class="sxs-lookup"><span data-stu-id="18d0c-166">**✓ CONSIDER** using arrays in low-level APIs to minimize memory consumption and maximize performance.</span></span>  
  
 <span data-ttu-id="18d0c-167">**CZY ✓** Użyj tablice typu byte zamiast kolekcji bajtów.</span><span class="sxs-lookup"><span data-stu-id="18d0c-167">**✓ DO** use byte arrays instead of collections of bytes.</span></span>  
  
 <span data-ttu-id="18d0c-168">**X nie** Użycie tablic dla właściwości, jeśli właściwość musiałaby zwracać nowej tablicy (np. kopia tablicy wewnętrznej) zawsze jest wywoływana metoda pobierająca właściwości.</span><span class="sxs-lookup"><span data-stu-id="18d0c-168">**X DO NOT** use arrays for properties if the property would have to return a new array (e.g., a copy of an internal array) every time the property getter is called.</span></span>  
  
## <a name="implementing-custom-collections"></a><span data-ttu-id="18d0c-169">Implementowanie kolekcje niestandardowe</span><span class="sxs-lookup"><span data-stu-id="18d0c-169">Implementing Custom Collections</span></span>  
 <span data-ttu-id="18d0c-170">**ROZWAŻ ✓** dziedziczących `Collection<T>`, `ReadOnlyCollection<T>`, lub `KeyedCollection<TKey,TItem>` podczas projektowania nowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-170">**✓ CONSIDER** inheriting from `Collection<T>`, `ReadOnlyCollection<T>`, or `KeyedCollection<TKey,TItem>` when designing new collections.</span></span>  
  
 <span data-ttu-id="18d0c-171">**CZY ✓** zaimplementować `IEnumerable<T>` podczas projektowania nowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-171">**✓ DO** implement `IEnumerable<T>` when designing new collections.</span></span> <span data-ttu-id="18d0c-172">Rozważ zaimplementowanie `ICollection<T>` lub nawet `IList<T>` których warto.</span><span class="sxs-lookup"><span data-stu-id="18d0c-172">Consider implementing `ICollection<T>` or even `IList<T>` where it makes sense.</span></span>  
  
 <span data-ttu-id="18d0c-173">Podczas wdrażania tych kolekcji niestandardowych, zgodne ze wzorcem interfejsu API, ustala `Collection<T>` i `ReadOnlyCollection<T>` możliwym stopniu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-173">When implementing such custom collection, follow the API pattern established by `Collection<T>` and `ReadOnlyCollection<T>` as closely as possible.</span></span> <span data-ttu-id="18d0c-174">Oznacza to, że jawnie implementować tych samych elementów członkowskich, nazwy parametrów, takich jak te dwie kolekcje nazwy ich i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="18d0c-174">That is, implement the same members explicitly, name the parameters like these two collections name them, and so on.</span></span>  
  
 <span data-ttu-id="18d0c-175">**ROZWAŻ ✓** implementowanie interfejsów kolekcji nierodzajowe (`IList` i `ICollection`) Jeśli kolekcji będą często przekazywane do interfejsów API biorąc te interfejsy jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="18d0c-175">**✓ CONSIDER** implementing nongeneric collection interfaces (`IList` and `ICollection`) if the collection will often be passed to APIs taking these interfaces as input.</span></span>  
  
 <span data-ttu-id="18d0c-176">**X należy UNIKAĆ** implementowanie interfejsów kolekcji na typach z złożonych interfejsów API niezwiązanych ze sobą koncepcji kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-176">**X AVOID** implementing collection interfaces on types with complex APIs unrelated to the concept of a collection.</span></span>  
  
 <span data-ttu-id="18d0c-177">**X nie** dziedziczyć nierodzajowe kolekcje podstawowej takich jak `CollectionBase`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-177">**X DO NOT** inherit from nongeneric base collections such as `CollectionBase`.</span></span> <span data-ttu-id="18d0c-178">Użyj `Collection<T>`, `ReadOnlyCollection<T>`, i `KeyedCollection<TKey,TItem>` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="18d0c-178">Use `Collection<T>`, `ReadOnlyCollection<T>`, and `KeyedCollection<TKey,TItem>` instead.</span></span>  
  
### <a name="naming-custom-collections"></a><span data-ttu-id="18d0c-179">Kolekcje niestandardowe nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="18d0c-179">Naming Custom Collections</span></span>  
 <span data-ttu-id="18d0c-180">Kolekcje (typy, które implementują `IEnumerable`) są tworzone głównie z dwóch przyczyn: (1), aby utworzyć nową strukturę danych z operacjami specyficzne dla struktury i często charakterystyki wydajności innego niż istniejących struktur danych (np. <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) i (2), aby utworzyć kolekcję specjalne do przechowywania określonych elementów (np. <xref:System.Collections.Specialized.StringCollection>).</span><span class="sxs-lookup"><span data-stu-id="18d0c-180">Collections (types that implement `IEnumerable`) are created mainly for two reasons: (1) to create a new data structure with structure-specific operations and often different performance characteristics than existing data structures (e.g.,  <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>), and (2) to create a specialized collection for holding a specific set of items (e.g.,  <xref:System.Collections.Specialized.StringCollection>).</span></span> <span data-ttu-id="18d0c-181">Struktury danych są najczęściej używane w wewnętrznej implementacji aplikacji i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="18d0c-181">Data structures are most often used in the internal implementation of applications and libraries.</span></span> <span data-ttu-id="18d0c-182">Specjalne kolekcje są głównie mają być uwidaczniane w interfejsów API (jako typów właściwości oraz parametru).</span><span class="sxs-lookup"><span data-stu-id="18d0c-182">Specialized collections are mainly to be exposed in APIs (as property and parameter types).</span></span>  
  
 <span data-ttu-id="18d0c-183">**CZY ✓** Użyj sufiksu "Słownik" w nazwach obiektów abstrakcyjnych implementacja `IDictionary` lub `IDictionary<TKey,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-183">**✓ DO** use the "Dictionary" suffix in names of abstractions implementing `IDictionary` or `IDictionary<TKey,TValue>`.</span></span>  
  
 <span data-ttu-id="18d0c-184">**CZY ✓** Użyj sufiksu "Kolekcji" w nazwach typów implementujących `IEnumerable` (lub któregokolwiek z jej obiektów podrzędnych) i reprezentujący listę elementów.</span><span class="sxs-lookup"><span data-stu-id="18d0c-184">**✓ DO** use the "Collection" suffix in names of types implementing `IEnumerable` (or any of its descendants) and representing a list of items.</span></span>  
  
 <span data-ttu-id="18d0c-185">**CZY ✓** Użyj nazwy struktury danych w strukturach danych niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="18d0c-185">**✓ DO** use the appropriate data structure name for custom data structures.</span></span>  
  
 <span data-ttu-id="18d0c-186">**X należy UNIKAĆ** przy użyciu wszelkie sufiksy podejrzeń konkretnej implementacji, takie jak "LinkedList" lub "Hashtable," w nazwach obiektów abstrakcyjnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18d0c-186">**X AVOID** using any suffixes implying particular implementation, such as "LinkedList" or "Hashtable," in names of collection abstractions.</span></span>  
  
 <span data-ttu-id="18d0c-187">**ROZWAŻ ✓** prefiksu nazwy kolekcji o nazwie typu elementu.</span><span class="sxs-lookup"><span data-stu-id="18d0c-187">**✓ CONSIDER** prefixing collection names with the name of the item type.</span></span> <span data-ttu-id="18d0c-188">Na przykład kolekcja przechowywanie elementów typu `Address` (Implementowanie `IEnumerable<Address>`) powinno być nazwanym `AddressCollection`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-188">For example, a collection storing items of type `Address` (implementing `IEnumerable<Address>`) should be named `AddressCollection`.</span></span> <span data-ttu-id="18d0c-189">Jeśli typ elementu jest interfejsem, prefiks "I" elementu typu można pominąć.</span><span class="sxs-lookup"><span data-stu-id="18d0c-189">If the item type is an interface, the "I" prefix of the item type can be omitted.</span></span> <span data-ttu-id="18d0c-190">W związku z tym Kolekcja <xref:System.IDisposable> elementów można wywołać `DisposableCollection`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-190">Thus, a collection of <xref:System.IDisposable> items can be called `DisposableCollection`.</span></span>  
  
 <span data-ttu-id="18d0c-191">**ROZWAŻ ✓** przy użyciu prefiksu "ReadOnly" w nazwach kolekcji tylko do odczytu, jeśli odpowiedniej kolekcji zapisu mogą być dodane lub już istnieje w ramach.</span><span class="sxs-lookup"><span data-stu-id="18d0c-191">**✓ CONSIDER** using the "ReadOnly" prefix in names of read-only collections if a corresponding writeable collection might be added or already exists in the framework.</span></span>  
  
 <span data-ttu-id="18d0c-192">Na przykład powinna być wywoływana tylko do odczytu kolekcji ciągów `ReadOnlyStringCollection`.</span><span class="sxs-lookup"><span data-stu-id="18d0c-192">For example, a read-only collection of strings should be called `ReadOnlyStringCollection`.</span></span>  
  
 <span data-ttu-id="18d0c-193">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="18d0c-193">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="18d0c-194">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="18d0c-194">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d0c-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18d0c-195">See Also</span></span>  
 [<span data-ttu-id="18d0c-196">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="18d0c-196">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="18d0c-197">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="18d0c-197">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)