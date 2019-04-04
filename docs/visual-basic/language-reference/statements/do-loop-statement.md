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
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826042"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop ステートメント (Visual Basic)
中にステートメント ブロックを繰り返します、`Boolean`条件が`True`まで、このような条件または`True`します。  
  
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
|`Do`|必須。 定義を開始、`Do`ループします。|  
|`While`|`Until` を使用しない場合に、必ず指定します。 までループを繰り返す`condition`は`False`します。|  
|`Until`|`While` を使用しない場合に、必ず指定します。 までループを繰り返す`condition`は`True`します。|  
|`condition`|省略可能です。 `Boolean` 式。 場合`condition`は`Nothing`、Visual Basic として扱います`False`します。|  
|`statements`|省略可能です。 1 つまたは複数のステートメント、まで、または while、繰り返される`condition`は`True`します。|  
|`Continue Do`|省略可能です。 次のイテレーションに制御を転送、`Do`ループします。|  
|`Exit Do`|省略可能です。 うちに制御を転送、`Do`ループします。|  
|`Loop`|必須。 定義を終了、`Do`ループします。|  
  
## <a name="remarks"></a>Remarks  
 使用して、`Do...Loop`一連の条件が満たされるまで何度で不特定数のステートメントを繰り返し表示するときに構造体します。 設定された数の時間、ステートメントを繰り返し表示する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は、通常のことをお勧めします。  
  
 いずれかを使用する`While`または`Until`を指定する`condition`、両方ではないです。  
  
 テストすることができます`condition`先頭またはループの終了のいずれか 1 つだけの時間。 テストする場合`condition`、ループの先頭 (で、`Do`ステートメント)、ループでも 1 回を実行しない可能性があります。 ループの最後にテストする場合 (で、`Loop`ステートメント)、ループは、1 つ以上の時間を常に実行されます。  
  
 条件は、通常は 2 つの値の比較から結果しますが、任意に評価される式を[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。 これにより、数値型に変換されたなどの他のデータ型の値が含まれます。`Boolean`します。  
  
 入れ子にすることができます`Do`内に別の 1 つのループを配置することでループします。 さまざまな種類を 1 つの制御構造の入れ子にすることもできます。 詳細については、[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)を参照してください。  
  
> [!NOTE]
>  `Do...Loop`構造より柔軟性、[中.End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)、ループを終了するかどうかを決定することもできるため、ときに`condition`停止されている`True`がそのときまたは`True`します。 テストすることもできます`condition`先頭またはループの終了のいずれか。  
  
## <a name="exit-do"></a>操作を終了します。  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する別の方法を提供する`Do…Loop`します。 `Exit Do` 続くステートメントに直ちに制御を移します、`Loop`ステートメント。  
  
 `Exit Do` 例では、いくつかの条件が評価された後に多くの場合に使用される、`If...Then...Else`構造体。 不要なまたは不可能なエラー値や終了要求など、反復処理を続行する条件を検出した場合、ループを終了する可能性があります。 用途の 1 つ`Exit Do`を引き起こす可能性のある条件をテストするには、*無限ループ*、これは、何度も長時間または無限でも実行できるループします。 使用することができます`Exit Do`ループを抜けます。  
  
 任意の数を含めることができます`Exit Do`でステートメントを任意の場所、`Do…Loop`します。  
  
 使用すると内で入れ子になった`Do`ループ、`Exit Do`上位レベルの入れ子にして、最も内側のループからコントロールを転送します。  
  
## <a name="example"></a>例  
 次の例では、ループ内のステートメントの続行までを実行する、`index`変数が 10 より大きい。 `Until`句は、ループの最後に、します。  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>例  
 次の例では、`While`句の代わりに、`Until`句と`condition`は最後の代わりに、ループの先頭にテストします。  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>例  
 次の例では、`condition`ループを停止するときに、`index`変数が 100 より大きい。 `If`ループでは、ステートメントがただし、により、`Exit Do`インデックス変数が 10 より大きい場合は、ループを停止するステートメント。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>例  
 次の例では、テキスト ファイルのすべての行を読み取ります。 <xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開くし、取得、<xref:System.IO.StreamReader>文字を読み取る。 `Do...Loop`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`追加の文字があるかどうかを決定します。  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>関連項目

- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
