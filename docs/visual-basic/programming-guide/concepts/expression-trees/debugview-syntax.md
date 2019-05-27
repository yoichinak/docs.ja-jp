---
title: DebugView プロパティ (Visual Basic) で使用される構文
description: DebugView プロパティで式ツリーの文字列表現を生成するために使用される特別な構文について説明します
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196532"
---
# <a name="debugview-syntax"></a>`DebugView` の構文 

`DebugView` (デバッグ時にのみ使用可能な) プロパティを文字列に式ツリーの表示を提供します。 構文のほとんどは; を理解するとても簡単です。特殊なケースは、次のセクションで説明します。

それぞれの例の後に、コメント ブロックを含む、`DebugView`します。 

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> 変数名は、先頭に記号 "$" を付けて表示されます。

パラメーターに名前がない場合、`$var1` や `$var2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a>ConstantExpressions

整数値、文字列、および `null` を表す <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> オブジェクトの場合、定数の値が表示されます。

一部の数値型の値に、サフィックスが追加されます。

| 型 | キーワード | サフィックス |  
|--|--|--|
| <xref:System.UInt32> | [UInteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Long](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Double](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Single](../../../language-reference/data-types/single-data-type.md) | F | 
| <xref:System.Decimal> | [Decimal](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>使用例

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a>BlockExpression

場合の種類、<xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType>オブジェクトは、ブロックの最後の式の型とは異なる、山かっこ内で、型が表示されます (`<`と`>`)。 それ以外の場合、<xref:System.Linq.Expressions.BlockExpression> オブジェクトの型は表示されません。

### <a name="examples"></a>使用例

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object), 
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> オブジェクトは、デリゲート型と共に表示されます。

ラムダ式に名前がない場合、`#Lambda1` や `#Lambda2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a>LabelExpression

<xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> オブジェクトの既定値を指定した場合、その値が <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> オブジェクトの前に表示されます。

`.Label` トークンは、ラベルの開始を示します。 `.LabelTarget` トークンは、ジャンプ先のターゲットを示します。

ラベルに名前がない場合、`#Label1` や `#Label2` など、自動的に生成された名前が割り当てられます。

### <a name="examples"></a>使用例

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), 
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a>checked 演算子

Checked 演算子はと共に表示されます、`#`シンボル、演算子の前にします。 たとえば、checked 加算演算子は `#+` と表示されます。

### <a name="examples"></a>使用例

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```