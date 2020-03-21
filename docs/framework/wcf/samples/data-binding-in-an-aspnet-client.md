---
title: ASP.NET クライアントでのデータ バインディング
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145008"
---
# <a name="data-binding-in-an-aspnet-client"></a>ASP.NET クライアントでのデータ バインディング
このサンプルでは、Web フォーム アプリケーションで、一般的な Wcf (WCF) サービスによって返されるデータをバインドする方法を示します。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。 このサンプルは、ブラウザーからアクセスできるクライアント Web フォーム アプリケーションと、インターネット インフォメーション サービス (IIS) によってホストされる WCF サービスで構成されます。  
  
 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。 コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。 この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 ASP.NET クライアント .aspx ページでは、DataGrid Web コントロールが定義され、サービスによって返されるデータのグラフィカルな表現が含まれています。 .aspx ページ上のコードは、気象データの WCF サービスを呼び出し`WeatherData`、オブジェクトの配列にデータを返します。 DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。 データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。 このコードはすべて、 内に含まれています。`aspx` ページの`Page_Load`メソッドは、ユーザーがブラウザー ページを更新するたびに、DataGrid でデータが更新されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。 開発用 Web サーバーを起動するには、コマンド プロンプトで次`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`のように入力します。 次に、`http://localhost:8000/client`を参照します。 このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
