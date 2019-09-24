---
title: '方法: プロシージャを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216724"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>方法: プロシージャを作成する (Visual Basic)

開始`Sub`宣言ステートメント (または`Function`) と終了宣言ステートメント (`End Sub`または`End Function`) の間でプロシージャを囲みます。 すべてのプロシージャのコードは、これらのステートメントの間にあります。

 プロシージャに別のプロシージャを含めることはできません。そのため、プロシージャの開始と終了のステートメントを他のプロシージャの外側に指定する必要があります。

 異なる場所で同じタスクを実行するコードがある場合は、そのタスクを1回のプロシージャとして記述し、コード内のさまざまな場所から呼び出すことができます。

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>値を返さないプロシージャを作成するには

1. 他のプロシージャの外部では`Sub` 、ステートメント`End Sub`とステートメントを使用します。

2. ステートメントで、 `Sub`キーワードに続けてプロシージャの名前を指定し、その後にパラメーターリストをかっこで囲んで指定します。 `Sub`

3. プロシージャのコードステートメントをステートメント`Sub`と`End Sub`ステートメントの間に配置します。

### <a name="to-create-a-procedure-that-returns-a-value"></a>値を返すプロシージャを作成するには

1. 他のプロシージャの外部では`Function` 、ステートメント`End Function`とステートメントを使用します。

2. ステートメントで、 `Function`キーワードに続けてプロシージャの名前を指定し、次に`As`かっこで囲んだパラメーターリストを指定し、次に戻り値のデータ型を指定する句を指定します。 `Function`

3. プロシージャのコードステートメントをステートメント`Function`と`End Function`ステートメントの間に配置します。

4. ステートメントを`Return`使用して、呼び出し元のコードに値を返します。

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>新しいプロシージャを古い繰り返しのコードブロックに接続するには

1. 古いコードがアクセスできる場所に新しいプロシージャを定義していることを確認します。

2. 繰り返し実行されるコードブロックで、反復するタスクを実行するステートメントを、 `Sub`または`Function`プロシージャを呼び出す1つのステートメントに置き換えます。

3. プロシージャが値を返す`Function`である場合は、呼び出し元のステートメントが戻り値を持つアクション (変数に格納するなど) を実行していることを確認してください。そうでない場合、値は失われます。

## <a name="example"></a>例

 次`Function`の手順では、直角三角形の最長の辺 (斜辺) を計算します。これは、他の2つの辺の値を指定したものです。

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>関連項目

- [手順](index.md)
- [Sub プロシージャ](sub-procedures.md)
- [Function プロシージャ](function-procedures.md)
- [Property プロシージャ](property-procedures.md)
- [演算子プロシージャ](operator-procedures.md)
- [プロシージャのパラメーターと引数](procedure-parameters-and-arguments.md)
- [再帰プロシージャ](recursive-procedures.md)
- [プロシージャのオーバーロード](procedure-overloading.md)
- [クラスとオブジェクト](../objects-and-classes/index.md)
- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
