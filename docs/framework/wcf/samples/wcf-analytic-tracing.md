---
title: WCF 分析トレース
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 9ed89bdbe2469a96f2a959c9fda8442e80b6f7ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332314"
---
# <a name="wcf-analytic-tracing"></a>WCF 分析トレース
このサンプルは、Windows Communication Foundation (WCF) が ETW に書き込む分析トレースのストリームに独自のトレース イベントを追加する方法を示します[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]します。 分析トレースは、パフォーマンスを低下させずに簡単にサービスを確認できるようにするためのものです。 このサンプルは、使用する方法を示します、 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> Api を WCF サービスと統合されるイベントを記述します。  
  
 詳細については、 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> Api を参照してください<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>します。  
  
 Windows でのイベント トレースの詳細についてを参照してください。[デバッグの向上およびパフォーマンス調整 ETW を](https://go.microsoft.com/fwlink/?LinkId=166488)します。  
  
## <a name="disposing-eventprovider"></a>EventProvider の破棄  
 このサンプルでは、<xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> を実装した <xref:System.IDisposable?displayProperty=nameWithType> クラスを使用します。 WCF サービスのトレースを実装するときに使用できる可能性がありますが、<xref:System.Diagnostics.Eventing.EventProvider>のサービスの有効期間にわたってリソース。 そのため、読みやすくするためにも、このサンプルでは、ラップされた <xref:System.Diagnostics.Eventing.EventProvider> を破棄しません。 何かの理由で、サービスに対して別のトレースの要件を設定し、このリソースを破棄しなければならない場合は、アンマネージ リソースの破棄に関するベスト プラクティスに従ってこのサンプルを変更してください。 アンマネージ リソースを破棄に関する詳細については、次を参照してください。 [Dispose メソッドの実装](https://go.microsoft.com/fwlink/?LinkId=166436)します。  
  
## <a name="self-hosting-vs-web-hosting"></a>自己ホスト型と Web ホスト  
 Web ホスト サービスでは、WCF の分析トレースは、"HostReference"は、サービスは、トレースの出力を識別するために使用をという名前のフィールドを指定します。 拡張可能なユーザー トレースをこのモデルに加えることができます。このサンプルで、そのためのベスト プラクティスを示します。 Web ホストの形式を参照場合に、パイプ '&#124;' 文字が実際には、最終的な表示文字列は、次のいずれかを指定できます。  
  
-   アプリケーションがルート以外にある場合  
  
     \<サイト名 >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   アプリケーションがルートにある場合  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 自己ホスト型サービスは、WCF の分析トレースで"HostReference"フィールドは設定されません。 このサンプルの `WCFUserEventProvider` クラスは、自己ホスト型サービスで使用した場合も同じように動作します。  
  
## <a name="custom-event-details"></a>カスタム イベントの詳細  
 WCF の ETW イベント プロバイダー マニフェストでは、サービス コード内から WCF サービスの作成者によって生成されるように設計された 3 つのイベントを定義します。 次の表に、その 3 つのイベントの概要を示します。  
  
|event|説明|イベント ID|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|このイベントは、問題以外の通知すべき処理がサービスで発生した場合に生成します。 たとえば、データベースの呼び出しに成功した後にイベントを生成します。|301|  
|UserDefinedWarningOccurred|このイベントは、後続の処理でエラーになる可能性がある問題が発生した場合に生成します。 たとえば、データベースの呼び出しが失敗したものの、冗長なデータ ストアを使用して回復できた場合に警告イベントを生成します。|302|  
|UserDefinedErrorOccurred|このイベントは、サービスが想定どおりに動作しなかった場合に生成します。 たとえば、データベースの呼び出しが失敗し、別の場所からもデータを取得できなかった場合にイベントを生成します。|303|  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1. Visual Studio 2012 を使用して、WCFAnalyticTracingExtensibility.sln ソリューション ファイルを開きます。  
  
2. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3. ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで次のようにクリックします。 **[calculator.svc]** します。 サービスの WSDL ドキュメントの URI がブラウザーに表示されます。 その URI をコピーします。  
  
4. WCF テスト クライアント (WcfTestClient.exe) を実行します。  
  
     WCF テスト クライアント (WcfTestClient.exe) は`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`します。 既定の Visual Studio 2012 のインストール ディレクトリは`C:\Program Files\Microsoft Visual Studio 10.0`します。  
  
5. 選択して、サービスを追加、WCF テスト クライアント内で**ファイル**、し**サービスの追加**します。  
  
     入力ボックスにエンドポイントのアドレスを追加します。  
  
6. クリックして**OK**ダイアログ ボックスを閉じます。  
  
     下の左ペインで、ICalculator サービスが追加された**マイ サービス プロジェクト**します。  
  
7. イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、WCF サービスから生成された追跡イベントのイベント ログがリッスンしていることを確認します。  
  
8. **開始**メニューの **管理ツール**、し**イベント ビューアー**します。 有効にする、**分析**と**デバッグ**ログ。  
  
9. イベント ビューアーのツリー ビューでに移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、。**アプリケーション サーバー-アプリケーション**します。 右クリックして**アプリケーション サーバー-アプリケーション**を選択します**ビュー**、し**分析およびデバッグ ログ**します。  
  
     いることを確認、 **分析およびデバッグ ログ**オプションをオンにします。 有効にする、**分析**ログ。  
  
     イベント ビューアーのツリー ビューでに移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 。**アプリケーション サーバー-アプリケーション**、し**分析**します。 右クリック**分析**選択**ログの有効化**します。  
  
10. WCF テスト クライアントを使用してサービスをテストします。  
  
    1.  WCF テスト クライアントでのダブルクリック**Add()** ICalculator サービス ノードの下。  
  
         **Add()** メソッドが 2 つのパラメーターと共に右ペインに表示されます。  
  
    2.  最初のパラメーターに「2」と入力し、2 番目のパラメーターに「3」と入力します。  
  
    3.  クリックして**Invoke**メソッドを呼び出します。  
  
11. 移動して、**イベント ビューアー**既に開いているウィンドウ。 移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー-アプリケーション**します。  
  
12. 右クリックし、**分析**ノード**更新**します。  
  
     右ペインにイベントが表示されます。  
  
13. ID が 303 のイベントを探してダブルクリックして開き、内容を確認します。  
  
     このイベントはによって作成された、 `Add()` ICalculator サービスのメソッドと等しく、ペイロードは"2 + 3 = 5"。  
  
#### <a name="to-clean-up-optional"></a>クリーンアップするには (省略可能)  
  
1. 開いている**イベント ビューアー**します。  
  
2. 移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**します。 右クリック**分析**選択**ログの無効化**します。  
  
3. 移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**、し**分析**します。 右クリック**分析**選択**ログの消去**します。  
  
4. クリックして**オフ**イベントを消去します。  
  
## <a name="known-issue"></a>既知の問題  
 既知の問題がある、**イベント ビューアー** ETW イベントのデコードに失敗する可能性があります。 というエラー メッセージを参照してください可能性があります。"イベント ID の説明\<id > 元が Microsoft Windows のアプリケーション サーバー-アプリケーションが見つかりません。 このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが破損しています。 インストールしたり、ローカル コンピューターのコンポーネントを修復できます。" このエラーが発生した場合は、選択**更新**から、**アクション**メニュー。 これにより、イベントが正常にデコードされます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
