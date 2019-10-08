---
title: Call ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005168"
---
# <a name="call-statement-visual-basic"></a>Call ステートメント (Visual Basic)

@No__t-0、@no__t 1、またはダイナミックリンクライブラリ (DLL) プロシージャに制御を転送します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>指定項目  

|||
|---|---|
|`procedureName`|必須。 呼び出すプロシージャの名前。|
|`argumentList`|任意。 プロシージャが呼び出されたときにプロシージャに渡される引数を表す変数または式のリスト。 複数の引数は、コンマで区切ります。 @No__t-0 を指定する場合は、かっこで囲む必要があります。|
|||
  
## <a name="remarks"></a>コメント

 プロシージャを呼び出すときには、`Call` キーワードを使用できます。 ほとんどのプロシージャ呼び出しでは、このキーワードを使用する必要はありません。

 通常、呼び出された式が識別子で始まらない場合は、`Call` キーワードを使用します。 他の用途には `Call` キーワードを使用しないことをお勧めします。

 プロシージャが値を返す場合、`Call` ステートメントはそれを破棄します。

## <a name="example"></a>例

 次のコードは、プロシージャを呼び出すために @no__t 0 キーワードが必要な2つの例を示しています。 どちらの例でも、呼び出された式の先頭が識別子ではありません。

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>関連項目

- [Function ステートメント](function-statement.md)
- [Sub ステートメント](sub-statement.md)
- [Declare ステートメント](declare-statement.md)
- [ラムダ式](../../programming-guide/language-features/procedures/lambda-expressions.md)
