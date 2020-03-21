---
title: パフォーマンス カウンターの使用
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143578"
---
# <a name="using-performance-counters"></a>パフォーマンス カウンターの使用
このサンプルでは、Windows 通信基盤 (WCF) のパフォーマンス カウンターにアクセスする方法と、ユーザー定義のパフォーマンス カウンターを作成する方法を示します。 このサンプルは、[作業の開始に](../../../../docs/framework/wcf/samples/getting-started-sample.md)基づいています。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。 この処理は、ユーザーが中断するまで継続して行われます。 サービスは変更されません。  
  
 パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 このタスクは、[構成エディター ツール (SvcConfigEditor.exe) を](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)使用して実行することもできます。  
  
 パフォーマンス カウンターが有効な場合、WCF パフォーマンス カウンターのスイート全体がサービスに対して有効になります。 .NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。 これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには、「 [Windows コミュニケーション ファウンデーション サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
### <a name="to-view-performance-data"></a>パフォーマンス データを表示するには  
  
1. [**スタート**] ボタン、[**ファイル名を指定して実行]** をクリックしてパフォーマンス モニタ ツールを起動し、次のように入力`perfmon`**して [OK] を**クリックするか、またはコントロール パネルの [**管理ツール**] を選択して、[**パフォーマンス**] をダブルクリックします。  
  
    > [!NOTE]
    > サンプル コードが実行されるまでは、カウンタを追加することはできません。  
  
2. 一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。  
  
3. グラフ ペインを右クリックし、[カウンターの追加] を選択して、WCF**カウンターを追加**します。 [**カウンターの追加]** ダイアログ ボックスで、[パフォーマンス オブジェクト] ドロップダウン リスト ボックスの [**サービスモデルオペレーション 3.0.0.0]、[サービスモデルエンドポイント 3.0.0.0]、または [ServiceModelService 3.0.0.0]** を選択します。 表示するカウンタを一覧から選択します。  
  
    > [!NOTE]
    > コンピューターで実行されている WCF サービスがない場合は、サービスの WCF パフォーマンス カウンターはありません。  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>構成エディターを使用してカウンターを有効にするには  
  
1. SvcConfigEditor.exe のインスタンスを開きます。  
  
2. [ファイル] メニューの [**開く**] をクリックし、[**構成ファイル.**  
  
3. サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。  
  
4. 構成ツリーで **[診断**]をクリックします。  
  
5. **[診断]** ウィンドウの**パフォーマンス カウンター**を [すべて] に切り替えます。  
  
6. 構成ファイルを保存し、エディターを終了します。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>関連項目

- [AppFabric の監視のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
