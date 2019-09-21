---
title: メッセージ フローの概要
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: 0bfbd1523f1d5db4a94cf3af03a03779af14655d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795972"
---
# <a name="message-flow-overview"></a>メッセージ フローの概要
相互接続されたサービスを持つ分散システムでは、サービス間の因果関係を調べる必要があります。 状態監視、トラブルシューティング、根本原因分析などの重要なシナリオをサポートするには、要求フローに含まれるさまざまなコンポーネントを理解することが重要です。 .NET Framework 4 では、多様なサービス間でトレースを関連付けることができるように、次の機能のサポートが追加されています。

- 分析トレース:Windows イベントトレーシング (ETW) を使用した高パフォーマンスで低レベルの詳細トレース機能。

- WCF/WF サービスのエンドツーエンドアクティビティモデル:この機能は、 <xref:System.ServiceModel>名前空間および<xref:System.Workflow.ComponentModel>名前空間によって生成されるトレースの相関関係をサポートします。

- WF の ETW 追跡:この機能は、WF サービスによって生成された追跡レコードを使用して、ワークフローの現在の状態と進行状況を可視化します。

 追跡レコードまたはトレース レコードに記録されたエラーを使用して、コード障害や誤った形式のメッセージを検出できます。 エラー状態のアクティビティの特定には、イベントのメッセージ ヘッダーにある Correlation ノードの ActivityId プロパティを使用することができます。 アクティビティ ID によるメッセージフローのトレースを有効にするには、「[メッセージフローのトレースの構成](./etw/configuring-message-flow-tracing.md)」を参照してください。 このトピックでは、チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にする方法を示します。

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>チュートリアル入門で作成されたプロジェクトでメッセージ フローのトレースを有効にするには

1. **[開始]** 、 **[実行]** の順に`eventvwr.exe`クリックしてイベントビューアーを開き、「」と入力します。

2. 分析トレースを有効にしていない場合は、 **[アプリケーションとサービスログ]** 、 **[Microsoft]** 、 **[Windows]** 、 **[アプリケーションサーバー-アプリケーション]** の順に展開します。 **[表示]** 、 **[分析およびデバッグログの表示]** を選択します。 **[分析]** を右クリックし、 **[ログを有効にする]** を選択します。 トレースが表示されるように、イベント ビューアーを開いたままにします。

3. Visual Studio 2012 の[はじめにチュートリアル](../getting-started-tutorial.md)で作成したサンプルを開きます。 サービスを作成できるようにするには、Visual Studio 2012 を管理者として実行する必要があることに注意してください。 WCF サンプルがインストールされている場合は、チュートリアルで作成した完成したプロジェクトを含む[はじめに](../samples/getting-started-sample.md)を開くことができます。

4. **サービス**プロジェクトを右クリックし、 **[追加]** 、 **[新しい項目]** の順に選択します。 **[アプリケーション構成ファイル]** を選択し、 **[OK]** をクリックします。

5. 上の手順で作成した App.Config ファイルに次のコードを追加します。

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Ctrl キーを押しながら F5 キーを押して、サーバー アプリケーションをデバッグなしで実行します。 **クライアントプロジェクト**を右クリックし、 **[デバッグ]** 、 **[新しいインスタンスを開始]** の順に選択して、クライアントプロジェクトを実行します。

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

10. **分析**ログを更新して確認します。  イベント ID が 220 のイベントを探します。  イベントを選択し、プレビューウィンドウの **[詳細]** タブをクリックします。 このイベントには、呼び出し元アクティビティの相関 ID が含まれています。

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    > ActivityID に同じ GUID を持つすべてのイベントは、1 つの要求に関連しています。 これは、特定のクライアントから特定のサービスへメッセージを関連付けるために使用できます。 このクライアントが別のサービスを呼び出した場合、同じクライアントが ActivityID によって識別されます。

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
    > 転送イベントは、アクティブな ActivityID が、ActivityID として指定された GUID から RelatedActivityID として指定された GUID に変更されたことを記録します。 転送イベントの生成後は、すべてのイベントに新しい GUID が ActivityID として格納されます。
