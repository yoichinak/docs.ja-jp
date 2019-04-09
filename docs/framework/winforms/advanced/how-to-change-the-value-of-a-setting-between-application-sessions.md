---
title: '方法: アプリケーション セッション間で設定値を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 03a10e95362b1d49e4929c07ab6193f53898d34f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142858"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>方法: アプリケーション セッション間で設定値を変更する
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
