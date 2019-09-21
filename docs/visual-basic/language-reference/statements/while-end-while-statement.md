---
title: While...End While ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965812"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While ステートメント (Visual Basic)
指定された条件が真`True`である間、一連のステートメントを繰り返し実行します。  
  
## <a name="syntax"></a>構文  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`condition`|必須。 `Boolean`条件. `False`が`condition` の場合、VisualBasicはとし`Nothing`て扱います。|  
|`statements`|任意。 に続く`While`1 つ以上のステートメント`condition`が、のたび`True`に実行されます。|  
|`Continue While`|任意。 `While`ブロックの次の反復処理に制御を転送します。|  
|`Exit While`|任意。 制御を`While`ブロックの外に転送します。|  
|`End While`|必須。 `While` ブロックの定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 条件が`While...End While`残っ`True`ている限り、一連のステートメントを無限の回数だけ繰り返す場合は、構造体を使用します。 お勧めのその条件をテストするか、結果の判定をより柔軟にテストする場合、[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)します。 設定された数の時間、ステートメントを繰り返し表示する場合、[For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)は、通常のことをお勧めします。  
  
> [!NOTE]
> `While`でキーワードを使用しても、[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)と[Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)します。  
  
 が`condition` `End While` `statements`の場合、ステートメントが見つかるまですべてのが実行されます。 `True` その後、制御`While` `condition`はステートメントに戻り、再度チェックされます。 が`condition` まだ`True`の場合、プロセスは繰り返されます。 の`False`場合、制御は`End While`ステートメントの後のステートメントに渡されます。  
  
 ステートメント`While`は、ループを開始する前に常に条件をチェックします。 条件が残っ`True`ている間、ループは続行されます。 が最初`False`にループに入るときに、が1回だけ実行されることはありません。 `condition`  
  
 `condition`が 2 つの値の比較からの結果に評価される任意の式は、通常、[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。 この式には、に`Boolean`変換された別のデータ型 (数値型など) の値を含めることができます。  
  
 ループを入れ子`While`にするには、ループを別のループ内に配置します。 また、さまざまな種類の制御構造を相互に入れ子にすることもできます。 詳細については、「[入れ子になったコントロール構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
## <a name="exit-while"></a>Exit While  
 [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する別の方法を提供する`While`ループします。 `Exit While``End While`ステートメントに続くステートメントに制御を直ちに転送します。  
  
 通常は、 `Exit While`何らかの条件が評価された後 ( `If...Then...Else`構造など) にを使用します。 誤った値や終了要求など、反復処理を続行することが不要または不可能な条件を検出した場合は、ループを終了することができます。 *無限ループ*の`Exit While`原因となる可能性のある条件をテストするときに、を使用できます。これは、非常に大きいまたは無限の回数実行されるループです。 その後、を`Exit While`使用してループをエスケープできます。  
  
 ループ内の任意の場所`Exit While`に任意の数のステートメントを配置できます。 `While`  
  
 入れ子になっ`While`たループ内`Exit While`で使用すると、最も内側のループから、入れ子の次の上位レベルに制御を転送します。  
  
 ステートメント`Continue While`は、ループの次の反復処理に制御を直ちに転送します。 詳細については、「 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、 `index`変数が10を超えるまで、ループ内のステートメントが実行され続けます。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>例  
 次の例は、ステートメント`Continue While`と`Exit While`ステートメントの使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>例  
 次の例では、テキストファイル内のすべての行を読み取ります。 メソッド<xref:System.IO.File.OpenText%2A>は、ファイルを開き、文字<xref:System.IO.StreamReader>を読み取るを返します。 条件で<xref:System.IO.StreamReader.Peek%2A> は`StreamReader` 、のメソッドは、ファイルに追加の文字が含まれているかどうかを判断します。 `While`  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>関連項目

- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)
