---
title: "'<eventname>' はイベントであるため、直接呼び出すことはできません。"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803323"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname>' はイベントであるため、直接呼び出すことはできません
'<`eventname`>' はイベントであるため、直接呼び出すことはできません。 `RaiseEvent` ステートメントを使用して、イベントを発生させます。  
  
 プロシージャ呼び出しは、プロシージャ名のイベントを指定します。 イベント ハンドラーはプロシージャですが、イベント自体はシグナル通知デバイスであり、これを発生させて処理する必要があります。  
  
 **エラー ID:** BC32022  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `RaiseEvent` ステートメントを使用して、イベントを通知し、それを処理するプロシージャを呼び出します。  
  
## <a name="see-also"></a>関連項目

- [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
