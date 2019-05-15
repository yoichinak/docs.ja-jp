---
title: '方法: 式ツリーを実行する (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 034a391a21e685a6ceb8342bb1738ff34381cebb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598041"
---
# <a name="how-to-execute-expression-trees-c"></a>方法: 式ツリーを実行する (C#)
このトピックでは、式ツリーを実行する方法について説明します。 式ツリーを実行すると値が返される場合がありますが、メソッドの呼び出しなどの処理が実行されるだけの場合もあります。  
  
 実行できるのは、ラムダ式を表す式ツリーのみです。 ラムダ式を表す式ツリーの型は、<xref:System.Linq.Expressions.LambdaExpression> または <xref:System.Linq.Expressions.Expression%601> です。 このような式ツリーを実行するには、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A> メソッドを呼び出して実行可能なデリゲートを作成した後、そのデリゲートを呼び出します。  
  
> [!NOTE]
>  デリゲートの型が不明な場合、つまり、ラムダ式が <xref:System.Linq.Expressions.LambdaExpression> 型であり <xref:System.Linq.Expressions.Expression%601> 型ではない場合には、デリゲートを直接呼び出さずに、デリゲートに対して <xref:System.Delegate.DynamicInvoke%2A> メソッドを呼び出す必要があります。  
  
 式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> メソッドを呼び出すことで、元の式ツリーを本体に含む新しいラムダ式を作成できます。 その後、このセクションの説明のとおりにラムダ式を実行できます。  
  
## <a name="example"></a>例  
 次のコード例は、ラムダ式を作成して実行することで数値の累乗を表す式ツリーの実行方法を示しています。 このコードを実行すると、累乗された数値を表す結果が表示されます。  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- System.Core.dll がまだ参照されていない場合は、System.Core.dll へのプロジェクト参照を追加します。  
  
- System.Linq.Expressions 名前空間をインクルードします。  
  
## <a name="see-also"></a>関連項目

- [式ツリー (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [方法: 式ツリーを変更する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
