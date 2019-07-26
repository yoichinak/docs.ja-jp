---
title: Object データ型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 1ac906494c49810e3d389591b1044f412e7320bc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513044"
---
# <a name="object-data-type"></a>Object データ型

オブジェクトを参照するアドレスを保持します。 任意の参照型 (文字列、配列、クラス、またはインターフェイス) を`Object`変数に割り当てることができます。 変数`Object`は、任意の値型 (numeric、 `Boolean`、 `Char` `Date`、、structure、または enumeration) のデータを参照することもできます。

## <a name="remarks"></a>Remarks

データ`Object`型は、アプリケーションで認識される任意のデータ型のデータを指すことができます。 コンパイル`Object`時に変数が指している可能性のあるデータ型を把握していない場合は、を使用します。

の`Object`既定値は`Nothing` 、(null 参照) です。

## <a name="data-types"></a>データの種類

任意のデータ型の変数、定数、または式を`Object`変数に割り当てることができます。 `Object`変数で現在参照されているデータ型を確認するには<xref:System.Type.GetTypeCode%2A> 、 <xref:System.Type?displayProperty=nameWithType>クラスのメソッドを使用します。 次に例を示します。

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

`Object`データ型は参照型です。 ただし、Visual Basic は、 `Object`値型のデータを参照するときに、変数を値型として扱います。

## <a name="storage"></a>記憶域

参照先のデータ型にかかわらず`Object` 、変数にはデータ値自体は含まれませんが、値へのポインターが含まれます。 コンピューターのメモリでは常に4バイトを使用しますが、変数の値を表すデータのストレージは含まれません。 ポインターを使用してデータを検索するコードがあるため`Object` 、値型を保持する変数は、明示的に型指定された変数よりもアクセスが多少遅くなります。

## <a name="programming-tips"></a>プログラミングのヒント

- **相互運用に関する考慮事項。** .NET Framework 用に作成されていないコンポーネント (オートメーションや COM オブジェクトなど) とやり取りする場合は、他の環境のポインター型が Visual Basic `Object`型と互換性がないことに注意してください。

- **パフォーマンス。** `Object`型を使用して宣言する変数は、任意のオブジェクトへの参照を格納するのに十分な柔軟性があります。 ただし、このような変数に対してメソッドまたはプロパティを呼び出すと、常に*遅延バインディング*(実行時) が発生します。 (コンパイル時に)*事前バインディング*を強制的に実行し、パフォーマンスを向上させるには、特定のクラス名を持つ変数を宣言するか、特定のデータ型にキャストします。

  オブジェクト変数を宣言するときは、汎用<xref:System.OperatingSystem> `Object`化された型ではなく、特定のクラス型を使用してみてください。 また、の<xref:System.Windows.Forms.Control>代わりに、使用可能な最も具体的な<xref:System.Windows.Forms.TextBox>クラスを使用して、そのプロパティとメソッドにアクセスできるようにする必要があります。 通常は、**オブジェクトブラウザー**の**クラス**の一覧を使用して、使用可能なクラス名を検索できます。

- **広げ.** すべてのデータ型とすべての参照型は`Object` 、データ型に拡大変換されます。 これは、エラーが`Object` <xref:System.OverflowException?displayProperty=nameWithType>発生することなく、任意の型をに変換できることを意味します。

  ただし、値型と`Object`の間で変換を行う場合、Visual Basic によって、*ボックス*化とボックス化*解除*と呼ばれる操作が実行され、実行速度が低下します。

- **文字を入力します。** `Object`にリテラルの型文字または識別子の型文字がありません。

- **フレームワークの種類。** .NET Framework 内の対応する型は<xref:System.Object?displayProperty=nameWithType>クラスです。

## <a name="example"></a>例

次の例は、 `Object`オブジェクトインスタンスを指す変数を示しています。

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>関連項目

- <xref:System.Object>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [方法: 2つのオブジェクトが関係しているかどうかを判断する](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [方法: 2つのオブジェクトが同一かどうかを判断する](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
