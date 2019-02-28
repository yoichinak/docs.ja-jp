---
title: "'Custom' 修飾子は、明示的なデリゲート型なしで宣言されたイベントでは無効です。"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c50cee530cab0d5d164d930678651f302ddc7f09
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980764"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾子は、明示的なデリゲート型なしで宣言されたイベントでは無効です。
非カスタム イベントとは異なり、`Custom Event`宣言が必要です、`As`句は次のイベント名を明示的にイベントのデリゲート型を指定します。  
  
 非カスタム イベントは、いずれかで定義されている、`As`句と明示的なデリゲート型、またはすぐにパラメーターを持つリスト次のイベント名。  
  
 **エラー ID:** BC31122  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  カスタム イベントと同じパラメーター リストを持つデリゲートを定義します。  
  
     たとえば場合、`Custom Event`で定義された`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`、対応するデリゲートは、次になります。  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2.  カスタム イベントのパラメーターのリストを置き換える、`As`デリゲート型を指定する句。  
  
     先ほどの例では、`Custom Event`宣言を次のように書き換えることができます。  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>例  
 この例で宣言、`Custom Event`し、必要なを指定します`As`デリゲート型を含む句。  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>関連項目
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
