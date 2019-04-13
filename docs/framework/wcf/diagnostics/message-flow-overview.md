---
title: メッセージ フローの概要
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: d75a535a601612196ef66151a4685723e048848f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312645"
---
# <a name="message-flow-overview"></a>メッセージ フローの概要
相互接続されたサービスを持つ分散システムでは、サービス間の因果関係を調べる必要があります。 状態監視、トラブルシューティング、根本原因分析などの重要なシナリオをサポートするには、要求フローに含まれるさまざまなコンポーネントを理解することが重要です。 .NET Framework 4 では、多様なサービス間でトレースを関連付けることができるように、次の機能のサポートが追加されています。

-   分析トレース:高パフォーマンスと Event Tracing for Windows (ETW) を使用して、詳細度は低いトレース機能。

-   WCF/WF サービス用のエンド ツー エンド アクティビティ モデル:この機能によって生成されたトレースの相関関係をサポートする、<xref:System.ServiceModel>と<xref:System.Workflow.ComponentModel>名前空間。

-   WF の ETW 追跡:この機能は、ワークフローの現在の状態と進行状況を可視化を提供するのに WF サービスによって生成された追跡レコードを使用します。

 追跡レコードまたはトレース レコードに記録されたエラーを使用して、コード障害や誤った形式のメッセージを検出できます。 エラー状態のアクティビティの特定には、イベントのメッセージ ヘッダーにある Correlation ノードの ActivityId プロパティを使用することができます。 アクティビティの ID でメッセージ フローのトレースを有効にするのを参照してください。 [Configuring Message Flow Tracing](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)します。 このトピックでは、チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にする方法を示します。

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にするには

1. クリックしてイベント ビューアーを開いて**開始**、**実行**、入力と`eventvwr.exe`します。

2. 分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 選択**ビュー**、 **分析およびデバッグ ログ**します。 右クリック**分析**選択**ログの有効化**します。 トレースが表示されるように、イベント ビューアーを開いたままにします。

3. 作成したサンプルを開き、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)Visual Studio 2012。 実行することする必要があります Visual Studio 2012 を管理者として、サービスを作成できるように注意してください。 WCF サンプルをインストールした場合は、開く、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)を含む、完成したプロジェクトのチュートリアルで作成します。

4. 右クリックし、**サービス**順に選択して**追加**、**新しい項目の**します。 選択**アプリケーション構成ファイル** をクリック**OK**します。

5. 上の手順で作成した App.Config ファイルに次のコードを追加します。

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Ctrl キーを押しながら F5 キーを押して、サーバー アプリケーションをデバッグなしで実行します。 右クリックし、クライアント プロジェクトを実行、**クライアント**プロジェクトと選択**デバッグ**、**新しいインスタンスを開始**します。

7. クライアントからサーバーへのイベントをトレースするには、Client プロジェクトのアプリケーション構成ファイルに次の内容を追加します。

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. クライアントの Program.cs に、次の Using ステートメントを追加します。

    ```csharp
    using System.Diagnostics;
    ```

9. Client プロジェクトの program.cs ファイルにある Main メソッドで、トレース GUID をイベント ログに伝達するように設定します。

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. 更新を調べ、**分析**ログ。  イベント ID が 220 のイベントを探します。  イベントを選択し、**詳細**プレビュー ペインでタブ。 このイベントには、呼び出し元アクティビティの相関 ID が含まれています。

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    >  ActivityID に同じ GUID を持つすべてのイベントは、1 つの要求に関連しています。 これは、特定のクライアントから特定のサービスへメッセージを関連付けるために使用できます。 このクライアントが別のサービスを呼び出した場合、同じクライアントが ActivityID によって識別されます。

11. 場合によっては、ActivityID が元の GUID から新しい ActivityID に変更されます。 その場合、転送イベントが生成されます。 このイベント ID は 499 で、イベントのヘッダーに次のデータが格納されます。

    ```xml
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
        <System>
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />
            <EventID>499</EventID>
            ...
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />
            ...
       </System>
    </Event>
    ```

    > [!NOTE]
    >  転送イベントは、アクティブな ActivityID が、ActivityID として指定された GUID から RelatedActivityID として指定された GUID に変更されたことを記録します。 転送イベントの生成後は、すべてのイベントに新しい GUID が ActivityID として格納されます。
