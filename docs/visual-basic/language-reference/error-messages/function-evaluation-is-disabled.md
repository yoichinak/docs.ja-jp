---
title: 前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d024420fbbc3efbd3d19bb58c9379eacbafac5d3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820738"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。
前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。関数の評価をもう一度有効にするには、もう一度ステップを実行するか、またはデバッグを再起動してください。  
  
 Visual Studio デバッガーで、プロシージャ呼び出しが式に指定されていますが、別の評価がタイムアウトしています。  
  
 プロシージャ呼び出しがタイムアウトの原因が考えられます、無限ループまたは*無限ループ*します。 詳細については、次を参照してください[をしています...次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)します。  
  
 無限ループの特殊なケースは*再帰*します。 詳細については、次を参照してください。[再帰プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)します。  
  
 **エラー ID:** BC30957  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  可能であれば、前回の関数の評価がどれかを判断し、タイムアウトした理由を調べます。判断できない場合、このエラーが再度表示される可能性があります。  
  
2.  デバッガーのステップをもう一度実行するか、デバッガーを終了させて再起動します。  
  
## <a name="see-also"></a>関連項目

- [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)
- [デバッガーでのコード間の移動](/visualstudio/debugger/navigating-through-code-with-the-debugger)
