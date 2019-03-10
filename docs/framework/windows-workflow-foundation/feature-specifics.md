---
title: Windows Workflow Foundation の機能仕様
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 4b9a9c5c6395ed27845c8b618e49150a02aa3bda
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721854"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation の機能仕様

[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] は、Windows Workflow Foundation にいくつかの機能を追加します。 このドキュメントでは、いくつかの新機能について説明し、役に立つ可能性のあるシナリオの詳細を示します。

## <a name="messaging-activities"></a>メッセージング アクティビティ

メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive>、 <xref:System.ServiceModel.Activities.SendReply>、 <xref:System.ServiceModel.Activities.Send>、 <xref:System.ServiceModel.Activities.ReceiveReply>)、ワークフローから WCF メッセージを送受信するために使用します。 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>アクティビティが標準の WCF web サービスと同様に、WSDL 経由で公開される Windows Communication Foundation (WCF) サービスの操作を形成するために使用されます。 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> WCF のような web サービスを使用するために使用<xref:System.ServiceModel.ChannelFactory>は**サービス参照の追加**エクスペリエンスは、事前構成済みのアクティビティを生成する Workflow Foundation にも存在します。

### <a name="getting-started-with-messaging-activities"></a>メッセージング アクティビティの概要

- Visual Studio 2012 では、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。 
  <xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアがキャンバスに配置されます。

- クリックし、プロジェクトを右クリックして**サービス参照の追加**します。 既存の web サービス WSDL をポイントしてクリックして**OK**します。 生成されたアクティビティを表示するプロジェクトをビルド (を使用して実装<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>)、ツールボックスにします。

- [ワークフロー サービスのドキュメント](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>メッセージング アクティビティのシナリオ例

A`BestPriceFinder`サービスは、複数の航空会社サービスを特定のルートの最良チケット価格を検索します。 このシナリオを実装するには、メッセージ アクティビティを使用して、価格要求を受信、バックエンド サービスから価格を取得し、価格要求に最良価格で応答することが必要ですが。 最適な価格を計算するためのビジネス ロジックを作成する他の既定のアクティビティを使用する必要も出ています。

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost> (ただし、ワークフローがホストされるためにメッセージングを使用する必要はありません)、複数のインスタンス、構成、および WCF メッセージングをサポートする既定のワークフロー ホストです。 また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。 WCF のと同様に<xref:System.ServiceModel.ServiceHost>、<xref:System.ServiceModel.WorkflowServiceHost>コンソール/WinForms と WPF アプリケーションまたは Windows サービスで自己ホストしたり、web ホスト (.xamlx ファイル) として IIS または WAS でします。

### <a name="getting-started-with-workflow-service-host"></a>ワークフロー サービス ホストの概要

- Visual Studio 2010 で WCF ワークフロー サービス アプリケーション プロジェクトを作成します。 を使用するようこのプロジェクトに設定されます<xref:System.ServiceModel.WorkflowServiceHost>web ホスト環境でします。

- 非メッセージング ワークフローをホストするには、メッセージに基づいてインスタンスを作成するカスタム <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> を追加します。

- ワークフロー インスタンスは、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> を <xref:System.ServiceModel.WorkflowServiceHost> に追加し、<xref:System.ServiceModel.Activities.WorkflowControlClient> を使用することで制御 (中断や終了など) できます。

- 
  <xref:System.ServiceModel.WorkflowServiceHost> のサンプルは次のセクションにあります。

    - [実行](./samples/execution.md)

    - アプリケーションの場合:[中断されたインスタンスの管理](./samples/suspended-instance-management.md)

- [ワークフロー サービスのホストの概要](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost のシナリオ

BestPriceFinder サービスは、複数の航空会社サービスを特定のルートの最良チケット価格を検索します。 このシナリオを実装する必要にワークフローをホスト<xref:System.ServiceModel.WorkflowServiceHost>します。 メッセージ アクティビティを使用しても、価格要求を受信、バックエンド サービスから価格を取得および価格要求に最良価格で応答するには。

## <a name="correlation"></a>相関関係

相関関係は次の 2 つのいずれかです。

- メッセージをグループ化する方法。つまり、要求メッセージとその応答の関係。

- サービス インスタンスにデータの一部をマッピングする方法。

### <a name="getting-started"></a>作業の開始

- 相関を開始するには、Visual Studio で新規プロジェクトを作成します。 <xref:System.ServiceModel.Activities.CorrelationHandle> 型の変数を作成します。

- メッセージのグループ化に使用する相関関係の例は、メッセージをグループ化する要求/応答の相関関係です。

    - <xref:System.ServiceModel.Activities.Receive>アクティビティをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>プロパティを追加し、<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>上記の最初の手順で作成された、CorrelationHandle を使用して。

    - 作成、<xref:System.ServiceModel.Activities.SendReply>アクティビティを右クリックし、 <xref:System.ServiceModel.Activities.Receive> "SendReply の作成" をクリックします。 これをワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティの後に貼り付けます。

- データの一部をサービス インスタンスにマッピングする例は、データの一部 (オーダー ID など) を特定のワークフロー インスタンスにマップするコンテンツ ベースの相関関係です。

    - 任意のメッセージング アクティビティで、`CorrelationInitializers` プロパティをクリックし、上記で作成した <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 変数を使用して <xref:System.ServiceModel.Activities.CorrelationHandle> を追加します。 ドロップダウン メニューで、メッセージ上の目的のプロパティ (OrderID など) をダブルクリックします。 
  `CorrelatesWith` プロパティを上記で使用した <xref:System.ServiceModel.Activities.CorrelationHandle> 変数に設定します。

- [相関関係の概念に関するドキュメント](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>相関関係のシナリオ

注文処理ワークフローを使用して、新規注文の作成とプロセス内にある既存の注文の更新を処理します。 このシナリオを実装する必要にワークフローをホスト<xref:System.ServiceModel.WorkflowServiceHost>とメッセージング アクティビティを使用します。 基づく相関関係が必要になることも、`orderId`に適切なワークフローに更新が行われることを確認します。

## <a name="simplified-configuration"></a>簡略化された構成

WCF 構成スキーマは複雑であり、機能を検索するハードの多くのユーザーを提供します。 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]、WCF ユーザーが次の機能が、サービスを構成する際に役立つを中心に説明しました。

- サービスごとの明示的な構成の必要性をなくします。 いずれかを構成しなかった場合\<service > 要素に、サービスと、サービスに任意のエンドポイントをプログラムで定義されていませんし、サービス コントラクトおよびサービスのベース アドレスごとに 1 つに、一連のエンドポイントが自動的に追加します。サービスによって実装されます。

- 明示的な構成のないサービスに適用される WCF バインディングおよび動作の既定値をユーザーが定義できるようにします。

- 標準のエンドポイントは、事前に構成された再利用可能なエンドポイントを定義します。このエンドポイントは、1 つ以上のエンドポイント プロパティ (アドレス、バインド、およびコントラクト) に対して固定値を持ち、カスタム プロパティを定義できるようにします。

- 最後に、 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF クライアントの構成、構成が選択されているまたはアプリケーション ドメインの読み込み時間後に変更のシナリオで役に立ちますの集中管理することができます。

### <a name="getting-started"></a>作業の開始

- [Wcf 4.0 開発者ガイド](https://go.microsoft.com/fwlink/?LinkId=204940)

- [構成チャネル ファクトリ](https://go.microsoft.com/fwlink/?LinkId=204941)

- [標準エンドポイント要素](https://go.microsoft.com/fwlink/?LinkId=204942)

- [サービス構成の向上では、.Net Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)

- [.NET 4 での一般的なユーザーの誤り:WF と WCF サービスの構成名の入力ミス](https://go.microsoft.com/fwlink/?LinkId=204944)

### <a name="simplified-configuration-scenarios"></a>簡略化された構成のシナリオ

- 経験豊富な ASMX 開発者が WCF の使用を開始しようとするとします。 ただし、WCF は複雑すぎるようです。 構成ファイルに書き込む必要のある情報は何ですか。 .NET 4 では、構成ファイルをまったく使用しないこともできます。

- 既存の WCF サービスのセットは構成とメンテナンスが非常に困難です。 構成ファイルには、変更するのが非常に危険な XML コードが何千行もあります。 コード量を管理しやすい量に減らすための支援が必要です。

## <a name="data-contract-resolver"></a>データ コントラクト リゾルバー

.NET 3.5 では、既知の型の設計にはいくつかの制限がありました。

- シリアル化または逆シリアル化中に既知の型を動的に追加することはできませんでした。

- シリアライザーは不明な xsi:type の情報を処理できませんでした。

- ユーザーは、ネットワーク上のシリアル化インスタンスのサイズを小さくするなど、ネットワーク上に出現する xsi:type を指定できませんでした。

[DataContractResolver](../wcf/samples/datacontractresolver.md) .NET 4.5 でこれらの問題を解決します。

### <a name="getting-started"></a>作業の開始

- [データ コントラクト リゾルバー API のドキュメント](https://go.microsoft.com/fwlink/?LinkId=204946)

- [データ コントラクト リゾルバーの概要](https://go.microsoft.com/fwlink/?LinkId=204947)

- サンプル:

    - [DataContractResolver](../wcf/samples/datacontractresolver.md)

    - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>データ コントラクト リゾルバーのシナリオ

- 数十の <xref:System.Runtime.Serialization.KnownTypeAttribute> オブジェクトをサービスで宣言する必要性の回避。

- XML BLOB のサイズの削減。

## <a name="flowchart"></a>フローチャート

フローチャートは、ドメインの問題を視覚的に表すための既知のパラダイムです。 これは .NET の 4 で導入される新しい制御フロー スタイルです。 フローチャートの主な特性は、一度に 1 つのアクティビティのみ実行されることです。 フローチャートはループと代替結果を表すことができますが、その性質上、複数ノードの同時実行を表すことはできません。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 では、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーにフローチャートを追加します。

- フローチャート機能では、次のクラスを使用します。

    - <xref:System.Activities.Statements.Flowchart>

    - <xref:System.Activities.Statements.FlowNode>

    - <xref:System.Activities.Statements.FlowDecision>

    - <xref:System.Activities.Statements.FlowStep>

    - <xref:System.Activities.Statements.FlowSwitch%601>

- サンプル:

    - [TryCatch を使用した Flowchart アクティビティでのエラー処理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

    - [雇用プロセス](./samples/hiring-process.md)

- デザイナー ドキュメント:

    - [フローチャート アクティビティ デザイナー](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>フローチャートのシナリオ

フローチャート アクティビティを使用して推測ゲームを実装できます。 推測ゲームは非常に単純です。コンピューターによってランダムな数値が選択され、プレーヤーはその数値を推測する必要があります。 プレーヤーが推測を送信するとき、コンピューターが表示されます (つまり"試行数が小さい) ヒント。 プレーヤーが 6 回以下で数値を見つけた場合は、特別な祝福のメッセージが表示されます。 このゲームは、次の手続き型アクティビティの組み合わせで実装できます。

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>手続き型アクティビティ (Sequence、If、ForEach、Switch、Assign、DoWhile、While)

手続き型アクティビティは、プログラマになじみのある概念を使用してシーケンシャル制御フローをモデル化するメカニズムを提供します。 これらのアクティビティにより、従来の構造型プログラミング言語構成要素が有効になり、該当する場合には C#/VB などの一般的な手続き型言語と同等の言語が提供されます。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 では、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで、手続き型アクティビティを追加します。

- サンプル:

    - [雇用プロセス](./samples/hiring-process.md)

    - [企業の購買プロセス](./samples/corporate-purchase-process.md)

- デザイナー ドキュメント:

    - [Parallel アクティビティ デザイナー](/visualstudio/workflow-designer/parallel-activity-designer)

    - [ParallelForEach\<T > アクティビティ デザイナー](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>手続き型アクティビティのシナリオ

- <xref:System.Activities.Statements.Parallel>:イントラネット ドキュメント管理システムでは、ドキュメント承認ワークフローが。 ドキュメントは、イントラネットに公開する前に、複数の部門の担当者によって承認する必要があります。 承認; の確立された注文がないです。「承認保留」フェーズで、ドキュメントには、いつでもが発生することができます。 ユーザーがレビューのためにドキュメントを送信した場合は、直属のマネージャー、イントラネット管理者、および内部コミュニケーション マネージャーがそのドキュメントを承認する必要があります。

- <xref:System.Activities.Statements.ParallelForEach%601>:WF アプリケーションでは、大企業内の企業購買を管理します。 企業の規則では、購買作業を計画する前に 3 社の異なるベンダーを評価する必要があると規定されています。 購買部門の従業員は、企業のベンダー リストから 3 社のベンダーを選択します。 これらのベンダーを選択し、通知した後で、企業は経済提案書を待ちます。 提案書は任意の順序で到着します。 WF でこのシナリオを実装するには、ベンダーのコレクションを反復処理して経済提案書を求める <xref:System.Activities.Statements.ParallelForEach%601> を使用します。 すべての提案が収集された後で、最良の提案が選択されて表示されます。

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> アクティビティでは、オブジェクト内のパブリック メソッドまたはスコープ内の型を呼び出すことができます。 パラメーター付きまたはパラメーターなし (パラメーター配列を含む) でのインスタンス メソッドおよび静的メソッドの呼び出し、および汎用メソッドの呼び出しがサポートされます。 メソッドを同期および非同期で実行することもできます。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 では、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーに <xref:System.Activities.Statements.InvokeMethod> アクティビティを追加し、そこに静的メソッドとインスタンス メソッドを構成します。

- デザイナー ドキュメント:[InvokeMethod アクティビティ デザイナー](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>InvokeMethod のシナリオ

- スコープ内のオブジェクトのメソッドを呼び出す必要があります。 たとえば、辞書に値を追加する必要があります。 辞書のインスタンスの Add メソッドが呼び出され、キーと値が指定されます。

- レガシー CLR オブジェクトに対してメソッドを呼び出す必要があります。 カスタム アクティビティを作成してそのレガシー クラスの呼び出しをラップする代わりに、ワークフロー実行中にそのクラスがスコープ内にある場合には <xref:System.Activities.Statements.InvokeMethod> を使用できます。

## <a name="error-handling-activities"></a>エラー処理アクティビティ

<xref:System.Activities.Statements.TryCatch> アクティビティには、含まれるアクティビティのセットの実行中に発生する例外をキャッチするメカニズムが用意されています (C#/VB の Try/Catch コンストラクトに類似)。 <xref:System.Activities.Statements.TryCatch> はワークフロー レベルの例外処理を提供します。 ハンドルされていない例外がスローされると、ワークフローが中止され、Finally ブロックは実行されません。 この動作は C# と一貫性があります。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 では、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで <xref:System.Activities.Statements.TryCatch> アクティビティを追加します。

- サンプル:[TryCatch を使用した Flowchart アクティビティでのエラー処理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- デザイナー ドキュメント:[エラー処理アクティビティ デザイナー](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>エラー処理のシナリオ

アクティビティのセットを実行する必要があり、エラーの発生時に特定のロジックを実行する必要があります。 そのエラー処理ロジック中にエラーが回復不能であることがわかった場合は、例外が再スローされ、親アクティビティ (またはホスト) によって問題が処理されます。

## <a name="pick-activity"></a>Pick アクティビティ

<xref:System.Activities.Statements.Pick> アクティビティは、WF でイベント ベースの制御フロー モデリングを提供します。 <xref:System.Activities.Statements.Pick> には、多数の分岐が含まれています。各分岐は、特定のイベントが発生すると実行されます。 この設定では、<xref:System.Activities.Statements.Pick> は、アクティビティがリッスンしているイベント セットの 1 つのみを実行する <xref:System.Activities.Statements.Switch%601> と同様に動作します。 各分岐はイベント ドリブンなので、発生したイベントが対応する分岐を実行します。 他のすべての分岐は、イベントのリッスンをキャンセルし、停止します。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 では、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで <xref:System.Activities.Statements.Pick> アクティビティを追加します。

- サンプル:[Pick アクティビティの使用](./samples/using-the-pick-activity.md)

- デザイナー ドキュメント:[Pick アクティビティ デザイナー](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Pick のシナリオ

ユーザーに入力を求めるプロンプトを表示する必要があります。 通常の状況下では、開発者は <xref:System.Console.ReadLine%2A> のようなメソッド呼び出しを使用してユーザーの入力を求めます。 この設定の問題は、ユーザーが何か入力するまでプログラムが待機することです。 このシナリオでは、ブロッキング アクティビティのブロックを解除するためにタイムアウトが必要です。 一般的なシナリオでは、特定の期間内にタスクが完了する必要があります。 ブロッキング アクティビティのタイムアウトは、Pick が大量の値を追加するシナリオです。

## <a name="wcf-routing-service"></a>WCF ルーティング サービス

ルーティング サービスは一般的なソフトウェア ルーター、クライアントとサービス間の WCF メッセージのフローを制御するために設計されています。 ルーティング サービスできます、サービスからクライアントを分離するために、構成の観点からさらに多くの自由を提供するサービスをホストする方法を検討する場合がある場合、柔軟性をサポートすることができます。 .NET 3.5 では、クライアントとサービスが密接に結び付いています。クライアントは、すべてのサービスとの対話に必要し、していた場所について知っておく必要があります。 また、.Net Framework 3.5 の WCF には次の制限がありました。

- ロジックをクライアントにハードコーディングする必要があったため、エラー処理が複雑でした。

- クライアントとサービスは常に同じバインディングを使用する必要がありました。

- サービスが適切に分類されていることはほとんどありませんでした。複数のサービス間で選択するよりも、クライアントがすべてを実装する 1 つのサービスと対話する方が簡単です。

.Net 4 のルーティング サービスは、これらの問題を簡単に解決できるように設計されています。 新しいルーティング サービスには次の機能があります。

1. コンテント ベースのルーティング (<xref:System.ServiceModel.Dispatcher.MessageFilter> オブジェクトがメッセージを調べて送信先を判断します。)

2. プロトコル ブリッジ (トランスポートとメッセージ)

3. エラー処理 (ルーターは、通信例外をキャッチし、バックアップ エンドポイントにフェールオーバーします)

4. <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> およびルーティング構成の動的 (メモリ内) 更新。

### <a name="getting-started"></a>作業の開始

1. ドキュメント:[ルーティング](../wcf/feature-details/routing.md)

2. サンプル:[ルーティング サービス&#91;WCF サンプル&#93;](../wcf/samples/routing-services.md)

3. ブログ:[ルーティング規則。](https://go.microsoft.com/fwlink/?LinkId=204956)

### <a name="routing-scenarios"></a>ルーティング シナリオ

ルーティング サービスは、次のシナリオに役立ちます。

- クライアントは、複数のサービスを直接アドレス指定することなく、これらのサービスと対話できます。

- クライアントは、ルーティング先を判断するためにクライアント要求で追加のロジックを実行できます。

- クライアントをリファクタリングすることなく、クライアントが実行する操作を複数のサービス実装に分解します。

- クライアントとサービスは、異なるセキュリティ設定の異なるバインディングで会話できます。

- クライアントは、障害またはサービスの使用不能に対してより堅牢になることができます。

## <a name="wcf-discovery"></a>WCF Discovery

WCF Discovery に、アプリケーションのインフラストラクチャに探索メカニズムを組み込むことができるフレームワーク テクノロジです。 これを使用して、サービスを探索可能にし、サービスを検索するようにクライアントを構成できます。 クライアントはエンドポイントでハードコーディングする必要がなくなるため、アプリケーションはより堅牢になりフォールト トレランスが向上します。 探索は、アプリケーションに自動構成機能をビルドするための最適なプラットフォームです。

製品は、WS-Discovery 標準の上に構築されます。 相互運用可能、拡張可能、および汎用的になるように設計されています。 製品では 2 つの操作モードがサポートされます。

1. マネージド: 既存のサービスに関する知識を持つエンティティがネットワーク上にあり、クライアントは情報を直接クエリします。 これは Active Directory に類似しています。

2. アドホック: クライアントはマルチキャスト メッセージを使用してサービスを特定します。

さらに、探索メッセージはネットワーク プロトコルに依存しません。モード要件をサポートする任意のプロトコル上でこれらを使用できます。 たとえば、探索マルチキャスト メッセージを UDP チャネルまたはマルチキャスト メッセージングをサポートするその他のネットワークを介して送信されることができます。 これらの設計ポイント機能の柔軟性と組み合わせて、ソリューションに探索を適応させることができます。

### <a name="getting-started"></a>作業の開始

- ドキュメント:[WCF Discovery](../wcf/feature-details/wcf-discovery.md)

- サンプル:[探索 (サンプル)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>探索のシナリオ

サービスがいつ使用可能になるかが不明なため、開発者はエンドポイントのハードコーディングを望みません。 代わりに、開発者は実行時にサービスを選択することを望んでいます。 アプリケーションのコンポーネント間に、切り離し、堅牢性、および自動構成がさらに必要です。

## <a name="tracking"></a>追跡

ワークフロー追跡では、ワークフロー インスタンスの実行に関する洞察を提供します。 追跡イベントは、ワークフロー インスタンス レベルで、ワークフロー内のアクティビティの実行時にワークフローから出力されます。 追跡レコードを定期受信するにはワークフロー追跡参加要素をワークフロー ホストに追加する必要があります。 追跡レコードは、追跡プロファイルを使用してフィルター処理されます。 .Net Framework には ETW (Event Tracing for Windows) 追跡参加要素が用意されており、基本プロファイルが machine.config ファイルにインストールされます。

### <a name="getting-started"></a>作業の開始

1. Visual Studio 2010 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。 開始するキャンバスに <xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアが配置されます。

2. web.config を開き、プロファイルなしで ETW 追跡動作を追加します。

    1. 既定のプロファイルが使用されます。

    2. イベント ビューアーを開き、次のノードで分析チャネルを有効にします。**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 右クリック**分析**選択**ログの有効化**します。

    3. ワークフロー サービスを実行します。

    4. イベント ビューアーでワークフロー追跡イベントを確認します。

3. サンプル:[追跡](./samples/tracking.md)

4. 概念説明のドキュメント:[ワークフローの追跡とトレース](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>SQL Workflow Instance Store

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は、SQL Server ベースのインスタンス ストアの実装です。 インスタンス ストアは、実行中のインスタンスの状態を、そのインスタンスの読み込みと再開に必要なすべてのデータと共に格納します。 サービス ホストは、ワークフローが永続的な場合にインスタンス状態を保存するようインスタンス ストアに指示し、そのインスタンスのメッセージが到着するか遅延アクティビティが期限切れになったときにインスタンス状態を読み込むようインスタンス ストアに指示します。

### <a name="getting-started"></a>作業の開始

1. Visual Studio 2012 で、暗黙的または明示的なを含むワークフロー作成<xref:System.Activities.Statements.Persist>アクティビティ。 
  <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 動作をワークフロー サービス ホストに追加します。 これはコードまたはアプリケーション構成ファイルで行うことができます。

2. サンプル:[永続性](./samples/persistence.md)

3. 概念説明のドキュメント:[SQL Workflow Instance Store](sql-workflow-instance-store.md)します。
