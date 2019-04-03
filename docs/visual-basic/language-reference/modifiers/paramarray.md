---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816663"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
プロシージャのパラメーターが指定した型の要素の省略可能な配列を受け取ることを指定します。 `ParamArray` パラメーター リストの最後のパラメーターでのみ使用できます。  
  
## <a name="remarks"></a>Remarks  
 `ParamArray` プロシージャに任意の数の引数を渡すことができます。 A`ParamArray`を使用してパラメーターが常に宣言[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)します。  
  
 1 つまたは複数の引数を指定できます、`ParamArray`適切なデータの配列を渡すことによってパラメーターの型、値、または何ものコンマ区切りの一覧にします。 詳細については、"呼び出しを ParamArray"を参照してください[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)します。  
  
> [!IMPORTANT]
>  無限に増大することができる配列を処理するたびに、アプリケーションの内部の容量を超過してしまう可能性があります。 呼び出し元のコードからパラメーターの配列を受け取る場合その長さをテスト、アプリケーションが大きすぎる場合は、適切な手順を実行してください。  
  
 `ParamArray` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
