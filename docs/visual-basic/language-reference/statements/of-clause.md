---
title: Of 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784151"
---
# <a name="of-clause-visual-basic"></a>Of 句 (Visual Basic)
導入されています、`Of`句は、識別、*パラメーターを入力*上、*ジェネリック*クラス、構造体、インターフェイス、デリゲート、またはプロシージャ。 ジェネリック型については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)します。  
  
## <a name="using-the-of-keyword"></a>使用して、キーワードの  
 次のコード例では、`Of`キーワードを 2 つの型パラメーターを受け取るクラスのアウトラインを定義します。 これは、*制約*、`keyType`パラメーターで、<xref:System.IComparable>インターフェイスで、使用側コードが実装する型引数を指定する必要がありますが、 <xref:System.IComparable>。 これは、必要なように、`add`プロシージャを呼び出すことができます、<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>メソッド。 制約の詳細については、「 [Type List](../../../visual-basic/language-reference/statements/type-list.md)」をご覧ください。  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 上記のクラス定義を完了するの場合は、さまざまなを構築できます`dictionary`からクラス。 指定する種類`entryType`と`keyType`決定エントリの種類、クラスを保持し、各エントリとキーの種類を関連付けます。 制約のために指定する必要があります`keyType`を実装する型<xref:System.IComparable>します。  
  
 次のコード例は、保持するオブジェクトを作成します。`String`エントリと、`Integer`がそれぞれのキー。 `Integer` 実装<xref:System.IComparable>し、そのために、制約を満たす`keyType`します。  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 キーワード `Of` は次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.IComparable>
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
