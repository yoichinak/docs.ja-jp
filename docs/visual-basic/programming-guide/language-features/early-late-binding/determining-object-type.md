---
title: オブジェクトの型の決定 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: becbbef008e8a474db198748d45f260fcb90c758
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966776"
---
# <a name="determining-object-type-visual-basic"></a>オブジェクトの型の決定 (Visual Basic)
汎用オブジェクト変数 (つまり、変数として宣言する`Object`) 任意のクラスからオブジェクトを保持できます。 型の変数を使用する場合`Object`オブジェクトのクラスに基づいて異なるアクションを実行する必要があります。 たとえば、一部のオブジェクト可能性がありますサポートしていませんが特定のプロパティまたはメソッドです。 Visual Basic のオブジェクト変数に保存するオブジェクトの種類を決定する 2 つの手段を提供します。、`TypeName`関数と`TypeOf...Is`演算子。  
  
## <a name="typename-and-typeofis"></a>TypeName と TypeOf...Is  
 `TypeName`関数は、文字列が返され、最適な選択肢は、次のコード フラグメントで示すように、格納したり、オブジェクトのクラス名を表示する必要がある場合。  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 `TypeOf...Is`演算子には、等価の文字列比較が使用するよりもはるかに高速であるために、オブジェクトの型をテストするための最適な選択肢`TypeName`します。 次のコード フラグメントを使用して`TypeOf...Is`内、`If...Then...Else`ステートメント。  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 注意事項は、ここで期限。 `TypeOf...Is`演算子を返します`True`オブジェクトが特定の種類のかが特定の型から派生します。 Visual Basic で行うほぼすべてには、オブジェクトで、文字列や整数などのオブジェクトとして考えることは、通常、いくつかの要素を含める必要があります。 これらのオブジェクトから派生するためのメソッドを継承<xref:System.Object>します。 渡されたときに、`Integer`を評価および`Object`、`TypeOf...Is`演算子を返します`True`します。 次の例で提供されるレポート パラメーター`InParam`はどちらも、`Object`と`Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 次の例では、両方は使用して`TypeOf...Is`と`TypeName`内で渡されるオブジェクトの種類を決定する、`Ctrl`引数。 `TestObject`プロシージャ呼び出し`ShowType`で 3 つの異なる種類のコントロール。  
  
#### <a name="to-run-the-example"></a>例を実行するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成し、追加、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.CheckBox>コントロール、および<xref:System.Windows.Forms.RadioButton>コントロールをフォームにします。  
  
2.  フォーム上のボタンから呼び出して、`TestObject`プロシージャ。  
  
3.  次のコードをフォームに追加します。  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>関連項目
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [文字列名によるプロパティまたはメソッドの呼び出し](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
