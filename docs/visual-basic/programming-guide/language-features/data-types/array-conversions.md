---
title: 配列の変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 88002e2c099ed9503beddb190d243aadcc1087fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830202"
---
# <a name="array-conversions-visual-basic"></a>配列の変換 (Visual Basic)
別の配列型に、配列型を変換するには、次の条件を満たす指定。  
  
-   **ランクが等しい。** 2 つの配列のランクは同じである必要があります、つまり、同じ次元数があります。 ただし、それぞれの次元の長さが同じである必要はありません。  
  
-   **要素のデータ型。** 両方の配列の要素のデータ型は、参照型である必要があります。 変換することはできません、`Integer`配列を`Long`配列、またはさらに、`Object`に少なくとも 1 つの値の型が関係するための配列。 詳細については、「 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
-   **でもです。** 2 つの配列の要素型の間で、拡張または縮小、変換できる必要があります。 この要件に失敗した例は、間の変換を実行しようとした、`String`とクラスの配列から派生した<xref:System.Attribute?displayProperty=nameWithType>します。 これら 2 つの型が共通の何もあるし、それらの間の任意の種類の変換は存在しません。  
  
 1 つの配列型の間の変換は拡大またはそれぞれの要素の変換を拡大または縮小するかどうかに応じて縮小します。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## <a name="conversion-to-an-object-array"></a>オブジェクトの配列への変換  
 宣言すると、`Object`初期化せず、要素の型の配列が`Object`は初期化されていない限り、します。 特定のクラスの配列に設定するとそのクラスの型にかかります。 ただし、基になる型は、まだ`Object`、関連付けられていないクラスの別の配列を後で設定できます。 すべてのクラスから派生するので`Object`、任意のクラスから、配列の要素の型を変更するには、他のクラス。  
  
 次の例では、変換が存在しない型の間で`student`と`String`から派生して両方`Object`ので、すべての割り当ては有効です。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>基になる配列の型  
 特定のクラスを使用して配列を宣言していた場合、基になる要素の種類はそのクラスです。 設定した場合、その後別のクラスの配列に、2 つのクラス間の変換が必要があります。  
  
 次の例では、`students`は、`student`配列。 間で変換が存在しないため`String`と`student`、最後のステートメントは失敗します。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [方法: オブジェクトを Visual Basic で別の型に変換します。](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
