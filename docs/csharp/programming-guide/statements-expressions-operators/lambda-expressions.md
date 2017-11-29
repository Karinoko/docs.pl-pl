---
title: "Wyrażenia lambda (Przewodnik programowania w języku C#)"
ms.date: 03/03/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: "64"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9127cc5404fb85356f01cac26aa7b03a8ccd70da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="919a8-102">Wyrażenia lambda (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="919a8-102">Lambda Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="919a8-103">Wyrażenie lambda jest [funkcji anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) używanej do tworzenia [delegaty](../../../csharp/programming-guide/delegates/using-delegates.md) lub [drzewo wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) typów.</span><span class="sxs-lookup"><span data-stu-id="919a8-103">A lambda expression is an [anonymous function](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) that you can use to create [delegates](../../../csharp/programming-guide/delegates/using-delegates.md) or [expression tree](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) types.</span></span> <span data-ttu-id="919a8-104">Za pomocą wyrażenia lambda można pisać funkcje lokalne, które mogą być przekazywane jako argumenty lub zwracane jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="919a8-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="919a8-105">Wyrażenia lambda są szczególnie przydatne w przypadku pisania wyrażeń zapytań w języku LINQ.</span><span class="sxs-lookup"><span data-stu-id="919a8-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>  
  
 <span data-ttu-id="919a8-106">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda [ => ](../../../csharp/language-reference/operators/lambda-operator.md), i umieszcza blok wyrażenia lub instrukcji z drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="919a8-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="919a8-107">Na przykład, wyrażenie lambda `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów.</span><span class="sxs-lookup"><span data-stu-id="919a8-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="919a8-108">To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="919a8-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="919a8-109">Aby utworzyć typ drzewa wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="919a8-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="919a8-110">`=>` Operator ma takie samo pierwszeństwo jako przypisania (`=`) i jest [prawo asocjacyjnej](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (zobacz sekcję "Kojarzenie" w artykule operatory).</span><span class="sxs-lookup"><span data-stu-id="919a8-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="919a8-111">Wyrażenia lambda są używane w oparte na metodzie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wysyła zapytanie jako argumenty do metod operator standardowej kwerendy, takich jak <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="919a8-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="919a8-112">Jeśli używasz składni na podstawie metody do wywołania <xref:System.Linq.Enumerable.Where%2A> metody w <xref:System.Linq.Enumerable> klasy (tak jak w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) parametr jest typem obiektu delegowanego <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="919a8-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="919a8-113">Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="919a8-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="919a8-114">Podczas wywoływania tej samej metody, na przykład <xref:System.Linq.Queryable?displayProperty=nameWithType> klasy (tak jak w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), a następnie typ parametru jest <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> Func w przypadku dowolnego delegatów Func o do szesnastu parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="919a8-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="919a8-115">I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="919a8-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="919a8-116">Zezwalaj na wyrażeń lambda `Where` wywołań wyglądać podobnie, chociaż w rzeczywistości różni się typ obiektu utworzone na podstawie lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="919a8-117">W poprzednim przykładzie parametr typu wejściowy powiadomienie, że podpis delegata ma jedną niejawnie wpisanych `int`i zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="919a8-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="919a8-118">Wyrażenia lambda można przekonwertować na delegata tego typu, ponieważ obejmuje ona również jeden parametr wejściowy (`x`) i które kompilator niejawnie przekonwertować na typ wartości zwracanej `int`.</span><span class="sxs-lookup"><span data-stu-id="919a8-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="919a8-119">(Wnioskowanie typów omówiono bardziej szczegółowo w następnych sekcjach). Kiedy delegat jest wywołany za pomocą parametru wejściowego 5, zwraca wynik 25.</span><span class="sxs-lookup"><span data-stu-id="919a8-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="919a8-120">Wyrażenia lambda nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) lub [jako](../../../csharp/language-reference/keywords/as.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="919a8-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="919a8-121">Wszystkie ograniczenia, które dotyczą metod anonimowych, dotyczą także wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="919a8-122">Aby uzyskać więcej informacji, zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="919a8-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="919a8-123">Lambdy wyrażeń</span><span class="sxs-lookup"><span data-stu-id="919a8-123">Expression Lambdas</span></span>  
 <span data-ttu-id="919a8-124">Wyrażenia lambda za pomocą wyrażenia po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*.</span><span class="sxs-lookup"><span data-stu-id="919a8-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="919a8-125">Wyrażenia lambda są często używane w konstrukcji [drzew wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span><span class="sxs-lookup"><span data-stu-id="919a8-125">Expression lambdas are used extensively in the construction of [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span></span> <span data-ttu-id="919a8-126">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="919a8-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>  
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="919a8-127">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="919a8-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="919a8-128">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="919a8-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="919a8-129">Czasami wywnioskowanie typów wejściowych jest dla kompilatora trudne lub wręcz niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="919a8-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="919a8-130">W takiej sytuacji można jawnie określić typy, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="919a8-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="919a8-131">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="919a8-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="919a8-132">Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="919a8-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="919a8-133">Jednak w przypadku tworzenia drzew wyrażeń, które będą obliczane poza programem .NET Framework, na przykład w programie SQL Server, nie należy używać wywołań metod w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="919a8-134">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="919a8-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="919a8-135">Lambdy instrukcji</span><span class="sxs-lookup"><span data-stu-id="919a8-135">Statement Lambdas</span></span>  
 <span data-ttu-id="919a8-136">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="919a8-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="919a8-137">(parametry wejściowe) = > {instrukcja;}</span><span class="sxs-lookup"><span data-stu-id="919a8-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="919a8-138">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="919a8-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="919a8-139">Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="919a8-139">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="919a8-140">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="919a8-140">Async Lambdas</span></span>  
 <span data-ttu-id="919a8-141">Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [async](../../../csharp/language-reference/keywords/async.md) i [await](../../../csharp/language-reference/keywords/await.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="919a8-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="919a8-142">Na przykład w poniższym przykładzie formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekujące na metody asynchronicznej `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="919a8-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="919a8-143">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="919a8-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="919a8-144">Aby dodać ten program obsługi, Dodaj `async` modyfikator przed listy parametrów lambda, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="919a8-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="919a8-145">Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="919a8-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="919a8-146">Lambdy ze standardowymi operatorami zapytań</span><span class="sxs-lookup"><span data-stu-id="919a8-146">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="919a8-147">Wiele standardowych operatorów zapytań ma parametr wejściowy, którego typ jest jednym z <xref:System.Func%602> rodzina delegatów.</span><span class="sxs-lookup"><span data-stu-id="919a8-147">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="919a8-148">Te delegaty używają parametrów typu użycia, aby zdefiniować liczbę i typy parametrów wejściowych oraz zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="919a8-148">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="919a8-149">`Func`Obiekty delegowane są bardzo przydatne w przypadku hermetyzując wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="919a8-149">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="919a8-150">Na przykład rozważmy następujący typ delegata:</span><span class="sxs-lookup"><span data-stu-id="919a8-150">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="919a8-151">Delegat można wdrożyć jako `Func<int,bool> myFunc` gdzie `int` jest parametrem wejściowym i `bool` jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="919a8-151">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="919a8-152">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="919a8-152">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="919a8-153">`Func<int, string, bool>`Definiuje delegata z dwóch parametrów wejściowych, `int` i `string`i typ zwracany `bool`.</span><span class="sxs-lookup"><span data-stu-id="919a8-153">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="919a8-154">Następujące `Func` delegata, gdy jest wywoływana, zwraca wartość PRAWDA lub FAŁSZ, aby wskazać, czy parametr wejściowy jest równa 5:</span><span class="sxs-lookup"><span data-stu-id="919a8-154">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="919a8-155">Może też podawać wyrażenia lambda, gdy typ argumentu jest `Expression<Func>`, na przykład w przypadku standardowych operatorów zapytań zdefiniowane w System.Linq.Queryable.</span><span class="sxs-lookup"><span data-stu-id="919a8-155">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="919a8-156">Po określeniu `Expression<Func>` argument, wyrażenie lambda zostanie skompilowany na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="919a8-156">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="919a8-157">Operator zapytania standardowe <xref:System.Linq.Enumerable.Count%2A> metody, jest następujący:</span><span class="sxs-lookup"><span data-stu-id="919a8-157">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="919a8-158">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="919a8-158">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="919a8-159">To wyrażenie lambda określonej liczby tych liczb całkowitych (`n`) który podzielona przez dwa mieć reszty 1.</span><span class="sxs-lookup"><span data-stu-id="919a8-159">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="919a8-160">Następujący wiersz kodu tworzy sekwencję, który zawiera wszystkie elementy w `numbers` tablicy, które są do lewej strony 9, ponieważ jest to pierwszy numer w sekwencji, które nie spełniają warunek:</span><span class="sxs-lookup"><span data-stu-id="919a8-160">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="919a8-161">W tym przykładzie pokazano, jak określić wiele parametrów danych wejściowych, umieszczając je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="919a8-161">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="919a8-162">Metoda zwraca wszystkie elementy w tablicy liczb, dopóki nie napotka liczby, której wartość jest mniejsza niż jej pozycja.</span><span class="sxs-lookup"><span data-stu-id="919a8-162">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="919a8-163">Nie należy mylić operatora lambda (`=>`) z operatorem większe lub równe (`>=`).</span><span class="sxs-lookup"><span data-stu-id="919a8-163">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="919a8-164">Wnioskowanie typów w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="919a8-164">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="919a8-165">Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typu delegata parametru i innych czynników, tak jak opisano w specyfikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="919a8-165">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="919a8-166">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="919a8-166">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="919a8-167">Tak, wyszukując `IEnumerable<Customer>`, następnie wejściowego zmiennej jest wywnioskowany jako `Customer` obiektu, co oznacza, że masz dostęp do właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="919a8-167">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="919a8-168">Ogólne reguły dotyczące wyrażeń lambda są następujące:</span><span class="sxs-lookup"><span data-stu-id="919a8-168">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="919a8-169">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="919a8-169">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="919a8-170">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="919a8-170">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="919a8-171">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="919a8-171">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="919a8-172">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”.</span><span class="sxs-lookup"><span data-stu-id="919a8-172">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="919a8-173">Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-173">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="919a8-174">W takich przypadkach typ odwołuje się do typu delegata lub <xref:System.Linq.Expressions.Expression> wpisz jest konwertowane Wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-174">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="919a8-175">Zakres zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="919a8-175">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="919a8-176">Wyrażenia lambda, może się odwoływać do *zmienne zewnętrzne* (zobacz [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) w zakresie w metodę, która definiuje funkcję lambda, lub w zakresie w typie, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-176">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="919a8-177">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="919a8-177">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="919a8-178">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="919a8-178">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="919a8-179">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="919a8-179">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="919a8-180">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="919a8-180">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="919a8-181">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="919a8-181">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="919a8-182">Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="919a8-182">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="919a8-183">Wyrażenia lambda nie może bezpośrednio przechwytywania `ref` lub `out` parametru z metody otaczającej.</span><span class="sxs-lookup"><span data-stu-id="919a8-183">A lambda expression cannot directly capture a `ref` or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="919a8-184">Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.</span><span class="sxs-lookup"><span data-stu-id="919a8-184">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="919a8-185">Wyrażenia lambda nie może zawierać `goto` instrukcji, `break` instrukcji lub `continue` instrukcji, która znajduje się wewnątrz funkcji lambda w przypadku docelowej instrukcji skok poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="919a8-185">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="919a8-186">Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="919a8-186">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="919a8-187">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="919a8-187">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="919a8-188">Polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="919a8-188">Featured Book Chapter</span></span>  
 <span data-ttu-id="919a8-189">[Obiekty delegowane, zdarzeń i wyrażenia Lambda](http://go.microsoft.com/fwlink/?LinkId=195395) w [C# 3.0 Cookbook, trzecia edycja: ponad 250 rozwiązań dla programistów języka C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="919a8-189">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919a8-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="919a8-190">See Also</span></span>  
 [<span data-ttu-id="919a8-191">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="919a8-191">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="919a8-192">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="919a8-192">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="919a8-193">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="919a8-193">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="919a8-194">jest</span><span class="sxs-lookup"><span data-stu-id="919a8-194">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="919a8-195">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="919a8-195">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [<span data-ttu-id="919a8-196">Visual Studio 2008 C# przykłady (zobacz zapytań LINQ przykładowe pliki i XQuery program)</span><span class="sxs-lookup"><span data-stu-id="919a8-196">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [<span data-ttu-id="919a8-197">Wyrażenia lambda cykliczne</span><span class="sxs-lookup"><span data-stu-id="919a8-197">Recursive lambda expressions</span></span>](http://go.microsoft.com/fwlink/?LinkId=112395)