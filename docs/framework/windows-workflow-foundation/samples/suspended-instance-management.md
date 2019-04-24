---
title: 中断されたインスタンスの管理
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: ace4d2baef8f6b030790deaa5b1c20bb4b0cd30d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319561"
---
# <a name="suspended-instance-management"></a>中断されたインスタンスの管理
このサンプルでは、中断されているワークフロー インスタンスを管理する方法を示します。  <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> の既定のアクションは `AbandonAndSuspend` です。 つまり、既定では、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー インスタンスからスローされた未処理の例外により、インスタンスがメモリから破棄され、インスタンスの永続バージョンが中断状態としてマークされることになります。 中断されたワークフロー インスタンスは、中断が解除されるまで実行できません。

 このサンプルでは、コマンド ライン ユーティリティを実装して、中断されたインスタンスについてクエリを実行する方法、およびユーザーがインスタンスを再開または終了できるようにする方法を示します。 このサンプルでは、ワークフロー サービスから例外が意図的にスローされ、中断状態になります。 その後、コマンド ライン ユーティリティを使用してインスタンスについてクエリを実行し、さらに、インスタンスを再開または終了できます。

## <a name="demonstrates"></a>使用例
 <xref:System.ServiceModel.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>と<xref:System.ServiceModel.Activities.WorkflowControlEndpoint>Windows Workflow foundation (WF)。

## <a name="discussion"></a>説明
 このサンプルに実装されているコマンド ライン ユーティリティは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に用意されている SQL インスタンス ストアの実装に固有のものです。 インスタンス ストアのカスタム実装がある場合は、サンプルの `WorkflowInstanceCommand` の実装を、使用しているインスタンス ストアに固有の実装に置き換えることで、このユーティリティを調整できます。

 用意されている実装では、SQL インスタンス ストアに対して SQL コマンドを直接実行して、中断されたインスタンスのリストを取得し、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> に追加された <xref:System.ServiceModel.WorkflowServiceHost> を使用して、インスタンスを再開または終了できるようにします。

#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. このサンプルでは、次の Windows コンポーネントが有効になっている必要があります。

    1.  Microsoft メッセージ キュー (MSMQ) サーバー

    2.  SQL Server Express

2. SQL Server データベースを設定します。

    1.  Visual Studio 2010 コマンド プロンプトでは、次の SuspendedInstanceManagement サンプル ディレクトリから"setup.cmd"を実行します。

        1.  SQL Server Express を使用して永続性データベースを作成します。 永続性データベースが既に存在する場合、データベースは削除され、再作成されます。

        2.  永続化のためにデータベースを設定します。

        3.  IIS APPPOOL\DefaultAppPool および NT AUTHORITY\Network Service を、永続化のためにデータベースを設定するときに定義された InstanceStoreUsers ロールに追加します。

3. サービス キューを設定します。

    1.  Visual Studio 2010 で右クリックし、 **SampleWorkflowApp**プロジェクトし、クリックして**スタートアップ プロジェクトとして設定**します。

    2.  コンパイルしてキーを押して SampleWorkflowApp を実行**F5**します。 これにより、必要なキューが作成されます。

    3.  キーを押して**Enter** SampleWorkflowApp を停止します。

    4.  コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。

    5.  展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**します。

    6.  右クリックして、 **ReceiveTx**キューし、選択**プロパティ**します。

    7.  選択、**セキュリティ**でき、タブ**Everyone**へのアクセス許可を持つ**メッセージの受信**、**メッセージのピーク**、および**メッセージを送信**します。

4. サンプルを実行します。

    1.  Visual Studio 2010、SampleWorkflowApp プロジェクトを再実行を押してデバッグなし**Ctrl + F5**します。 2 つのエンドポイント アドレスがコンソール ウィンドウに出力されます。1 つはアプリケーション エンドポイントのアドレスで、もう 1 つは <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> のアドレスです。 その後、ワークフロー インスタンスが作成され、そのインスタンスの追跡レコードがコンソール ウィンドウに表示されます。 ワークフロー インスタンスから例外がスローされ、インスタンスは中断されて中止されます。

    2.  次に、コマンド ライン ユーティリティを使用して、これらのインスタンスに対してさらに操作を実行できます。 コマンド ライン引数の構文は次のとおりです。

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         サポートされるコマンドは、`Query`、`Resume`、および `Terminate` です。  InstanceId スイッチを指定する必要があるのは、`Resume` 操作および `Terminate` 操作だけです。

#### <a name="to-cleanup-optional"></a>クリーンアップするには (省略可能)

1. `vs2010` コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。

2. 展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**します。

3. 削除、 **ReceiveTx**キュー。

4. 永続性データベースを削除するには、cleanup.cmd を実行します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
