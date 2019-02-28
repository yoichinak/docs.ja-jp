---
title: End ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 8b189449044a48432a6cf05b75f39581be111495
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979536"
---
# <a name="end-statement"></a>End ステートメント
すぐに実行を終了します。  
  
## <a name="syntax"></a>構文  
  
```  
End  
```  
  
## <a name="remarks"></a>Remarks  
 配置することができます、`End`ステートメント、プロシージャを強制的に実行を停止するアプリケーション全体で任意の場所。 `End` 開かれた任意のファイルを閉じ、`Open`ステートメントと、アプリケーションのすべての変数を消去します。 アプリケーションは、そのオブジェクトへの参照を保持している他のプログラムがないとのコードが実行されているとすぐに閉じます。  
  
> [!NOTE]
>  `End`ステートメントは、突然、コードが実行を停止しは呼び出されません、`Dispose`または`Finalize`メソッド、またはその他の Visual Basic コードです。 その他のプログラムによって保持されているオブジェクト参照が無効になります。 場合、`End`内でステートメントが検出された、`Try`または`Catch`コントロール ブロックは、対応するのには渡されません`Finally`ブロックします。  
  
 `Stop`ステートメントのとは異なり、実行を中断`End`、すべてのファイルを終了したり、コンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアしません。  
  
 `End`在籍していることがなく、アプリケーションを終了します。 開いている可能性があるすべてのリソースを閉じるためクリーンに使用する前に行う必要があります。 たとえば、すべてのフォームを開くアプリケーションの場合は、する必要があります閉じたコントロールに到達する前に、`End`ステートメント。  
  
 使用する必要があります`End`限り注意を必要がある場合を直ちに停止します。 プロシージャを終了する通常の方法 ([Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)と[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)) だけでなく、プロシージャを正しく閉じてがも呼び出し元コードに正常に閉じるための機会を提供します。 単に、コンソール アプリケーションはなどできます`Return`から、`Main`プロシージャ。  
  
> [!IMPORTANT]
>  `End`ステートメントの呼び出し、<xref:System.Environment.Exit%2A>のメソッド、<xref:System.Environment>クラス、<xref:System>名前空間。 <xref:System.Environment.Exit%2A> 必要です`UnmanagedCode`権限。 そうでない場合、<xref:System.Security.SecurityException>エラーが発生します。  
  
 1 つのキーワードに続く場合[エンド\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)適切なプロシージャまたはブロックの定義の末尾を区切ります。 たとえば、`End Function`の定義を終了、`Function`プロシージャ。  
  
## <a name="example"></a>例  
 次の例では、`End`ユーザーが要求する場合は、コードの実行を終了するステートメント。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>スマート デバイスの開発者向け注意事項  
 このステートメントはサポートされていません。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop ステートメント](../../../visual-basic/language-reference/statements/stop-statement.md)
- [終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
