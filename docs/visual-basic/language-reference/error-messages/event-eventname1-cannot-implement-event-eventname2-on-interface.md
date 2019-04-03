---
title: デリゲート型 '<eventname1>' および '<eventname2>' が一致しないため、イベント '<interface>' はインターフェイス '<delegate1>' 上のイベント '<delegate2>' を実装できません。
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 9581168fa86f8f0715e004b60c2eb2a813cd38ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840524"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>イベント '\<eventname1 >' イベントを実装することはできません'\<eventname2 >' インターフェイスで '\<インターフェイス >' ため、デリゲート型の\<delegate1 >' と'\<delegate2 >' と一致しません。
イベントのデリゲート型がインターフェイスでイベントのデリゲート型と一致しないために、Visual Basic では、イベントを実装できません。 このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。 実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。  
  
 **エラー ID:** BC31423  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   イベントを個別に実装します。  
  
     または  
  
-   インターフェイスを使用して、イベントを定義、`As`構文と同じデリゲート型を指定します。  
  
## <a name="see-also"></a>関連項目

- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
