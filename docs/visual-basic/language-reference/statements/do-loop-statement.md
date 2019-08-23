---
title: Do...Loop ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942994"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop ステートメント (Visual Basic)
`Boolean`条件がで`True` ある`True`か、条件がになるまで、ステートメントのブロックを繰り返します。  
  
## <a name="syntax"></a>構文  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`Do`|必須。 `Do`ループの定義を開始します。|  
|`While`|`Until` を使用しない場合に、必ず指定します。 がに`condition` `False`なるまでループを繰り返します。|  
|`Until`|`While` を使用しない場合に、必ず指定します。 がに`condition` `True`なるまでループを繰り返します。|  
|`condition`|省略可能です。 `Boolean`条件. `False`が`condition` の場合、VisualBasicはとし`Nothing`て扱います。|  
|`statements`|省略可能です。 または`condition`の間に繰り返される1つ以上のステートメントが`True`です。|  
|`Continue Do`|省略可能です。 `Do`ループの次の反復処理に制御を転送します。|  
|`Exit Do`|省略可能です。 制御を`Do`ループの外に転送します。|  
|`Loop`|必須。 `Do`ループの定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 条件が`Do...Loop`満たされるまで、一連のステートメントを不特定の回数繰り返し繰り返す場合は、構造体を使用します。 設定された数の時間、ステートメントを繰り返し表示する場合、[For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)は、通常のことをお勧めします。  
  
 または`While` `Until`のいずれかを使用`condition`して、両方を指定することはできません。  
  
 ループの開始`condition`時または終了時に1回だけテストできます。 ループの開始`condition`時 ( `Do`ステートメント内) にテストした場合、ループは一度も実行されない可能性があります。 ループの最後 ( `Loop`ステートメント内) でテストした場合、ループは常に少なくとも1回は実行されます。  
  
 通常、この条件は2つの値の比較によって得られますが、[ブールデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)の値 (`True`また`False`は) に評価される任意の式を指定できます。 これには、に`Boolean`変換された他のデータ型 (数値型など) の値が含まれます。  
  
 ループを入れ子`Do`にするには、ループを別のループ内に配置します。 また、さまざまな種類の制御構造を相互に入れ子にすることもできます。 詳細については、「[入れ子になったコントロール構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
> [!NOTE]
> `Do...Loop`構造体によって、より高い柔軟性が得られます。 [End while ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)を使用すると、ループが停止`condition` `True`したとき、または最初`True`に発生したときに、ループを終了するかどうかを決定できます。 また、ループの開始時`condition`または終了時にテストすることもできます。  
  
## <a name="exit-do"></a>終了  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントは、を終了する別の`Do…Loop`方法を提供できます。 `Exit Do``Loop`ステートメントの後にあるステートメントに制御を直ちに転送します。  
  
 `Exit Do`は、 `If...Then...Else`構造体などの条件を評価した後に頻繁に使用されます。 誤った値や終了要求など、反復処理を続行することが不要または不可能な条件を検出した場合は、ループを終了することができます。 の1つ`Exit Do`の用途は、*無限ループ*の原因となる可能性のある条件をテストすることです。これは、大規模または無限の回数実行されるループです。 を使用`Exit Do`すると、ループをエスケープできます。  
  
 内の任意の場所に`Exit Do`任意の数のステートメントを含めることができます。`Do…Loop`  
  
 入れ子になっ`Do`たループ内`Exit Do`で使用すると、最も内側のループから、入れ子の次の上位レベルに制御を転送します。  
  
## <a name="example"></a>例  
 次の例では、 `index`変数が10を超えるまで、ループ内のステートメントが実行され続けます。 `Until`句はループの最後にあります。  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>例  
 次の例では`While` 、 `Until`句ではなく句を`condition`使用して、末尾ではなくループの開始時にテストします。  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>例  
 次の例では`condition` 、 `index`変数が100より大きい場合、はループを停止します。 ただし、ループ内の`Exit Do` ステートメントを指定すると、インデックス変数が10を超える場合、ステートメントによってループが停止します。`If`  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>例  
 次の例では、テキストファイル内のすべての行を読み取ります。 メソッド<xref:System.IO.File.OpenText%2A>は、ファイルを開き、文字<xref:System.IO.StreamReader>を読み取るを返します。 条件では、 `StreamReader`のメソッドによって、追加の文字があるかどうかが判断されます。<xref:System.IO.StreamReader.Peek%2A> `Do...Loop`  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>関連項目

- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
