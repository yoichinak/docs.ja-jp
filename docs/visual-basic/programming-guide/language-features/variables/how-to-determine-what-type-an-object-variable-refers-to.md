---
title: '方法: オブジェクト変数の参照 (Visual Basic) にどのような種類を決定します。'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: dc6f54719d4f30be00b7b85f0ab18c4cb02b0d7c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816409"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>方法: オブジェクト変数の参照 (Visual Basic) にどのような種類を決定します。
オブジェクト変数には、別の場所に格納されているデータへのポインターが含まれています。 実行時にそのデータの種類を変更できます。 任意の時点では、使用することができます、<xref:System.Type.GetTypeCode%2A>する現在の実行時の型を判断するメソッド、または[TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)ことを確認する現在の実行時の型が指定された型との互換性。  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>現在オブジェクト変数を入力を正確なを判断するには  
  
1.  オブジェクト変数を呼び出して、<xref:System.Object.GetType%2A>を取得するメソッド、<xref:System.Type?displayProperty=nameWithType>オブジェクト。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <xref:System.Type?displayProperty=nameWithType>クラス、共有メソッドを呼び出す<xref:System.Type.GetTypeCode%2A>を取得する、<xref:System.TypeCode>オブジェクトの型の列挙値。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     テストすることができます、<xref:System.TypeCode>などは、関心のある方の列挙体メンバーに対して列挙値`Double`します。  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>変数の型が指定した型と互換性がオブジェクトかどうかを判断するには  
  
-   使用して、`TypeOf`演算子と組み合わせて、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)でオブジェクトをテストする、 `TypeOf`.`Is`式。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`.`Is`式を返します`True`型に指定した型と互換性がある場合は、オブジェクトの実行時。  
  
     互換性のための条件は、指定した型がクラス、構造体、またはインターフェイスによって異なります。 一般に、型が互換性のあるオブジェクトと同じ型の継承、または指定した型を実装する場合。 詳細については、[TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 指定した型が変数または式ができないことに注意してください。 クラス、構造体、インターフェイスなどの定義済みの型の名前があります。 などの組み込みの型が含まれます`Integer`と`String`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
