---
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913161"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>派生クラスで基本クラスのイベントを発生させることはできません。
イベントを発生させることができるのは、それが宣言されている宣言領域からのみです。 そのため、クラスは、派生元のクラスであっても、他のクラスからイベントを発生させることはできません。  
  
 **エラー ID:** BC30029  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `Event` ステートメントまたは `RaiseEvent` ステートメントが同じクラス内になるように移動します。  
  
## <a name="see-also"></a>関連項目

- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
