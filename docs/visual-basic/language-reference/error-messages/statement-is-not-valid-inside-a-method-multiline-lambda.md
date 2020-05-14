---
title: メソッドや複数行のラムダの内部では有効でないステートメントです。
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 9e6c8ddd7851aee6d9fa1928a6854f7337b867b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593226"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>メソッドや複数行のラムダの内部では有効でないステートメントです。
ステートメントは、`Sub`、`Function`、プロパティ `Get`、またはプロパティ `Set` プロシージャ内で無効です。 一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。 `Option Strict` などの他のものは、名前空間レベルで、他のすべての宣言の前に配置する必要があります。  
  
 **エラー ID:** BC30024  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- プロシージャからステートメントを削除します。  
  
## <a name="see-also"></a>関連項目

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
