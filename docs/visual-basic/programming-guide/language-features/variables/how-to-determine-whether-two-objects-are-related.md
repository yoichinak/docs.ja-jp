---
title: '方法: 2 つのオブジェクトが関連するかどうかを判断する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: f59e00d80d28fc4bf24874d25b5c12643649c834
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342103"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>方法: 2 つのオブジェクトが関連するかどうかを判断する (Visual Basic)
作成元のクラス間のリレーションシップを判別する 2 つのオブジェクトを比較することができます。 <xref:System.Type.IsInstanceOfType%2A>のメソッド、<xref:System.Type?displayProperty=nameWithType>クラスを返します。`True`指定したクラスは、現在のクラスから継承する場合、または現在の型が指定したクラスでサポートされているインターフェイス。  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>1 つのオブジェクトが別のオブジェクトのクラスまたはインターフェイスから継承かどうかを判断するには  
  
1. 思われるオブジェクトの可能性があります、基本型で、呼び出し、<xref:System.Object.GetType%2A>メソッド。  
  
2. <xref:System.Type?displayProperty=nameWithType>によって返されるオブジェクト<xref:System.Object.GetType%2A>を呼び出し、<xref:System.Type.IsInstanceOfType%2A>メソッド。  
  
3. 引数リストで<xref:System.Type.IsInstanceOfType%2A>、派生型のオブジェクトと思われる場合がありますを指定します。  
  
     <xref:System.Type.IsInstanceOfType%2A> 返します`True`その引数の型から継承している場合、<xref:System.Type?displayProperty=nameWithType>オブジェクトの種類。  
  
## <a name="example"></a>例  
 次の例では、1 つのオブジェクトが別のオブジェクトのクラスから派生したクラスを表すかどうかを判断します。  
  
```  
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
  
 予期しない呼び出しで 2 つのオブジェクト変数の配置に注意してください<xref:System.Type.IsInstanceOfType%2A>します。 想定される基本データ型の生成に使用、<xref:System.Type?displayProperty=nameWithType>クラス、および想定される派生型が引数として渡される、<xref:System.Type.IsInstanceOfType%2A>メソッド。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [方法: 2 つのオブジェクトが同一かどうかを判断します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
