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
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591653"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 演算子 (Visual Basic)
特定のプロシージャを参照するデリゲートインスタンスを作成します。  
  
## <a name="syntax"></a>構文  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>指定項目  
 `procedurename`  
 必須。 新しく作成されたデリゲートによって参照されるプロシージャを指定します。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 演算子は、`procedurename` によって指定されたサブまたは関数を指すデリゲートを作成します。 指定されたプロシージャがインスタンスメソッドの場合、デリゲートはインスタンスとメソッドの両方を参照します。 次に、デリゲートが呼び出されると、指定したインスタンスの指定したメソッドが呼び出されます。  
  
 @No__t-0 演算子は、デリゲートコンストラクターのオペランドとして使用することも、コンパイラによってデリゲートの型を決定できるコンテキストで使用することもできます。  
  
## <a name="example"></a>例  
 この例では、`AddressOf` 演算子を使用して、ボタンの @no__t イベントを処理するデリゲートを指定します。  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>例  
 次の例では、`AddressOf` 演算子を使用して、スレッドのスタートアップ関数を指定します。  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
