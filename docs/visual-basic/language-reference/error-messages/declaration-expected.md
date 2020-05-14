---
title: 宣言が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: e6f8bf2b4ce9789a1715971b8262bdd162ba8035
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619530"
---
# <a name="declaration-expected"></a>宣言が必要です。
代入ステートメントやループ ステートメントなどの非宣言ステートメントが、プロシージャの外側に記述されています。 プロシージャの外側で許可されるのは宣言のみです。  
  
 または、プログラミング要素が、`Dim` や `Const` などの宣言キーワードを使用せずに宣言されています。  
  
 **エラー ID:** BC30188  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 非宣言ステートメントをプロシージャの本体に移動します。  
  
- 適切な宣言キーワードを使用して、宣言を開始します。  
  
- 宣言キーワードのスペルが間違っていないことを確認します。  
  
## <a name="see-also"></a>関連項目

- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
