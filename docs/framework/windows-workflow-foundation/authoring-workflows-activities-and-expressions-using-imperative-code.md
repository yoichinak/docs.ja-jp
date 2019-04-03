---
title: 命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 1a11da9ce3dd73f0bc2851b68e7c354e55c9d2d3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708367"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法
ワークフロー定義は、構成済みのアクティビティ オブジェクトのツリーです。 このアクティビティ ツリーは、手動で XAML を編集したり、ワークフロー デザイナーを使用して XAML を生成したりするなど、多くの方法で定義することができます。 ただし、XAML の使用は必須ではありません。 ワークフロー定義は、プログラムで作成することもできます。 このトピックでは、コードを使用したワークフローの定義、アクティビティ、および式の作成の概要について説明します。 コードを使用して XAML ワークフローを使用した作業の例については、[ワークフローのシリアル化と XAML との間のアクティビティ](serializing-workflows-and-activities-to-and-from-xaml.md)を参照してください。  
  
## <a name="creating-workflow-definitions"></a>ワークフロー定義の作成  
 アクティビティ型のインスタンスをインスタンス化して、アクティビティ オブジェクトのプロパティを構成することで、ワークフロー定義を作成できます。 子アクティビティを含まないアクティビティの場合、数行のコードを使用してこれを作成できます。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  このトピックの例では、<xref:System.Activities.WorkflowInvoker> を使用してサンプル ワークフローを実行します。 ワークフローの呼び出し、引数の受け渡し、および利用できるさまざまなホストの選択の詳細については、[を使用して WorkflowInvoker と WorkflowApplication](using-workflowinvoker-and-workflowapplication.md)を参照してください。  
  
 次の例では、1 つの <xref:System.Activities.Statements.WriteLine> アクティビティから成るワークフローを作成します。 <xref:System.Activities.Statements.WriteLine> アクティビティの <xref:System.Activities.Statements.WriteLine.Text%2A> 引数が設定され、ワークフローが呼び出されます。 アクティビティに子アクティビティが含まれる場合も、作成のメソッドは同じです。 次の例では、2 つの <xref:System.Activities.Statements.Sequence> アクティビティを含む <xref:System.Activities.Statements.WriteLine> アクティビティを使用します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>オブジェクト初期化子の使用  
 このトピックの例では、オブジェクトの初期化の構文を使用します。 オブジェクトの初期化の構文は、コードでワークフロー定義を作成する場合に便利な方法です。これは、ワークフローのアクティビティの階層ビューが提供され、アクティビティ間の関係が示されるためです。 プログラムからワークフローを作成する場合に、オブジェクトの初期化の構文を使用しなければならないという要件はありません。 次の例は、機能的には前のサンプルと同じです。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 オブジェクト初期化子の詳細については、[方法。コンス トラクターを呼び出さずにオブジェクトを初期化 (C#プログラミング ガイド)](https://go.microsoft.com/fwlink/?LinkId=161015)と[方法。オブジェクト初期化子を使用してオブジェクトを宣言](https://go.microsoft.com/fwlink/?LinkId=161016)を参照してください。  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>変数、リテラル値、および式の使用  
 コードを使用してワークフロー定義を作成する場合は、ワークフロー定義の作成の一部としてコードが実行する内容、およびそのワークフローのインスタンスの実行の一部としてコードが実行する内容に注意してください。 たとえば、次のワークフローはランダムな数値を生成し、それをコンソールに出力します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 このワークフロー定義のコードが実行されると、`Random.Next` への呼び出しが実行され、その結果がリテラル値としてワークフロー定義に保存されます。 このワークフローの多くのインスタンスを呼び出すことができ、そのすべてに同じ数字が表示されます。 ワークフローの実行中にランダムな数値を生成するには、ワークフローを実行するたびに評価する式を使用する必要があります。 次の例では、<xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> で Visual Basic 式を使用します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 前の例にある式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> と C# 式を使用して実装することもできます。  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C# 式は、その式を含むワークフローが呼び出される前にコンパイルする必要があります。 場合、C#式がコンパイルされない、 <xref:System.NotSupportedException> 、次のようなメッセージでワークフローが呼び出される場合にスローされます。`Expression Activity type 'CSharpValue`1' を実行するためにコンパイルが必要です。  ワークフローがコンパイルされていることを確認してください。 ' Visual Studio は、c# で作成されたワークフローに関連するほとんどのシナリオで式は、自動的にコンパイルされますが、コード ワークフローなど、一部のシナリオで c# 式は、手動でコンパイルします。 C# の式をコンパイルする方法の例は、次を参照してください。、[コード ワークフローで c# を使用した式](csharp-expressions.md#CodeWorkflows)のセクション、 [C# 式](csharp-expressions.md)トピック。  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> は式の右辺値として使用できる Visual Basic 構文の式を表し、<xref:Microsoft.CSharp.Activities.CSharpValue%601> は式の右辺値として使用できる C# 構文の式を表します。 これらの式は、含まれるアクティビティが実行されるたびに評価されます。 式の結果はワークフローの変数 `n` に代入され、これらの結果はワークフローの次のアクティビティによって使用されます。 実行時にワークフローの変数 `n` の値にアクセスするには、<xref:System.Activities.ActivityContext> が必要です。 次のようなラムダ式を使用するとアクセスできます。  
  
> [!NOTE]
>  この 2 つのコードはプログラミング言語として C# を使用している例ですが、1 つは <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用し、もう 1 つは <xref:Microsoft.CSharp.Activities.CSharpValue%601> を使用しています。 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> および <xref:Microsoft.CSharp.Activities.CSharpValue%601> は、Visual Basic と C# の両方のプロジェクトで使用できます。 既定では、ワークフロー デザイナーで作成された式は、ホスティング プロジェクトの言語に一致します。 ワークフローをコードで作成する場合、必要な言語はワークフロー作成者の判断に委ねられます。  
  
 これらの例では、式の結果がワークフロー変数 `n` に代入され、その結果がワークフロー内の次のアクティビティで使用されます。 実行時にワークフローの変数 `n` の値にアクセスするには、<xref:System.Activities.ActivityContext> が必要です。 次のようなラムダ式を使用するとアクセスできます。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 ラムダ式の詳細については、[ラムダ式 (c# プログラミング ガイド)](https://go.microsoft.com/fwlink/?LinkID=152436)または[ラムダ式 (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437)を参照してください。  
  
 ラムダ式は XAML 形式にシリアル化できません。 ラムダ式を使用して、ワークフローのシリアル化が行われた場合、<xref:System.Activities.Expressions.LambdaSerializationException>で、次のメッセージがスローされます。"このワークフローには、コードで指定されたラムダ式が含まれています。 これらの式は XAML にシリアル化できません。 このワークフローを XAML にシリアル化できるようにするには、VisualBasicValue/VisualBasicReference を使用するか、ExpressionServices.Convert(lambda) を使用します。 これにより、ラムダ式が式アクティビティに変換されます。" というメッセージが表示されます。 この式に XAML との互換性を持たせるには、次の例に示すように <xref:System.Activities.Expressions.ExpressionServices> および <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> を使用します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用することもできます。 Visual Basic 式を使用する場合はラムダ式が不要であることに注意してください。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 実行時に、Visual Basic 式は LINQ 式にコンパイルされます。 前の例はいずれも XAML にシリアル化できますが、シリアル化された XAML をワークフロー デザイナーで表示および編集することを目的としている場合は、式に <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用してください。 `ExpressionServices.Convert` を使用するシリアル化されたワークフローはデザイナーで開くことができますが、式の値は空白になります。 XAML のワークフローをシリアル化の詳細については、次を参照してください。[ワークフローのシリアル化と XAML との間のアクティビティ](serializing-workflows-and-activities-to-and-from-xaml.md)します。  
  
#### <a name="literal-expressions-and-reference-types"></a>リテラル式と参照型  
 リテラル式は、ワークフロー内では <xref:System.Activities.Expressions.Literal%601> アクティビティによって表されます。 次の <xref:System.Activities.Statements.WriteLine> アクティビティは機能的には同じです。  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 <xref:System.String> 以外の参照型を使用してリテラル式を初期化することはできません。 次の例では、<xref:System.Activities.Statements.Assign> アクティビティの <xref:System.Activities.Statements.Assign.Value%2A> プロパティは `List<string>` を使用したリテラル式で初期化されます。  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 このアクティビティを含むワークフローが検証されると、次の検証エラーが返されます。"リテラル サポート値型と変更不可の型 System.String のみです。 型 System.Collections.Generic.List`1[System.String] はリテラルとして使用できません。" という検証エラーが返されます。 ワークフローが呼び出されると、検証エラーのテキストを含む <xref:System.Activities.InvalidWorkflowException> がスローされます。 参照型のリテラル式を作成しても、ワークフローの各インスタンスに対して参照型の新しいインスタンスが作成されないため、これは検証エラーとなります。 このエラーを解決するには、リテラル式を、参照型の新しいインスタンスを作成して返すリテラル式に置き換えます。  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 式の詳細については、[式](expressions.md)を参照してください。  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>式と InvokeMethod アクティビティを使用したオブジェクトのメソッド呼び出し  
 <xref:System.Activities.Expressions.InvokeMethod%601> アクティビティを使用すると、.NET Framework のクラスの静的メソッドとインスタンス メソッドを呼び出すことができます。 このトピックの前の例では、乱数が <xref:System.Random> クラスを使用して生成されました。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 また <xref:System.Activities.Expressions.InvokeMethod%601> アクティビティは、<xref:System.Random.Next%2A> クラスの <xref:System.Random> メソッドの呼び出しにも使用されました。  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =   
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 <xref:System.Random.Next%2A> は静的メソッドではないので、<xref:System.Random> プロパティには <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> クラスのインスタンスが指定されます。 この例では、新しいインスタンスが Visual Basic 式を使用して作成されますが、これまでも作成されてワークフロー変数に格納されている場合があります。 この例では、<xref:System.Activities.Statements.Assign%601> アクティビティの代わりに、<xref:System.Activities.Expressions.InvokeMethod%601> アクティビティをより簡単に使用しています。 <xref:System.Activities.Statements.Assign%601> アクティビティまたは <xref:System.Activities.Expressions.InvokeMethod%601> アクティビティで最終的に呼び出されるメソッド呼び出しが長時間実行されている場合、<xref:System.Activities.Expressions.InvokeMethod%601> には <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> プロパティがあるため、効果があります。 このプロパティが `true` に設定されると、呼び出されるメソッドはワークフローに対して非同期に実行されます。 他のアクティビティが並列実行される場合、そのメソッドは非同期に実行され、それらのアクティビティはブロックされません。 また、呼び出すメソッドに戻り値がない場合、<xref:System.Activities.Expressions.InvokeMethod%601> はメソッドを呼び出すための適切な手段となります。  
  
## <a name="arguments-and-dynamic-activities"></a>引数と動的なアクティビティ  
 アクティビティをアクティビティ ツリーにまとめてプロパティと引数を構成すると、コードでワークフロー定義を作成できます。 既存の引数を見つけることはできますが、新しい引数をアクティビティに追加することはできません。 これには、ルート アクティビティに渡されるワークフロー引数が含まれます。 ワークフロー引数は、命令型コードでは新しい CLR 型のプロパティとして指定され、XAML では `x:Class` および `x:Member` を使用して宣言されます。 ワークフロー定義がメモリ内オブジェクトのツリーとして作成された場合は新しい CRL 型が作成されないため、引数を追加できません。 ただし、<xref:System.Activities.DynamicActivity> に引数を追加することはできます。 次の例では、2 つの整数の引数を取り、それを一緒に追加して結果を返す <xref:System.Activities.DynamicActivity%601> を作成します。 各引数に対して <xref:System.Activities.DynamicActivityProperty> が作成され、操作の結果が <xref:System.Activities.DynamicActivity%601> の <xref:System.Activities.Activity%601.Result%2A> 引数に代入されます。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 動的アクティビティの詳細については、[実行時にアクティビティを作成する](creating-an-activity-at-runtime-with-dynamicactivity.md)を参照してください。  
  
## <a name="compiled-activities"></a>コンパイルされたアクティビティ  
 動的アクティビティは、コードを使用して引数を格納するアクティビティを定義するための 1 つの方法ですが、アクティビティをコードで作成して型にコンパイルすることもできます。 <xref:System.Activities.CodeActivity> から派生する単純なアクティビティと、<xref:System.Activities.AsyncCodeActivity> から派生する非同期アクティビティを作成できます。 これらのアクティビティは、引数を保持し、値を返して、命令型コードを使用してロジックを定義できます。 これらの種類のアクティビティを作成する例については、[CodeActivity 基本クラス](workflow-activity-authoring-using-the-codeactivity-class.md)と[非同期アクティビティを作成する](creating-asynchronous-activities-in-wf.md)を参照してください。  
  
 <xref:System.Activities.NativeActivity> から派生するアクティビティは、命令型コードを使用してロジックを定義できるだけでなく、ロジックを定義する子アクティビティを含むこともできます。 これらのアクティビティは、ブックマークの作成など、ランタイムの機能をすべて利用できます。 作成の例については、 <xref:System.Activities.NativeActivity>-ベースのアクティビティを参照してください[NativeActivity の基本クラス](nativeactivity-base-class.md)、[方法。アクティビティ作成](how-to-create-an-activity.md)、および[Native Activity を使用してカスタム複合](./samples/custom-composite-using-native-activity.md)サンプル。  
  
 <xref:System.Activities.Activity> から派生するアクティビティは、子アクティビティを使用してロジックだけを定義します。 これらのアクティビティは、通常、ワークフロー デザイナーを使用して作成されますが、コードを使用して定義することもできます。 次の例では、`Square` から派生する `Activity<int>` アクティビティが定義されます。 `Square` アクティビティには <xref:System.Activities.InArgument%601> という名前の 1 つの `Value` があり、そのロジックが <xref:System.Activities.Statements.Sequence> プロパティを使用して <xref:System.Activities.Activity.Implementation%2A> アクティビティを指定してロジックを定義します。 <xref:System.Activities.Statements.Sequence> アクティビティには、<xref:System.Activities.Statements.WriteLine> アクティビティと <xref:System.Activities.Statements.Assign%601> アクティビティが含まれています。 この 3 つのアクティビティは、`Square` アクティビティのロジックを実装します。  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 次の例では、単一の `Square` アクティビティで構成されるワークフロー定義を <xref:System.Activities.WorkflowInvoker> を使用して呼び出します。  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 このワークフローが呼び出されると、次の出力がコンソールに表示されます。  
  
 **値を 2 乗。5**  
**結果:25**
