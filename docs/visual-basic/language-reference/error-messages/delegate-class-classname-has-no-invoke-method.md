---
title: Delegate クラス '<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803637"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Delegate クラス '\<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません
デリゲート クラスに `Invoke` が実装されていないため、デリゲートを使用して `Invoke` を呼び出すことができませんでした。  
  
 **エラー ID:** BC30220  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. デリゲート クラスのインスタンスが `Dim` ステートメントを使用して作成されていること、およびプロシージャが `AddressOf` 演算子を使用してデリゲート インスタンスに割り当てられていることを確認してください。  
  
2. デリゲート クラスを実装するコードを見つけ、それによって `Invoke` プロシージャが実装されることを確認します。  
  
## <a name="see-also"></a>関連項目

- [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
