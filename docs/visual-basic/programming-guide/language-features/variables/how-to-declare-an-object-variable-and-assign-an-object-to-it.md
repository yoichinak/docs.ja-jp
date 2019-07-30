---
title: '方法: オブジェクト変数を宣言し、その変数にオブジェクトを割り当てます Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630874"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>方法: オブジェクト変数を宣言し、その変数にオブジェクトを割り当てます Visual Basic

[オブジェクトデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)の変数を宣言するには、 `As Object` [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)でを指定します。 このような変数にオブジェクトを代入するには、代入ステートメントまたは初期化`=`句で等号 () の後にオブジェクトを配置します。

## <a name="example"></a>例

次の例では`Object` 、変数を宣言し、現在のインスタンスをその変数に代入します。

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

宣言の一部として変数を初期化することで、宣言と代入を組み合わせることができます。 次の例は、前の例と同じです。

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>コードのコンパイル

この例で必要な要素は次のとおりです。

- <xref:System> 名前空間への参照

- `Dim`ステートメントを配置するクラス、構造体、またはモジュール。

- 代入ステートメントを配置するプロシージャ。

## <a name="see-also"></a>関連項目

- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
