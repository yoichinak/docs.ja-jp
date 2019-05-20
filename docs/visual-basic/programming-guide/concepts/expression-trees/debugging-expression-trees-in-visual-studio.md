---
title: Visual Studio (Visual Basic) で式ツリーのデバッグ
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879822"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio (Visual Basic) で式ツリーのデバッグ
アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。 式ツリーの構造体の簡単な概要を取得するには、使用することができます、`DebugView`プロパティを説明する特殊な構文を使用して式ツリーを表す[下](#debugview-syntax)します。 (なお`DebugView`デバッグ モードでのみ使用できます)。  

![Visual Studio デバッガー内で式ツリーの DebugView](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

`DebugView`文字列で、使用することができます、[組み込みテキスト ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)複数の行を選択して表示する**テキスト ビジュアライザー**隣にある虫眼鏡アイコンから、 `DebugView`ラベル。

 !['DebugView' の結果に適用されるテキスト ビジュアライザー](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

インストールして使用する代わりに、[カスタム ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)式ツリー。

* [読み取り可能な式](https://github.com/agileobjects/ReadableExpressions)([MIT ライセンス](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)で使用可能な[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers))、として式ツリーを表示します。C#コード。

  ![読み取り可能な式のビジュアライザー](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [式ツリーのビジュアライザー](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT ライセンス](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) を式ツリー、そのプロパティ、および関連するオブジェクトのグラフィカル ビューを提供し、Visual Basic コードを使用して式ツリーを表示することができます。

  ![ExpressionToString ビジュアライザー](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>式ツリーのビジュアライザーを開くには  
  
1. 式ツリーの横に表示される、虫眼鏡アイコンをクリックします**データヒント**、**ウォッチ**ウィンドウで、 **[自動変数]** ウィンドウで、または **[ローカル]。** ウィンドウ。  
  
     使用可能なビジュアライザーの一覧が表示されます。 

      ![Visual Studio からビジュアライザーを開く](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. 使用するビジュアライザーをクリックします。  

## <a name="debugview-syntax"></a>`DebugView` 構文 

それぞれの式の型は、以下のセクションで説明するように、ビジュアライザーに表示されます。

## <a name="parameterexpressions"></a>ParameterExpressions

<xref:System.Linq.Expressions.ParameterExpression> 変数名は、先頭に記号 "$" を付けて表示されます。

パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    `DebugView` プロパティ

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    `DebugView` プロパティ

    `$var1`

## <a name="constantexpressions"></a>ConstantExpressions
 整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression> オブジェクトの場合、定数の値が表示されます。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` プロパティ

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    `DebugView` プロパティ

    10D

## <a name="blockexpression"></a>BlockExpression

<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型が、ブロック内の最後の式の型と異なる場合、その型が `DebugInfo` プロパティに山かっこ (\< および >) で囲まれて表示されます。 それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    `DebugView` プロパティ

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    `DebugView` プロパティ

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> オブジェクトは、デリゲート型と共に表示されます。

ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    `DebugView` プロパティ

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    `DebugView` プロパティ

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

<xref:System.Linq.Expressions.LabelExpression> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget> オブジェクトの前に表示されます。

`.Label` トークンは、ラベルの開始を示します。 `.LabelTarget` トークンは、ジャンプ先のターゲットを示します。

ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    `DebugView` プロパティ

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    `DebugView` プロパティ

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>checked 演算子

checked 演算子は、演算子の前に "#" 記号が付く形式で表示されます。 たとえば、checked 加算演算子は `#+` と表示されます。

### <a name="examples"></a>使用例

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    `DebugView` プロパティ

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    `DebugView` プロパティ

    `#(System.Int32)10D`

## <a name="see-also"></a>関連項目

- [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)
- [カスタム ビジュアライザーを作成する](/visualstudio/debugger/create-custom-visualizers-of-data)
