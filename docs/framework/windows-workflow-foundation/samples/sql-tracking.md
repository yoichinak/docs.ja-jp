---
title: SQL 追跡
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: e2cb86a92e075d9117f2fe208f2044d4bc30dac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710018"
---
# <a name="sql-tracking"></a>SQL 追跡
このサンプルでは、カスタム SQL 追跡参加要素を作成し、追跡レコードを SQL データベースに書き込む方法を示します。 Windows Workflow Foundation (WF) は、ワークフロー インスタンスの実行時に可視性を示すワークフロー追跡を提供します。 追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。 ワークフロー追跡の詳細については、[ワークフロー追跡とトレース](../workflow-tracking-and-tracing.md)を参照してください。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1.  SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。 サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。 別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。

2.  Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。 これによって、TrackingSample という名前のデータベースが作成されます。

    > [!NOTE]
    >  このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。 別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。  
  
3.  Visual Studio 2010 で SqlTrackingSample.sln を開きます。  
  
4.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
5.  F5 キーを押してアプリケーションを実行します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
6.  ブラウザーで、StockPriceService.xamlx をクリックします。  
  
7.  ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。 このアドレスをコピーします。  
  
     ローカル サービスの WSDL アドレスの例は`http://localhost:65193/StockPriceService.xamlx?wsdl`します。  
  
8.  
  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアント (WcfTestClient.exe) を実行します。 このテスト クライアントは Microsoft Visual Studio 10.0\Common7\IDE ディレクトリにあります。  
  
9. WCF テスト クライアントでのクリックして、**ファイル**メニュー選択し、**サービスの追加**します。 テキスト ボックスにローカル サービスのアドレスを貼り付けます。 クリックして**OK**ダイアログ ボックスを閉じます。  
  
10. WCF テスト クライアントでダブルクリック **[getstockprice]** します。 開き、`GetStockPrice`操作を 1 つのパラメーター値の型を受け取る`Contoso` をクリック**Invoke**します。  
  
11. 出力された追跡レコードが SQL データベースに書き込まれます。 追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。 SQL Server Management Studio の詳細については、[SQL Server Management Studio の概要](https://go.microsoft.com/fwlink/?LinkId=165645)を参照してください。 SQL Server 2008 Management Studio Express をダウンロードできます[ここ](https://go.microsoft.com/fwlink/?LinkId=180520)します。 テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。  
  
#### <a name="to-uninstall-the-sample"></a>サンプルをアンインストールするには  
  
1.  サンプル ディレクトリ (\WF\Basic\Tracking\SqlTracking) で Trackingcleanup.cmd スクリプトを実行します。  
  
    > [!NOTE]
    >  Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。 別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>関連項目
- [AppFabric の監視のサンプル](https://go.microsoft.com/fwlink/?LinkId=193959)
