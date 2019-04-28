---
title: WCF サービスと Event Tracing for Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 35d0202a3b9cf4060240dc521554644d419a5c23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723174"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF サービスと Event Tracing for Windows
このサンプルでは、Event Tracing for Windows (ETW で) を出力する Windows Communication Foundation (WCF) での分析トレースを使用する方法を示します。 分析トレースは、運用環境で WCF サービスのトラブルシューティングできるように、WCF スタックのキー_ポイントで出力されるイベントです。

 WCF サービスの分析トレースのトレースが可能に運用環境でのパフォーマンスに影響を最小限にします。 これらのトレースは、ETW セッションにイベントとして出力されます。

 このサンプルでは、基本的な WCF サービスでイベントがサービスから生成された、イベント ビューアーを使用して表示できるイベント ログに含まれています。 WCF サービスからのイベントをリッスンする専用の ETW セッションを開始することもできます。 サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2012 を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。

2. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。

3. ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。

     Web ブラウザーで次のようにクリックします。 **[calculator.svc]** します。 サービスの WSDL ドキュメントの URI がブラウザーに表示されます。 その URI をコピーします。

     既定では、サービスの開始ポート 1378 で要求のリッスン`http://localhost:1378/Calculator.svc`します。

4. WCF テスト クライアント (WcfTestClient.exe) を実行します。

     WCF テスト クライアント (WcfTestClient.exe) は`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`します。  既定の Visual Studio 2012 のインストール ディレクトリは`C:\Program Files\Microsoft Visual Studio 10.0`します。

5. 選択して、サービスを追加、WCF テスト クライアント内で**ファイル**、し**サービスの追加**します。

     入力ボックスにエンドポイントのアドレスを追加します。 既定値は `http://localhost:1378/Calculator.svc` です。

6. イベント ビューアー アプリケーションを開きます。

     サービスを呼び出す前に、イベント ビューアーを起動し、WCF サービスから生成された追跡イベントのイベント ログがリッスンしていることを確認します。

7. **開始**メニューの **管理ツール**、し**イベント ビューアー**します。  有効にする、**分析**と**デバッグ**ログ。

8. イベント ビューアーのツリー ビューでに移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、。**アプリケーション サーバー-アプリケーション**します。 右クリックして**アプリケーション サーバー-アプリケーション**を選択します**ビュー**、し**分析およびデバッグ ログ**します。

     いることを確認、 **分析およびデバッグ ログ**オプションをオンにします。

9. 有効にする、**分析**ログ。

     イベント ビューアーのツリー ビューでに移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、。**アプリケーション サーバー-アプリケーション**します。 右クリック**分析**選択**ログの有効化**します。

#### <a name="to-test-the-service"></a>サービスをテストするには

1. WCF テスト クライアントに戻ると、ダブルクリックして`Divide`分母を 0、既定値を保持しているとします。

     分母が 0 の場合、サービスからエラーがスローされます。

2. サービスから出力されたイベントを確認します。

     イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**します。 右クリック**分析**選択**更新**します。

     WCF 分析トレースのイベントがイベント ビューアーに表示されます。 サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。

3. 手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。 `N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。

     分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。

 このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。

#### <a name="to-cleanup-optional"></a>クリーンアップするには (省略可能)

1. イベント ビューアーを開きます。

2. 移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**します。 右クリック**分析**選択**ログの無効化**します。

3. 移動します**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**します。 右クリック**分析**選択**ログの消去**します。

4. 選択、**オフ**イベントを消去するオプション。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
