---
title: Windows フォーム クライアントのデータ バインディング
ms.date: 03/30/2017
ms.assetid: a2a30b37-d6e2-4552-820e-e60b2bbe8829
ms.openlocfilehash: d538e8a525f8d07e9ac9f57d4b10119907602d90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145047"
---
# <a name="data-binding-in-a-windows-forms-client"></a>Windows フォーム クライアントのデータ バインディング
このサンプルでは、Windows フォーム アプリケーションで、WCF (WCF) サービスによって返されるデータにバインドする方法を示します。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。  
  
 このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。 このサンプルは、クライアントの Windows フォーム アプリケーション (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされる WCF サービスで構成されます。  
  
 コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。 この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。  
  
 データ バインディングは、Windows フォーム アプリケーションのクライアントで発生します。 `DataGridView` は Windows フォーム デザイナで定義し、データをグラフィック表示します。 さらに、`BindingSource` という中継局も作成されます。 `BindingSource` のデータ ソースは、サービスによって返されるデータ配列に設定されます。 `BindingSource` の目的は、データとデータ ビュー間を間接化するレイヤを提供することです。 データとの対話 (移動、並べ替え、フィルタ処理、更新など) はすべて、`BindingSource` コンポーネントを呼び出すことによって実行します。 `DataGridView` へのデータ バインディングを行うには、`datasource` の `DataGridView` を `BindingSource` オブジェクトに設定します。 WCF サービスから返されるすべてのデータは、ユーザーにグラフィカルに表示されます。  ユーザーがボタンをクリックするたびに、返されたデータはデータ バインドされた `DataGridView` で自動的に更新されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WindowsForms`  
