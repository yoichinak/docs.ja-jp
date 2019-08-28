---
title: メッセージ キュー (MSMQ) のインストール
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 118143f2d434e9f4399c3e9141743fc0254b61ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039625"
---
# <a name="installing-message-queuing-msmq"></a>メッセージ キュー (MSMQ) のインストール
メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。  
  
> [!NOTE]
> メッセージ キュー 4.0 は、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では使用できません。  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには  
  
1. サーバーマネージャーで、 **[機能]** をクリックします。  
  
2. 右側のウィンドウの 機能の **[概要]** で、 **[機能の追加]** をクリックします。  
  
3. 結果のウィンドウで、 **[メッセージキュー]** を展開します。  
  
4. **[メッセージキューサービス]** を展開します。  
  
5. **[ディレクトリサービスの統合]** (ドメインに参加しているコンピューターの場合) をクリックし、 **[HTTP サポート]** をクリックします。  
  
6. **[次へ]** をクリックし、 **[インストール]** をクリックします。  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには  
  
1. **[コントロール パネル]** を開きます。  
  
2. **[プログラム]** をクリックし、 **[プログラムと機能]** で **[Windows の機能の有効化または無効化]** をクリックします。  
  
3. [Microsoft Message Queue (MSMQ) Server]、[Microsoft Message Queue (MSMQ) Server Core] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。  
  
    - [MSMQ Active Directory Domain Services Integration] (ドメインに参加するコンピューターの場合)  
  
    - [MSMQ HTTP サポート]  
  
4. **[OK]** をクリックします。  
  
5. コンピューターの再起動を求めるメッセージが表示されたら、 **[OK]** をクリックしてインストールを完了します。  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには  
  
1. **[コントロール パネル]** を開きます。  
  
2. **[プログラムの追加と削除]** をクリックし、 **[Windows コンポーネントの追加]** をクリックします。  
  
3. メッセージキュー を選択し、**詳細** をクリックします。  
  
    > [!NOTE]
    > [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] を実行している場合は、メッセージ キューにアクセスするアプリケーション サーバーを選択します。  
  
4. 詳細ページで、[MSMQ HTTP サポート] オプションが選択されていることを確認します。  
  
5. **[OK]** をクリックして詳細ページを終了し、 **[次へ]** をクリックします。 インストールを完了します。  
  
6. コンピューターの再起動を求めるメッセージが表示されたら、 **[OK]** をクリックしてインストールを完了します。  
  
## <a name="see-also"></a>関連項目

- [セットアップ手順](../../../../docs/framework/wcf/samples/set-up-instructions.md)
