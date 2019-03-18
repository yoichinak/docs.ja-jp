---
title: 正しくないパターン文字列
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027308"
---
# <a name="invalid-pattern-string"></a>正しくないパターン文字列
検索の `Like` 演算で指定されているパターン文字列が正しくありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  リスト式に使用できる文字を確認します。  
  
2.  パターン範囲の指定で、 `[a-z]`のように、範囲の開始文字が終了文字より小さいことを確認します。  
  
3.  パターン範囲の指定で、 `[a--z]`のように、複数のハイフンが続けて指定されていないことを確認します。  
  
4.  パターン範囲を右角かっこで終了します。  
  
## <a name="see-also"></a>関連項目

- [Like 演算子](../../visual-basic/language-reference/operators/like-operator.md)
