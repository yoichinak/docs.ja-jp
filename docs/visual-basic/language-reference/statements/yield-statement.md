---
title: Yield ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352728"
---
# <a name="yield-statement-visual-basic"></a>Yield ステートメント (Visual Basic)
Sends the next element of a collection to a `For Each...Next` statement.  
  
## <a name="syntax"></a>構文  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>パラメーター  
  
|用語|定義|  
|---|---|  
|`expression`|必須です。 An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.|  
  
## <a name="remarks"></a>Remarks  
 The `Yield` statement returns one element of a collection at a time. The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.  
  
 You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query. Each iteration of the `For Each` loop calls the iterator function. When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained. 次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。  
  
 An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.  
  
 You can use an `Exit Function` or `Return` statement to end the iteration.  
  
 "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.  
  
 For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Iterator Functions and Get Accessors  
 The declaration of an iterator function or `Get` accessor must meet the following requirements:  
  
- It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.  
  
- 戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。  
  
- It cannot have any `ByRef` parameters.  
  
 An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.  
  
 An iterator function can be an anonymous function. 詳細については、「[反復子](../../programming-guide/concepts/iterators.md)」をご覧ください。  
  
## <a name="exception-handling"></a>例外処理  
 A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.  
  
 A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.  
  
 If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed. A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.  
  
## <a name="technical-implementation"></a>技術的な実装  
 The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 The call to `MyIteratorFunction` doesn't execute the body of the function. この呼び出しでは、`IEnumerable(Of String)` が `elements` 変数に返されます。  
  
 `For Each` ループの反復処理では、<xref:System.Collections.IEnumerator.MoveNext%2A> について `elements` メソッドが呼び出されます。 この呼び出しでは、次の `MyIteratorFunction` ステートメントに到達するまで、`Yield` の本体が実行されます。 The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.  
  
 `For Each` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`Yield` ステートメントに到達したときに再度停止します。 The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.  
  
## <a name="example"></a>例  
 The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function. Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。  
  
 The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type. Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>例  
 次の例は、反復子である `Get` アクセサーを示しています。 The property declaration includes an `Iterator` modifier.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>関連項目

- [ステートメント](../../../visual-basic/language-reference/statements/index.md)
