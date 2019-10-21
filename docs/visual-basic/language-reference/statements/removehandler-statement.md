---
title: RemoveHandler ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582022"
---
# <a name="removehandler-statement"></a>RemoveHandler ステートメント
イベントとイベントハンドラーの間の関連付けを削除します。  
  
## <a name="syntax"></a>構文  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`event`|処理されるイベントの名前。|  
|`eventhandler`|イベントを現在処理しているプロシージャの名前。|  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 および `RemoveHandler` ステートメントを使用すると、プログラムの実行中に、特定のイベントのイベント処理をいつでも開始および停止できます。  
  
> [!NOTE]
> カスタムイベントの場合は、`RemoveHandler` ステートメントによって、イベントの `RemoveHandler` アクセサーが呼び出されます。 カスタムイベントの詳細については、「 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
