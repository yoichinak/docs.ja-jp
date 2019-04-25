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
ms.openlocfilehash: 755443a99a1ad8b0430a76d2dba1ff27472d4c9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832646"
---
# <a name="call-statement-visual-basic"></a>Call ステートメント (Visual Basic)
転送コントロールを`Function`、 `Sub`、またはダイナミック リンク ライブラリ (DLL) プロシージャ。  
  
## <a name="syntax"></a>構文  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>指定項目  
|||
|---|---|
|`procedureName`|必須。 呼び出すプロシージャの名前。|
|`argumentList`|任意。 変数または呼び出された場合、プロシージャに渡される引数を表す式の一覧です。 複数の引数は、コンマで区切られます。 含める場合`argumentList`かっこで囲む必要があります。|
|||
  
## <a name="remarks"></a>Remarks  
 使用することができます、`Call`プロシージャを呼び出すときに、キーワード。 ほとんどのプロシージャ呼び出しについては、このキーワードを使用する必要はありません。  
  
 通常、使用、`Call`キーワード、識別子で呼び出された式が開始しない場合。 使用、`Call`キーワードの他の使用はお勧めしません。  
  
 プロシージャは、値を返す場合、`Call`ステートメントでは、それを破棄します。  
  
## <a name="example"></a>例  
 次のコードは 2 つの例で、`Call`キーワードは、プロシージャを呼び出すために必要な。 どちらの例では、呼び出された式が識別子で開始しません。  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>関連項目

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
