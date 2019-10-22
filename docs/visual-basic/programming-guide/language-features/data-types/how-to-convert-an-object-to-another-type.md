---
title: '方法: Visual Basic でオブジェクトを別の型に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 39083fc55d30e24c357ec162a15466f81655f4c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582325"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>方法: Visual Basic でオブジェクトを別の型に変換する
`Object` 変数を別のデータ型に変換するには、 [CType 関数 (Visual Basic)](../../../../visual-basic/language-reference/functions/ctype-function.md)などの変換キーワードを使用します。  
  
## <a name="example"></a>例  
 次の例では、`Object` 変数を `Integer` と `String` に変換します。  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 @No__t_0 変数の内容が特定のデータ型であることがわかっている場合は、変数をそのデータ型に変換することをお勧めします。 @No__t_0 変数を引き続き使用する場合は、*ボックス*化とボックス化*解除*(値型の場合) または*遅延バインディング*(参照型の場合) のいずれかが発生します。 これらの操作はすべて、追加の実行時間がかかり、パフォーマンスが低下します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- <xref:System?displayProperty=nameWithType> 名前空間への参照  
  
## <a name="see-also"></a>関連項目

- <xref:System.Object>
- [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
