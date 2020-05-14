---
title: 型が、'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、型 '<typename>' の 'For Each' は不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: bdfb6e9b1332db1f049bb2575e97215026efe0dd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591759"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>型 '\<typename>' の 'For Each' は、型が 'System.Collections.Generic.IEnumerable(Of T)' の複数のインスタンス生成を実装するため、不適切です
`For Each` ステートメントで、複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを含む反復子変数を指定しています。  
  
 反復子変数は、.NET Framework の `Collections` 名前空間のいずれかに <xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する型である必要があります。 1 つのクラスで複数の構築されたジェネリック インターフェイスを、それぞれの構築に異なる型引数を使用して実装することができます。 これを行うクラスが反復子変数に使用されている場合、その変数には複数の <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドがあります。 このような場合、Visual Basic で呼び出すメソッドを選択することはできません。  
  
 **エラー ID:** BC32096  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- [DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)または [TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)を使用して、反復子変数の型を、使用する <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義するインターフェイスにキャストします。  
  
## <a name="see-also"></a>関連項目

- [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
