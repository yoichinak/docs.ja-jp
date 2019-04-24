---
title: 配列のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 2b051d22fe3d331626f2e181c008043e576b7526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833374"
---
# <a name="troubleshooting-arrays-visual-basic"></a>配列のトラブルシューティング (Visual Basic)
このページには、配列を使用する場合に発生する可能性がある一般的な問題が一覧表示されます。  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>コンパイル エラーを宣言して、配列の初期化  
 宣言、作成、および配列の初期化の規則の誤解からコンパイル エラーが発生します。 エラーの最も一般的な原因は次のとおりです。  
  
-   指定する、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)配列変数の宣言に次元の長さを指定した後の句。 次のコード行では、この型の無効な宣言を表示します。  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   ジャグ配列の最上位の配列の次元の長さを指定します。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   省略すると、`New`キーワード要素の値を指定する場合。 次のコード行は、この型の無効な宣言を示しています。  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   指定する、`New`中かっこのない句 (`{}`)。 次のコード行では、この型の無効な宣言を表示します。  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>範囲外の配列へのアクセス  
 配列の初期化中のプロセスは、各ディメンションを上限と下限の境界を割り当てます。 配列の要素へのすべてのアクセスには、有効なインデックス、またはすべてのディメンションの添字を指定します。 任意のインデックスが、上限の上または下の下限の境界の場合、<xref:System.IndexOutOfRangeException>例外が発生します。 コンパイラは、実行時にエラーが発生したため、このようなエラーを検出できません。  
  
### <a name="determining-bounds"></a>範囲の確認  
 場合は、コードに別のコンポーネントが配列を渡すと、たとえば、プロシージャの引数としてわからないその配列のサイズまたはその次元の長さ。 任意の要素にアクセスしようとする前に常に配列のすべての次元の上限の境界を決定する必要があります。 Visual Basic 以外の手段で配列が作成された場合`New`句では、下限の境界では、0 でない可能性がありもその下限の境界を決定するおくと安心になります。  
  
### <a name="specifying-the-dimension"></a>ディメンションを指定します。  
 多次元配列の境界を決定する際に注意して、ディメンションを指定する方法。 `dimension`のパラメーター、<xref:System.Array.GetLowerBound%2A>と<xref:System.Array.GetUpperBound%2A>メソッドは、中に、0 から始まる、 `Rank` Visual Basic のパラメーター<xref:Microsoft.VisualBasic.Information.LBound%2A>と<xref:Microsoft.VisualBasic.Information.UBound%2A>関数は、1 から始まります。  
  
## <a name="see-also"></a>関連項目

- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [方法: Visual Basic で配列変数を初期化します。](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
