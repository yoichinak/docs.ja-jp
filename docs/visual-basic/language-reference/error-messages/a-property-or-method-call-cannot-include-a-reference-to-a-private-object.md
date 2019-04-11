---
title: プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341479"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。
このエラーでは以下の原因が考えられます。  
  
-   クライアントが、アウトプロセス コンポーネントのプロパティまたはメソッドを呼び出し、引数の 1 つとしてプライベート オブジェクトへの参照を渡そうとしました。  
  
-   アウトプロセス コンポーネントがクライアントに対してコールバック メソッドを呼び出し、プライベート オブジェクトへの参照を渡そうとしました。  
  
-   アウトプロセス コンポーネントが、それ自身が発生させているイベントの引数として、プライベート オブジェクトへの参照を渡そうとしました。  
  
-   クライアントが、それ自身が処理しているイベントの `ByRef` 引数に、プライベート オブジェクト参照を代入しようとしました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 参照を削除します。  
  
## <a name="see-also"></a>関連項目

- [プライベート](../../../visual-basic/language-reference/modifiers/private.md)
