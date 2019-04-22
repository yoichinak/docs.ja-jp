---
title: "'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817267"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。
ステートメントを使用して、`AddressOf`のプロシージャを表すオペランドと演算子、<xref:System.Nullable%601>構造体。  
  
 **エラー ID:** BC32126  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャ名に置き換えます、`AddressOf`句のメンバーでないオペランドとして<xref:System.Nullable%601>します。  
  
-   メソッドをラップするクラスを作成<xref:System.Nullable%601>を使用します。 次の例では、`NullableWrapper`クラスという名前の新しいメソッドを定義する`GetValueOrDefault`します。 この新しいメソッドのメンバーでないため、<xref:System.Nullable%601>に適用できる`nullInstance`、引数を形成する、null 許容型のインスタンス`AddressOf`します。  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Nullable%601>
- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
