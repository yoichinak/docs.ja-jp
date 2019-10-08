---
title: AddHandler ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004544"
---
# <a name="addhandler-statement"></a>AddHandler ステートメント
実行時にイベントをイベントハンドラーに関連付けます。  
  
## <a name="syntax"></a>構文  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>指定項目  
|||
|---|---|
|イベント|処理するイベントの名前。|  
|`eventhandler`|イベントを処理するプロシージャの名前。|
|||
  
## <a name="remarks"></a>コメント  
 `AddHandler`ステートメントと`RemoveHandler`ステートメントを使うと、プログラムの実行中にいつでもイベント処理を開始および停止できます。  
  
 `eventhandler`プロシージャのシグネチャは、`event`イベントのシグネチャと一致する必要があります。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。 `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。 `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。 詳細については、「[ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)」を参照してください。  
  
> [!NOTE]
> カスタムイベントの場合、`AddHandler` ステートメントによって、イベントの `AddHandler` アクセサーが呼び出されます。 カスタムイベントの詳細については、「 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
