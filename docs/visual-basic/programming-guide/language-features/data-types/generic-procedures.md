---
title: Visual Basic におけるジェネリック プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 4aed16ce9eb59da54156a0cd5f1594819788521b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818918"
---
# <a name="generic-procedures-in-visual-basic"></a>Visual Basic におけるジェネリック プロシージャ
A*ジェネリック プロシージャ*も呼ばれ、*ジェネリック メソッド*、少なくとも 1 つの型パラメーターで定義されたプロシージャは。 これにより、呼び出し元のコードでプロシージャを呼び出すたびにその要件にデータ型を調整できます。  
  
 手順は、ジェネリック クラスまたはジェネリック構造体の内部で定義されていることだけでジェネリックではありません。 ジェネリックとは、プロシージャがかかる場合があります、通常のパラメーターだけでなく、少なくとも 1 つの型パラメーターを実行する必要があります。 ジェネリック クラスまたは構造体は、非ジェネリック プロシージャは、および非ジェネリック クラス、構造体を含めることができます、またはモジュールには、ジェネリック プロシージャが含まれていることができます。  
  
 ジェネリック プロシージャでは、1 つ、およびそのプロシージャのコードがある場合、戻り値の型で、通常のパラメーター リストで、その型パラメーターを使用できます。  
  
## <a name="type-inference"></a>型推論  
 型引数をまったく指定せず、ジェネリック プロシージャを呼び出すことができます。 この方法で呼び出すことがある場合、コンパイラは適切なデータ型、プロシージャの型引数を渡すを判断するしようとします。 これは呼び出されます*型推論*します。 次のコードの呼び出しを示しているコンパイラが推論型を渡すかで`String`型パラメーターに`t`します。  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 コンパイラが、呼び出しのコンテキストから型引数を推論されない場合、エラーを報告します。 このようなエラーの考えられる原因の 1 つは、配列ランクが一致していません。 たとえば、型パラメーターの配列として通常のパラメーターを定義するとします。 ジェネリック プロシージャを呼び出す場合の異なるランク (次元数)、配列を指定する、不一致が原因で型の推定が失敗します。 次のコードは呼び出しの 1 次元配列を受け取るプロシージャを 2 次元の配列が渡されます。  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 型の推定は、すべての型引数を省略することによってのみ呼び出すことができます。 1 つの型引数を指定する場合に、それらすべてを指定する必要があります。  
  
 型の推定は、ジェネリック プロシージャのみサポートされます。 ジェネリック クラス、構造体、インターフェイス、またはデリゲートの型の推定を呼び出すことはできません。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、ジェネリック`Function`配列で特定の要素を検索する手順。 1 つの型パラメーターを定義しを使用して、パラメーター リストの 2 つのパラメーターを作成します。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>コメント  
 前の例を比較する機能を必要と`searchValue`の各要素に対して`searchArray`します。 この機能を保証するために、型パラメーター制約`T`実装するために、<xref:System.IComparable%601>インターフェイス。 コードを使用して、<xref:System.IComparable%601.CompareTo%2A>メソッドの代わりに、`=`演算子、型引数を指定するという保証がないため`T`サポート、`=`演算子。  
  
 テストすることができます、`findElement`手順を次のコード。  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 呼び出す前に、 `MsgBox` 「0」、「1」、「-1」をそれぞれ表示します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [方法: 複数のデータ型に同一の機能を提供できるクラスを定義する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [方法: ジェネリック クラスを使用する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [プロシージャのパラメーターと引数](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [型リスト](../../../../visual-basic/language-reference/statements/type-list.md)
- [パラメーター リスト](../../../../visual-basic/language-reference/statements/parameter-list.md)
