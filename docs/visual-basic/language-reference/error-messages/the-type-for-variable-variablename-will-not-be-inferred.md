---
title: 変数 '<variablename>' の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013648"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>変数の型 '\<variablename >' は、外側のスコープ内のフィールドにバインドされているために、推論できません。
変数の型 '\<variablename >' は、外側のスコープ内のフィールドにバインドされているために、推論できません。 名前を変更するか '\<variablename >'、または完全修飾名 (たとえば、Me.variablename"や 'MyBase.variablename') を使用します。  
  
 コードのループ制御変数は、クラスまたは他の外側のスコープ内のフィールドと同じ名前を持っています。 制御変数は、`As` 句なしで使用されるため、外側のスコープ内のフィールドにバインドされ、コンパイラがこれに対して新しい変数を作成したり、その型を推論したりすることはありません。  
  
 次の例では、`Index` (`For` ステートメントの制御変数) が、`Index` クラスの `Customer` フィールドにバインドされています。 コンパイラが制御変数 `Index` に対して新しい変数を作成したり、その型を推論したりすることはありません。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42110  
  
### <a name="to-address-this-warning"></a>この警告に対処するには  
  
- ループ制御変数の名前を、クラスのフィールドの名前とは異なる識別子に変更して、この変数をローカルにします。  
  
    ```  
    For I = 1 To 10  
    ```  
  
- 変数名の前に `Me.` を付けることにより、クラス フィールドにループ制御変数がバインドされていることを明確にします。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- ローカル型の推定ではなく `As` 句を使用して、ループ制御変数に型を指定します。  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>例  
 次のコードは、上の例に最初の修正を行ったものです。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>関連項目

- [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [方法: オブジェクトの現在のインスタンスを参照してください。](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
