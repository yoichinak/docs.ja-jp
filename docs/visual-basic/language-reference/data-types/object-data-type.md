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
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751677"
---
# <a name="object-data-type"></a>Object データ型
オブジェクトを参照するアドレスを保持します。 参照型 (文字列、配列、クラス、またはインターフェイス) を割り当てることができます、`Object`変数。 `Object`変数は、任意の値型のデータを指すことも (数値、 `Boolean`、 `Char`、 `Date`、構造体、または列挙型)。  
  
## <a name="remarks"></a>Remarks  
 `Object`データ型は、アプリケーションが認識済みのオブジェクト インスタンスを含む、任意のデータ型のデータを指すことができます。 使用`Object`コンパイル時にわからない場合をポイントする変数がどのようなデータ型します。  
  
 既定値`Object`は`Nothing`(null 参照)。  
  
## <a name="data-types"></a>データの種類  
 変数、定数、またはに任意のデータ型の式を割り当てることができます、`Object`変数。 データ型を決定する、`Object`変数を現在参照して、使用することができます、<xref:System.Type.GetTypeCode%2A>のメソッド、<xref:System.Type?displayProperty=nameWithType>クラス。 次に例を示します。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object`データ型が参照型。 ただし、Visual Basic の処理、`Object`変数に値型のデータを参照する場合、値型。  
  
## <a name="storage"></a>記憶域  
 参照するすべてのデータ型、`Object`自体が、値へのポインターではなく、変数がデータ値を含んでいません。 コンピューターのメモリ内で常に 4 バイトを使用しますが、これは、変数の値を表すデータのストレージには含まれません。 ポインターを使用して、データを検索するコードのため`Object`値の型を保持する変数より明示的に型指定された変数へのアクセスをわずかに遅くなります。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
- **相互運用の考慮事項。** オートメーションまたは COM オブジェクトのように、.NET Framework 用に作成されていないコンポーネントとやり取りする場合は、他の環境でのポインター型が、Visual Basic と互換性がないことに留意してください`Object`型。  
  
- **パフォーマンス。** 使用して宣言する変数、`Object`型は柔軟なので、任意のオブジェクトへの参照が含まれます。 ただし、メソッドまたはプロパティをこのような変数を呼び出すと常に発生*遅延バインディング*(実行時)。 強制的に*事前バインディング*(コンパイル時) より高いパフォーマンスと、特定のクラスの名前を持つ変数を宣言または特定のデータ型にキャストします。  
  
     オブジェクト変数を宣言するときに、特定のクラス型を使用して、たとえばしよう<xref:System.OperatingSystem>ではなく、汎用化された`Object`型。 などに使用できる、最も具体的なクラスを使用することも必要があります。<xref:System.Windows.Forms.TextBox>の代わりに<xref:System.Windows.Forms.Control>、そのプロパティとメソッドにアクセスできるようにします。 通常使用することができます、**クラス**の一覧で、**オブジェクト ブラウザー**利用可能なクラス名を検索します。  
  
- **拡大します。** すべてのデータ型とすべての参照型に変換、`Object`データ型。 つまり、任意の種類を変換する`Object`遭遇することがなく、<xref:System.OverflowException?displayProperty=nameWithType>エラー。  
  
     ただし、値型の間で変換する場合と`Object`、という操作を実行する Visual Basic*ボックス化*と*ボックス化解除*、実行速度が低下することをします。  
  
- **型宣言文字。** `Object` リテラルの型文字または識別子の型文字がありません。  
  
- **フレームワークの型。** .NET Framework に対応する型は、<xref:System.Object?displayProperty=nameWithType>クラス。  
  
## <a name="example"></a>例  
 次の例を示しています、`Object`オブジェクトのインスタンスを指す変数。  
  
```  
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
- [方法: 2 つのオブジェクトが関連するかどうかを判断します。](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [方法: 2 つのオブジェクトが同一かどうかを判断します。](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
