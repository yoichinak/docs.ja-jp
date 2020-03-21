---
title: フィード フォーマッタ (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183652"
---
# <a name="feed-formatter-json"></a>フィード フォーマッタ (JSON)
このサンプルでは、カスタムの <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> を使用することにより JSON (JavaScript Object Notation) 形式の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> クラスのインスタンスをシリアル化する方法を示します。  
  
## <a name="architecture-of-the-sample"></a>サンプルのアーキテクチャ  
 このサンプルは `JsonFeedFormatter` を継承する <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> という名前のクラスを実行します。 `JsonFeedFormatter` クラスは <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存し、JSON 形式でデータの読み取りと書き込みを行います。 内部的には、フォーマッタは `JsonSyndicationFeed` および `JsonSyndicationItem` という名前のデータ コントラクト型のカスタム セットを使用し、シリアライザによって生成される JSON データの形式を制御します。 これらの実装の詳細はエンド ユーザーには表示されず、標準的な <xref:System.ServiceModel.Syndication.SyndicationFeed> および <xref:System.ServiceModel.Syndication.SyndicationItem> クラスに対する呼び出しを行うことができます。  
  
## <a name="writing-json-feeds"></a>JSON フィードの書き込み  
 次のコード例に示すように、JSON フィードの書き込みは `JsonFeedFormatter` (このサンプルで実装) を <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と共に使用して実行できます。  
  
```csharp  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>JSON フィードの読み取り  
 次のコードに示すように、JSON 形式のデータのストリームからの <xref:System.ServiceModel.Syndication.SyndicationFeed> の取得は `JsonFeedFormatter` を使用して実行できます。  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
