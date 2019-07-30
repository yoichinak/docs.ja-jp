---
title: '方法: 2つのオブジェクトが関連付けられているかどうかを判断する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626557"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>方法: 2つのオブジェクトが関連付けられているかどうかを判断する (Visual Basic)

2つのオブジェクトを比較して、作成元のクラス間のリレーションシップ (存在する場合) を判断できます。 クラスのメソッドは<xref:System.Type.IsInstanceOfType%2A> 、指定`True`したクラスが現在のクラスから継承している場合、または現在の型が指定したクラスでサポートされているインターフェイスである場合にを返します。 <xref:System.Type?displayProperty=nameWithType>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>あるオブジェクトが別のオブジェクトのクラスまたはインターフェイスから継承しているかどうかを確認するには

1. 基本型と考えられるオブジェクトで、 <xref:System.Object.GetType%2A>メソッドを呼び出します。

2. によって<xref:System.Object.GetType%2A>返される<xref:System.Type.IsInstanceOfType%2A>オブジェクトで、メソッドを呼び出します。 <xref:System.Type?displayProperty=nameWithType>

3. の<xref:System.Type.IsInstanceOfType%2A>引数リストで、派生型として考えられるオブジェクトを指定します。

    <xref:System.Type.IsInstanceOfType%2A>引数`True`の型がオブジェクト型から継承<xref:System.Type?displayProperty=nameWithType>される場合は、を返します。

## <a name="example"></a>例
 次の例では、あるオブジェクトが、別のオブジェクトのクラスから派生したクラスを表しているかどうかを判断します。

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

の呼び出しで、2つのオブジェクト変数が予期せず<xref:System.Type.IsInstanceOfType%2A>に配置されていることに注意してください。 想定される基本型は<xref:System.Type?displayProperty=nameWithType>クラスを生成するために使用され、想定される派生型は引数として<xref:System.Type.IsInstanceOfType%2A>メソッドに渡されます。

## <a name="see-also"></a>関連項目

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [方法: 2つのオブジェクトが同一かどうかを判断する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
