---
title: '方法: アプリケーション セッション間で設定値を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318900"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>方法: アプリケーション セッション間で設定値を変更する
アプリケーションをコンパイルおよび展開後に、アプリケーション セッション間での設定の値を変更する可能性があります。 たとえば、適切なデータベースの場所を指す接続文字列を変更する可能性があります。 アプリケーションをコンパイルおよび展開した後は、デザイン時ツールを使用できない、ために、ファイルに手動で設定値を変更する必要があります。  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>アプリケーション セッション間での設定の値を変更するには  
  
1. Microsoft メモ帳またはいくつかその他のテキスト エディターまたは XML エディターを使用して、アプリケーションに関連する .config ファイルを開きます。  
  
2. 変更する設定のエントリを見つけます。 次の例のようになります。  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. 設定の新しい値を入力し、ファイルを保存します。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [アプリケーション設定の概要](application-settings-overview.md)
