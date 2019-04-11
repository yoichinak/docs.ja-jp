---
title: ASP.NET クライアントでのデータ バインディング
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 07e03a4580795b3424f63cec8f93fea2039b6733
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339412"
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET クライアントでのデータ バインディング
このサンプルでは、Web フォーム アプリケーションで一般的な Windows Communication Foundation (WCF) サービスによって返されるデータをバインドする方法を示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。 このサンプルは、クライアント ブラウザーとインターネット インフォメーション サービス (IIS) によってホストされる WCF サービスからアクセスできる Web フォーム アプリケーションで構成されます。  
  
 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。 コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。 この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] クライアントの .aspx ページには DataGrid Web コントロールが定義されています。このコントロールには、サービスによって返されるデータのグラフィック表示が含まれます。 .Aspx ページにコードは、気象データ用の WCF サービスを呼び出すし、データの配列を返す`WeatherData`オブジェクト。 DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。 データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。 このコードのすべてに含まれているのです。`aspx` ページの`Page_Load`DataGrid で毎回ユーザーがブラウザーのページ、データを更新するためのメソッドが更新されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。 開発 Web サーバーを起動するには、コマンド プロンプトで、次を入力:`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`します。 次に参照`http://localhost:8000/client`します。 このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
