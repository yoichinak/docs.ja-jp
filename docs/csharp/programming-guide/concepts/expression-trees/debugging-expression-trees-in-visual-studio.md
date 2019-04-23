---
title: 式ツリーのデバッグ (Visual Studio) (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330410"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>式ツリーのデバッグ (Visual Studio) (C#)
アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。 式ツリーの構造を簡単に確認する場合は、`DebugView` プロパティを使用できます。このプロパティは、デバッグ モードでのみ使用できます。 デバッグの詳細については、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」を参照してください。  
  
 式ツリーの内容をわかりやすく表すために、`DebugView` プロパティでは Visual Studio ビジュアライザーを使用します。 詳細については、「[Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data)」 (カスタム ビジュアライザーを作成する) を参照してください。  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>式ツリーのビジュアライザーを開くには  
  
1. **[データヒント]**、**[ウォッチ]** ウィンドウ、**[自動変数]** ウィンドウ、または **[ローカル]** ウィンドウで、式ツリーの `DebugView` プロパティの横に表示されている虫眼鏡のアイコンをクリックします。  
  
     ビジュアライザーの一覧が表示されます。  
  
2. 使用するビジュアライザーをクリックします。  
  
 それぞれの式の型は、以下のセクションで説明するように、ビジュアライザーに表示されます。  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> 変数名は、先頭に記号 "$" を付けて表示されます。  
  
 パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression> オブジェクトの場合、定数の値が表示されます。  
  
 C# リテラルとしての標準のサフィックスを持つ数値型の場合、サフィックスが値に追加されます。 さまざまな数値型に関連するサフィックスを次の表に示します。  
  
|型|サフィックス|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 <xref:System.Linq.Expressions.BlockExpression> オブジェクトの型が、ブロック内の最後の式の型と異なる場合、その型が `DebugInfo` プロパティに山かっこ (\< および >) で囲まれて表示されます。 それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> オブジェクトは、デリゲート型と共に表示されます。  
  
 ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 <xref:System.Linq.Expressions.LabelExpression> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget> オブジェクトの前に表示されます。  
  
 `.Label` トークンは、ラベルの開始を示します。 `.LabelTarget` トークンは、ジャンプ先のターゲットを示します。  
  
 ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>checked 演算子  
 checked 演算子は、演算子の前に "#" 記号が付く形式で表示されます。 たとえば、checked 加算演算子は `#+` と表示されます。  
  
### <a name="examples"></a>使用例  
  
|正規表現|`DebugView` プロパティ|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>関連項目

- [式ツリー (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)
- [カスタム ビジュアライザーを作成する](/visualstudio/debugger/create-custom-visualizers-of-data)
