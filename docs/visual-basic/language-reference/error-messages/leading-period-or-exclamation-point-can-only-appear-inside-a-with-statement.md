---
title: 先頭の '.' または '!' は、'With' ステートメント内でのみ使用できます。
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 15390fb506fe9bca10f6917f5b26451a5569bece
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322850"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>先頭の '.' または '!' は、'With' ステートメント内でのみ使用できます。
ピリオド (.) または感嘆符 (!) でない内部、`With`左の式がブロックされます。 メンバー アクセス (`.`) およびディクショナリ メンバー アクセス (`!`) メンバーを含む要素を指定する式が必要です。 これは、アクセサーのまたはのターゲットとしての左側にすぐに表示する必要があります、`With`メンバー アクセスを含むブロックします。  
  
 **エラー ID:** BC30157  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. いることを確認、`With`ブロックが正しく書式設定します。  
  
2. 存在する場合ありません`With`ブロック、メンバーを含む定義の要素に評価されるアクセサーの左側に式を追加します。  
  
## <a name="see-also"></a>関連項目

- [コード内の特殊文字](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
