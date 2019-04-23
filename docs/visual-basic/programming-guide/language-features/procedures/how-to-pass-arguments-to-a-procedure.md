---
title: '方法: (Visual Basic)、プロシージャに引数を渡す'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333913"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>方法: (Visual Basic)、プロシージャに引数を渡す
プロシージャを呼び出すときに、引数リストをかっこで、プロシージャ名に従ってください。 プロシージャに定義されたすべての必須パラメーターに対応する引数を指定して、引数を指定することができます必要に応じて、`Optional`パラメーター。 指定しない場合、`Optional`呼び出しのパラメーターは、すべての後続の引数を指定している場合、引数リスト内の場所をマークする、コンマを含める必要があります。  
  
 など、対応するパラメーターの異なるに渡すには、データ型の引数にするかどうかに`Byte`に`String`、型チェック スイッチを設定することができます ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) に`Off`します。 場合`Option Strict`は`On`、いずれかを使用する必要がありますまたはキーワードの明示的な変換の変換を拡大します。 詳細については、次を参照してください。 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)します。  
  
 詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)します。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>プロシージャに 1 つまたは複数の引数を渡す  
  
1. 呼び出し元のステートメントをかっこでプロシージャ名に従います。  
  
2. かっこの内側に、引数リストを配置します。 プロシージャの定義、必要な各パラメーターの引数を含むし、引数をコンマで区切ります。  
  
3. 各引数は、対応するパラメーターの型、プロシージャに変換できるデータ型に評価される有効な式を定義することを確認します。  
  
4. パラメーターとして定義されている場合[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)、引数リストに含めるか、これを省略します。 を省略した場合、手順は、そのパラメーターの定義された既定値を使用します。  
  
5. 引数を省略した場合、`Optional`パラメーターとパラメーター リストで別のパラメーター後に、引数リスト内の余分なコンマが省略された引数の代わりをマークすることができます。  
  
     次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数。  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     前の例では、必要な最初の引数は表示されるメッセージ文字列を提供します。 メッセージ ボックスに表示するボタンを指定する省略可能な第 2 パラメーターの引数が省略されます。 呼び出しは、値を指定していないため、 `MsgBox` 、既定値を使用して`MsgBoxStyle.OKOnly`、のみが表示されます、 **[ok]** ボタンをクリックします。  
  
     引数リスト内の 2 つ目のコンマは省略すると 2 番目の引数の場所をマークし、最後の文字列の省略可能な 3 番目のパラメーターに渡された`MsgBox`、これは、タイトル バーに表示されるテキスト。  
  
## <a name="see-also"></a>関連項目

- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [方法: プロシージャのパラメーターを定義します。](./how-to-define-a-parameter-for-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [再帰プロシージャ](./recursive-procedures.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
