---
title: 式-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 1c79d4294ce1e7d6f6fc13e8220f88919c8f6021
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989747"
---
# <a name="expressions"></a>式
Windows Workflow Foundation (WF) 式は、結果を返す任意のアクティビティです。 すべての式アクティビティは、アクティビティの戻り値として <xref:System.Activities.Activity%601> という名前の <xref:System.Activities.OutArgument> プロパティを含む <xref:System.Activities.Activity%601.Result%2A> から間接的に派生します。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] には、幅広い式アクティビティが用意されています。式アクティビティは、演算子アクティビティを介して 1 つのワークフロー変数へアクセスできる <xref:System.Activities.Expressions.VariableValue%601> や <xref:System.Activities.Expressions.VariableReference%601> などの単純なアクティビティから、結果を生成するために Visual Basic 言語一式へアクセスできる <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> や <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> などの複雑なアクティビティまでさまざまです。 追加の式アクティビティは、<xref:System.Activities.CodeActivity%601> または <xref:System.Activities.NativeActivity%601> から派生して作成できます。  
  
## <a name="using-expressions"></a>式の使用  
 ワークフロー デザイナーでは、Visual Basic プロジェクトのすべての式に <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> および <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601>、C# ワークフロー プロジェクトの式に <xref:Microsoft.CSharp.Activities.CSharpValue%601> および <xref:Microsoft.CSharp.Activities.CSharpReference%601> を使用します。  
  
> [!NOTE]
> ワークフロープロジェクトC#での式のサポートは、.NET Framework 4.5 で導入されました。 詳細については、「 [ C#式](csharp-expressions.md)」を参照してください。  
  
 デザイナーによって生成されたワークフローは XAML に保存されます。XAML には、次の例のように、式が角かっこに囲まれて表示されます。  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 コードでワークフローを定義すると、任意の式アクティビティを使用できます。 次のコードは、3 つの数を追加する演算子アクティビティの使用例です。  
  
```csharp  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 C# のラムダ式を使用すると、次の例のように、同じワークフローをよりコンパクトに表現できます。  
  
```csharp  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 次の例のように、Visual Basic の式アクティビティを使用してワークフローを表現することもできます。  
  
```vb  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>カスタム式アクティビティによる使用可能な式の拡張  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] の式には、追加の式アクティビティを作成できる拡張性があります。 次のコードは、3 つの整数値の合計を返すアクティビティの例です。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 次の例のように、この新しいアクティビティを使用して、3 つの値を追加した前のワークフローを書き直すことができます。  
  
```csharp  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 コードで式を使用する方法の詳細については、「[命令型コードを使用したワークフロー、アクティビティ、および式の作成](authoring-workflows-activities-and-expressions-using-imperative-code.md)」を参照してください。
