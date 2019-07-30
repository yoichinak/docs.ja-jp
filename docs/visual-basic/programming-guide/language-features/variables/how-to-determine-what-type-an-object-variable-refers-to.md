---
title: '方法: オブジェクト変数が参照する型を確認する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626572"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>方法: オブジェクト変数が参照する型を確認する (Visual Basic)

オブジェクト変数には、他の場所に格納されているデータへのポインターが含まれています。 データの種類は、実行時に変更される可能性があります。 いつでも、 <xref:System.Type.GetTypeCode%2A>メソッドを使用して現在のランタイム型を判断したり、 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)を使用して、現在の実行時の型が指定された型と互換性があるかどうかを確認したりすることができます。

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>オブジェクト変数で現在参照されている正確な型を確認するには

1. オブジェクト変数で、 <xref:System.Object.GetType%2A>メソッドを呼び出してオブジェクトを<xref:System.Type?displayProperty=nameWithType>取得します。

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. クラスで、共有メソッド<xref:System.Type.GetTypeCode%2A>を呼び出して、オブジェクトの<xref:System.TypeCode>型の列挙値を取得します。 <xref:System.Type?displayProperty=nameWithType>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    列挙値は<xref:System.TypeCode> 、などの目的`Double`の列挙体メンバーに対してテストできます。

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>オブジェクト変数の型が指定した型と互換性があるかどうかを判断するには

- 演算子を[is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md) `TypeOf`と組み合わせて使用して、... `TypeOf``Is`式。

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`...オブジェクトの`True`実行時の型が指定した型と互換性がある場合、式はを返します。 `Is`

    互換性の基準は、指定された型がクラス、構造体、またはインターフェイスのいずれであるかによって異なります。 一般に、オブジェクトがと同じ型であるか、指定された型を継承するか、または実装する場合、型は互換性があります。 詳細については、「 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)」を参照してください。

## <a name="compiling-the-code"></a>コードのコンパイル

指定された型を変数または式にすることはできません。 クラス、構造体、インターフェイスなど、定義された型の名前である必要があります。 これには、や`Integer` `String`などの組み込み型が含まれます。

## <a name="see-also"></a>関連項目

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
