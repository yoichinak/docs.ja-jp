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
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843712"
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
|`condition`|必須。 `Boolean` 式。 場合`condition`は`Nothing`、Visual Basic として扱います`False`します。|  
|`statements`|任意。 1 つまたは複数のステートメントの次`While`、毎回を実行する`condition`は`True`します。|  
|`Continue While`|任意。 次のイテレーションに制御を転送、`While`ブロックします。|  
|`Exit While`|任意。 うちに制御を転送、`While`ブロックします。|  
|`End While`|必須。 `While` ブロックの定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 使用して、`While...End While`条件が残っている限りを一連の回数、不特定数のステートメントを繰り返し表示するときに`True`します。 お勧めのその条件をテストするか、結果の判定をより柔軟にテストする場合、[の操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)します。 設定された数の時間、ステートメントを繰り返し表示する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は、通常のことをお勧めします。  
  
> [!NOTE]
>  `While`でキーワードを使用しても、[の操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)と[Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)します。  
  
 場合`condition`は`True`、すべての`statements`まで実行、`End While`ステートメントが見つかりました。 制御を返します、`While`ステートメント、および`condition`が再度チェックします。 場合`condition`が`True`プロセスが繰り返されます。 `False`、コントロールに続くステートメントに渡す、`End While`ステートメント。  
  
 `While`ステートメントは常に、ループを開始する前に、条件を確認します。 条件がループが継続`True`します。 場合`condition`は`False`一度も実行されない、ループを最初に入力するとします。  
  
 `condition`が 2 つの値の比較からの結果に評価される任意の式は、通常、[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。 この式は、数値型に変換されているなどの別のデータ型の値を含めることができます`Boolean`します。  
  
 入れ子にすることができます`While`内に別の 1 つのループを配置することでループします。 さまざまな種類の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)します。  
  
## <a name="exit-while"></a>中に終了  
 [終了中に](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する別の方法を提供する`While`ループします。 `Exit While` すぐに続くステートメントに制御を転送、`End While`ステートメント。  
  
 通常使用する`Exit While`いくつかの条件が評価された後 (たとえば、`If...Then...Else`構造)。 不要なまたは不可能なエラー値や終了要求など、反復処理を続行する条件を検出した場合、ループを終了する可能性があります。 使用することができます`Exit While`の考えられる原因の条件をテストするとき、*無限ループ*、これは、非常に大規模または無限も可能回数だけ実行できるループします。 使用することができますし、`Exit While`ループを抜けます。  
  
 任意の数を配置する`Exit While`でステートメントを任意の場所、`While`ループします。  
  
 使用すると内で入れ子になった`While`ループ、`Exit While`上位レベルの入れ子にして、最も内側のループからコントロールを転送します。  
  
 `Continue While`ステートメントはすぐに、ループの次のイテレーションに制御を転送します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、ループ内のステートメントの続行までを実行する、`index`変数が 10 より大きい。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>例  
 次の例では、使用、`Continue While`と`Exit While`ステートメント。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>例  
 次の例では、テキスト ファイルのすべての行を読み取ります。 <xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開くし、取得、<xref:System.IO.StreamReader>文字を読み取る。 `While`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`ファイルに追加の文字が含まれているかどうかを決定します。  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>関連項目

- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)
