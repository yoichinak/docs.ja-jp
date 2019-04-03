---
title: 派生クラスで基本クラスのイベントを発生させることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835142"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>派生クラスで基本クラスのイベントを発生させることはできません。
宣言されている宣言領域からのみイベントを発生させることができます。 そのため、クラスは、その他のクラスを派生元であるものも含めてからイベントを発生させることはできません。  
  
 **エラー ID:** BC30029  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   移動、`Event`ステートメントまたは`RaiseEvent`ステートメント、同じクラスにされるためです。  
  
## <a name="see-also"></a>関連項目

- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
