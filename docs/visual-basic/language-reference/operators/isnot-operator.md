---
title: IsNot 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331632"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 演算子 (Visual Basic)
2つのオブジェクト参照変数を比較します。

## <a name="syntax"></a>構文

```vb
result = object1 IsNot object2
```

## <a name="parts"></a>指定項目
 `result` 必須。 `Boolean` 値。

 `object1` 必須。 @No__t 0 の変数または式。

 `object2` 必須。 @No__t 0 の変数または式。

## <a name="remarks"></a>コメント
 @No__t-0 演算子は、2つのオブジェクト参照が異なるオブジェクトを参照するかどうかを判断します。 ただし、値の比較は実行されません。 @No__t-0 および `object2` がまったく同じオブジェクトインスタンスを参照している場合、`result` は `False` です。そうでない場合、`result` は `True` になります。

 `IsNot` は、`Is` 演算子の逆です。 @No__t-0 の利点は、`Not` と `Is` を使用して、読みにくい構文を避けることができることです。

 @No__t-0 および `IsNot` 演算子を使用すると、事前バインディングオブジェクトと遅延バインディングオブジェクトの両方をテストできます。

## <a name="example"></a>例
 次のコード例では、`Is` 演算子と `IsNot` 演算子の両方を使用して、同じ比較を実行します。

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a>関連項目

- [Is 演算子](is-operator.md)
- [TypeOf 演算子](typeof-operator.md)
- [Visual Basic における演算子の優先順位](operator-precedence.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
