---
title: '方法: アプリケーション セッション間での設定の値を変更します。'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: c1626cea581e5c180665d0ce805dea3e67f27a05
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714360"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>方法: アプリケーション セッション間での設定の値を変更します。
アプリケーションをコンパイルおよび展開後に、アプリケーション セッション間での設定の値を変更する可能性があります。 たとえば、適切なデータベースの場所を指す接続文字列を変更する可能性があります。 アプリケーションをコンパイルおよび展開した後は、デザイン時ツールを使用できない、ために、ファイルに手動で設定値を変更する必要があります。  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>アプリケーション セッション間での設定の値を変更するには  
  
1.  Microsoft メモ帳またはいくつかその他のテキスト エディターまたは XML エディターを使用して、アプリケーションに関連する .config ファイルを開きます。  
  
2.  変更する設定のエントリを見つけます。 次の例のようになります。  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  設定の新しい値を入力し、ファイルを保存します。  
  
## <a name="see-also"></a>関連項目
- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [アプリケーション設定の概要](application-settings-overview.md)
