---
title: スタック領域が不足しています。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318794"
---
# <a name="out-of-stack-space-visual-basic"></a>スタック領域が不足しています。(Visual Basic)
スタックは、実行しているプログラムの要求で動的に拡張し、縮小がメモリの作業領域です。 その制限を超えました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. プロシージャが深すぎます。 入れ子にしないことを確認します。  
  
2. 再帰プロシージャが正常に終了することを確認します。  
  
3. ローカル変数では、複数領域がある必要がある場合は、モジュール レベルでいくつかの変数を宣言することをお試しください。 できますも変数を宣言するすべての手順で静的前に追加して、 `Property`、 `Sub`、または`Function`キーワード`Static`します。 使用することができます、`Static`プロシージャ内で個々 の静的変数を宣言するステートメント。  
  
4. 固定長文字列が可変長の文字列よりも多くのスタック領域を使用して、可変長の文字列として、固定長文字列の一部を再定義します。 スタック領域必要ありません、モジュール レベルで文字列を定義することもできます。  
  
5. 数を確認してください。 入れ子になった`DoEvents`関数を使用して呼び出し、、`Calls`スタック上でアクティブなプロシージャ ビュー ダイアログ ボックス。  
  
6. スタックに既にイベント プロシージャを呼び出すイベントをトリガーすることによって、「イベントの連鎖」が発生しなかったことを確認します。 イベントに cascade は、終了していない再帰プロシージャ呼び出しに似ていますがわかりにくく、コード内の明示的な呼び出しではなく、Visual Basic での呼び出しが行われるため。 使用して、`Calls`スタック上でアクティブなプロシージャ ビュー ダイアログ ボックス。  
  
## <a name="see-also"></a>関連項目

- [[メモリ] ウィンドウ](/visualstudio/debugger/memory-windows)
