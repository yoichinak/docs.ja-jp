---
title: ラムダ式 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 77701653abacbe6d876c0890a11586f0840bad5d
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200898"
---
# <a name="lambda-expressions-c-programming-guide"></a>ラムダ式 (C# プログラミング ガイド)

ラムダ式は、 [デリゲート](anonymous-methods.md) 型または [式ツリー](../delegates/using-delegates.md) 型を作成するために使用できる [匿名関数](../concepts/expression-trees/index.md) です。 ラムダ式を使用すると、引数として渡したり関数呼び出しの結果値として返すことができるローカル関数を記述できます。 ラムダ式は、LINQ クエリ式を記述する場合に特に便利です。
  
ラムダ式を作成するには、ラムダ演算子 ( [=>](../../../csharp/language-reference/operators/lambda-operator.md)) の左側に入力パラメーター (ある場合) を指定し、反対側に式またはステートメント ブロックを置きます。 たとえば、ラムダ式 `x => x * x` は、 `x` という名前のパラメーターを指定し、 `x` を 2 乗した値を返します。 次の例に示すように、この式をデリゲート型に割り当てることもできます。  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 式ツリー型を作成するには  
  
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
  
 `=>` 演算子は、代入 (`=`) と同じ優先順位であり、[結合規則が右から左](../../../csharp/programming-guide/statements-expressions-operators/operators.md) です (演算子に関するドキュメントの「結合規則」を参照してください)。  
  
 ラムダは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] のメソッド ベースのクエリ内で標準クエリ演算子のメソッド (<xref:System.Linq.Enumerable.Where%2A> など) の引数として使用されます。  
  
 メソッド ベースの構文を使用して ( <xref:System.Linq.Enumerable.Where%2A> to Objects および <xref:System.Linq.Enumerable> の場合と同様に) [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クラスの [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メソッドを呼び出すと、パラメーターはデリゲート型 <xref:System.Func%602?displayProperty=nameWithType>になります。 ラムダ式はデリゲートを作成するための最も便利な方法です。 たとえば (<xref:System.Linq.Queryable?displayProperty=nameWithType> の場合と同様に) [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] クラスの同じメソッドを呼び出すと、パラメーター型は <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> になります。Func は最大 16 の入力パラメーターを持つ Func デリゲートです。 ラムダ式は、こうした式ツリーを構築するための非常に簡潔な方法でもあります。 ラムダを使用すると `Where` 呼び出しの外観を似たものにできますが、ラムダから実際に作成されるオブジェクトの型は異なります。  
  
 先ほどの例では、デリゲート シグネチャは暗黙的に型指定される `int`型の入力パラメーターを 1 つ持ち、 `int`を返します。 このラムダ式を同じ型のデリゲートに変換することができます。デリゲートも 1 つの入力パラメーター (`x`) を持ち、コンパイラが暗黙的に `int` 型に変換できる値を返すからです  (型の推論については後のセクションで詳しく説明します)。入力パラメーターとして 5 を使用してデリゲートを呼び出すと、デリゲートは 25 という結果を返します。  
  
 [is](../../../csharp/language-reference/keywords/is.md) 演算子または [as](../../../csharp/language-reference/keywords/as.md) 演算子の左辺にラムダを使用することはできません。  
  
 匿名メソッドに適用される制限は、すべてラムダ式にも適用されます。 詳細については、「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照してください。  
  
## <a name="expression-lambdas"></a>式形式のラムダ

 => 演算子の右辺に式があるラムダ式を "*式形式のラムダ*" と呼びます。 式形式のラムダは、[式ツリー](../concepts/expression-trees/index.md)の構築に幅広く使用されます。 式形式のラムダは式の結果を返します。基本的な形式は次のとおりです。
  
```csharp
(input-parameters) => expression
```

 かっこはラムダの入力パラメーターが 1 つの場合のみ省略可能で、それ以外の場合は必須です。 入力パラメーターが 2 つ以上ある場合は、かっこで囲んで各パラメーターをコンマで区切ります。  
  
```csharp
(x, y) => x == y
```

 コンパイラが入力の型を推論するのが困難または不可能な場合もあります。 このような場合は、次の例のように型を明示的に指定できます。  
  
```csharp
(int x, string s) => s.Length > x
```
 入力パラメーターの種類は、すべて明示的またはすべて暗黙的である必要があります。それ以外の場合、C# は [CS0748](../../misc/cs0748.md) コンパイラ エラーを生成します。

 入力パラメーターがないことを指定するには、次のように空のかっこを使用します。  
  
```csharp
() => SomeMethod()
```

 この例では、式形式のラムダの本体をメソッド呼び出しで構成できることに注目してください。 ただし、SQL Server など .NET Framework の外部で評価される式ツリーを作成する場合は、ラムダ式内でメソッド呼び出しを使用することはできません。 .NET 共通言語ランタイムのコンテキストの外部では、これらのメソッドは通用しません。  
  
## <a name="statement-lambdas"></a>ステートメント形式のラムダ

 ステートメント形式のラムダは式形式のラムダに似ていますが、ステートメントが中かっこで囲まれる点が異なります。  
  
(input-parameters) => { statement; }

 ステートメント形式のラムダの本体は任意の数のステートメントで構成できますが、実際面では通常、2、3 個以下にします。  
  
[!code-csharp[StatementLambda#1](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLambda#2](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#2)]

 匿名メソッドと同様、ステートメント形式のラムダを使用して式ツリーを作成することはできません。  
  
## <a name="async-lambdas"></a>非同期ラムダ

 [async](../../../csharp/language-reference/keywords/async.md) キーワードと [await](../../../csharp/language-reference/keywords/await.md) キーワードを使用すると、非同期処理を組み込んだラムダ式およびステートメントを簡単に作成できます。 たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。  
  
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

 非同期ラムダを使用して、同じイベント ハンドラーを追加できます。 次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `async` 修飾子を追加します。  
  
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

 非同期メソッドの作成および使用方法の詳細については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」を参照してください。  
  
## <a name="lambdas-with-the-standard-query-operators"></a>標準クエリ演算子を使用したラムダ

 標準クエリ演算子の多くが、汎用デリゲートの <xref:System.Func%602> ファミリに属する型の入力パラメーターを持ちます。 これらのデリゲートは型パラメーターを使用して入力パラメーターの数と型、およびデリゲートの戻り値の型を定義します。 `Func` デリゲートは、ソース データのセット内の各要素に適用されるユーザー定義の式をカプセル化する場合に非常に便利です。 たとえば、次のデリゲート型を考えてみましょう。  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 このデリゲートを `Func<int,bool> myFunc` としてインスタンス化できます。 `int` は入力パラメーター、 `bool` は戻り値です。 戻り値は必ず最後の型パラメーターで指定されます。 `Func<int, string, bool>` は 2 つの入力パラメーター ( `int` と `string`) と戻り値の型 `bool`を持つデリゲートを定義しています。 次の `Func` デリゲートを呼び出すと、入力パラメーターが 5 に等しいかどうかを示す true または false が返されます。  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 たとえば System.Linq.Queryable で定義された標準クエリ演算子において、引数型が `Expression<Func>`の場合もラムダ式を使用できます。 `Expression<Func>` 引数を指定すると、ラムダは式ツリーにコンパイルされます。  
  
 標準クエリ演算子である <xref:System.Linq.Enumerable.Count%2A> メソッドを次に示します。  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 入力パラメーターの型はコンパイラが推論できますが、明示的に指定することもできます。 この特定のラムダ式は、2 で除算したときに剰余が 1 になる整数 (`n`) をカウントします。  
  
 次のメソッドは、配列 `numbers` 内で 9 より左側にある要素をすべて含むシーケンスを作成します。これは、9 がシーケンス内で条件を満たさない最初の数値であるためです。  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 次の例は、複数の入力パラメーターをかっこで囲んで指定する方法を示しています。 このメソッドは、値がその位置よりも小さい数値が出現するまで配列 numbers に含まれるすべての要素を返します。 ラムダ演算子 (`=>`) と以上演算子 (`>=`) を混同しないようにしてください。  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>ラムダにおける型の推論

 ラムダを記述する際、多くの場合は入力パラメーターの型を指定する必要はありません。これは、ラムダ本体やパラメーターのデリゲート型など C# 言語仕様に記述されている要素に基づいて、コンパイラが型を推論できるためです。 ほとんどの標準クエリ演算子では、最初の入力がソース シーケンス内の要素の型です。 したがって、 `IEnumerable<Customer>`を問い合わせると、入力変数は `Customer` オブジェクトであると推論されます。これは、そのメソッドとプロパティにアクセスできることを意味します。  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 ラムダの一般規則は、次のとおりです。  
  
-   ラムダにはデリゲート型と同じ数のパラメーターが含まれていなければなりません。  
  
-   ラムダに含まれる各入力パラメーターは、対応するデリゲート パラメーターに暗黙的に変換できなければなりません。  
  
-   ラムダの戻り値 (ある場合) は、デリゲートの戻り値の型に暗黙的に変換できなければなりません。  
  
 共通型システムには "ラムダ式" の概念が組み込まれていないため、ラムダ式自体は型を持ちません。 しかし、変則的ではあってもラムダ式の "型" を表現できると都合が良い場合もあります。 このような場合の型は、ラムダ式の変換後のデリゲート型または <xref:System.Linq.Expressions.Expression> 型を指します。  
  
## <a name="variable-scope-in-lambda-expressions"></a>ラムダ式における変数のスコープ

 ラムダは、"*外部変数*" を参照できます (「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照)。外部変数とは、ラムダ関数を定義するメソッド内のスコープ、またはラムダ式を含む型のスコープに存在する変数のことです。 こうして取り込まれた変数は、ラムダ式で使用するために格納されます。これは、変数がスコープ外に出てガベージ コレクトされる場合でも変わりません。 外部変数は、ラムダ式で使用される前に明示的に代入する必要があります。 次の例は、こうした規則を示しています。  
  
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
  
 ラムダ式における変数のスコープには、次の規則が適用されます。  
  
-   取り込まれた変数は、その変数を参照するデリゲートがガベージ コレクションの対象になるまでガベージ コレクトされません。  
  
-   ラムダ式内に導入された変数は、外側のメソッドでは参照できません。  
  
-   ラムダ式は、外側のメソッドの `in`、`ref`、`out` パラメーターを直接取り込むことはできません。  
  
-   ラムダ式に含まれる return ステートメントで外側のメソッドを戻すことはありません。  
  
-   ラムダ式には、 `goto` ステートメント、 `break` ステートメント、およびジャンプ ステートメントのジャンプ先がブロック外である場合はラムダ式の内部にある `continue` ステートメントを含めることはできません。 また、ジャンプ先がブロックの内部にある場合は、ラムダ式の外部でジャンプ ステートメントを使用するとエラーになります。  
  
## <a name="c-language-specification"></a>C# 言語仕様

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>参考書籍の該当する章

 「[Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)」(『[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)』)  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [統合言語クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [式ツリー](../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio 2008 C# Samples (Visual Studio 2008 の C# サンプル) (LINQ サンプル クエリ ファイルと XQuery プログラムを参照してください)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Recursive lambda expressions (再帰的なラムダ式)](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
