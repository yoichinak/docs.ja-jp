---
title: RemoveHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 177952acf362ccb36a36b5f09b11a1a93dbefa29
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333037"
---
# <a name="removehandler-statement"></a>RemoveHandler ステートメント
イベントとイベント ハンドラー間の関連付けを削除します。  
  
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
 `AddHandler` および `RemoveHandler` ステートメントを使用すると、プログラムの実行中に、特定のイベントのイベント処理をいつでも開始および停止できます。  
  
> [!NOTE]
> カスタム イベントの場合は、`RemoveHandler` ステートメントによってイベントの `RemoveHandler` アクセサーが呼び出されます。 カスタム イベントの詳細については、「[Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>関連項目

- [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
