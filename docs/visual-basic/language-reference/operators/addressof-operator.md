---
title: AddressOf 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760378"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 演算子 (Visual Basic)
特定のプロシージャを参照するデリゲート インスタンスを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>指定項目  
 `procedurename`  
 必須。 新しく作成されたデリゲートが参照するプロシージャを指定します。  
  
## <a name="remarks"></a>Remarks  
 `AddressOf`演算子は、sub またはで指定された関数を指すデリゲートを作成します。`procedurename`します。 ときに、指定したプロシージャは、インスタンス メソッド、デリゲートがインスタンスとメソッドの両方を参照します。 次に、デリゲートが呼び出されたときに、指定したインスタンスの指定されたメソッドが呼び出されます。  
  
 `AddressOf` Delegate コンス トラクターのオペランドとして使用できる演算子またはにおいて、コンパイラによってデリゲートの型を決定するために使用できます。  
  
## <a name="example"></a>例  
 この例では、`AddressOf`を処理するデリゲートを指定する演算子、`Click`ボタンのイベント。  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>例  
 次の例では、`AddressOf`スレッドのスタートアップ関数を指定する演算子。  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
