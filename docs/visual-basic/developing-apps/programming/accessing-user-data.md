---
title: ユーザー データへのアクセス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
ms.openlocfilehash: e5d18adcb331162a72da0adb4018d1d59ecc072e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825301"
---
# <a name="accessing-user-data-visual-basic"></a>ユーザー データへのアクセス (Visual Basic)
このセクションには、`My.User` オブジェクトとそれで実行できるタスクに関するトピックが含まれています。  
  
 `My.User` オブジェクトを利用すれば、<xref:System.Security.Principal.IPrincipal> インターフェイスを実装するオブジェクトを返すことで、ログオン ユーザーに関する情報にアクセスできます。  
  
## <a name="tasks"></a>[タスク]  
  
|終了|解決方法については、|  
|--------|---------|  
|ユーザーのログイン名を取得する|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|アプリケーションで Windows 認証が使用される場合、ユーザーのドメイン名を取得する|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|ユーザーの役割を判断する|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.User>
