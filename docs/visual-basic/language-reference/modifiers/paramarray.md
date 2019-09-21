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
ms.openlocfilehash: 8fc5d1afd9e9723e6b3c58e100b0519ef8fdfab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968364"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
プロシージャパラメーターが、指定された型の要素のオプションの配列を受け取ることを指定します。 `ParamArray`は、パラメーターリストの最後のパラメーターでのみ使用できます。  
  
## <a name="remarks"></a>Remarks  
 `ParamArray`プロシージャに任意の数の引数を渡すことができます。 パラメーターは常に [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) を使用して宣言されます。`ParamArray`  
  
 適切なデータ型の配列、コンマ区切り`ParamArray`の値のリスト、または何も指定しないで、パラメーターに1つ以上の引数を渡すことができます。 詳細については、「[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)」の「ParamArray の呼び出し」を参照してください。  
  
> [!IMPORTANT]
> 無限に大きくなる可能性がある配列を処理する場合、アプリケーションの内部容量がオーバーランするリスクがあります。 呼び出し元のコードからパラメーター配列を受け取る場合は、その長さをテストし、アプリケーションにとって大きすぎる場合は適切な手順を実行する必要があります。  
  
 `ParamArray` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
