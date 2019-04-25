---
title: "	'#Else' の前には、対応する '#If' または '#ElseIf' が必要です。"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311059"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>	'#Else' の前には、対応する '#If' または '#ElseIf' が必要です。
`#ElseIf` は条件付きコンパイル ディレクティブです。 `#ElseIf`句の前に、対応する`#If`または`#ElseIf`句が必要です。  
  
 **エラー ID:** BC30014  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 先行する`#If`または`#ElseIf`と、この`#ElseIf`とが、間に条件付きコンパイル ブロックを挿入することによって分離されていないこと、または`#End If`句を間違った場所に記述したために分離されていないことを確認します。  
  
2. `#ElseIf`の前に`#Else`ディレクティブがある場合は、その`#Else`を削除するか、`#ElseIf`に変更します。  
  
3. すべて問題ない場合は、条件付きコンパイル ブロックの先頭に `#If` ディレクティブを追加します。  
  
## <a name="see-also"></a>関連項目

- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
