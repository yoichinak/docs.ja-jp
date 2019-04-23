---
title: データ サービスのホスティング (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: e738fa1feebdd91bdb84484340b31e599d7f5f76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517942"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>データ サービスのホスティング (WCF Data Services)
WCF Data Services を使用すると、データとして公開するサービスを作成することができます、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。 このデータ サービスは、<xref:System.Data.Services.DataService%601> から継承されたクラスとして定義されます。 このクラスは、要求メッセージの処理で、データ ソースに対して更新プログラムを実行し、OData に必要なの応答メッセージの生成に必要な機能を提供します。 ただし、データ サービスにバインドし、ネットワーク ソケットの受信 HTTP 要求をリッスンできません。 この機能要件のため、データ サービスはホスティング コンポーネントに依存します。

 データ サービス ホストは、データ サービスに代わって次のタスクを実行します。

-   要求をリッスンし、その要求をデータ サービスにルーティングする。

-   要求ごとにデータ サービスのインスタンスを作成する。

-   受信要求を処理するようデータ サービスに要求する。

-   データ サービスに代わって応答を送信する。

 データ サービスのホスティングを簡素化するには、WCF Data Services は、Windows Communication Foundation (WCF) を統合する設計されています。 データ サービスでデータ サービス ホストとして機能する既定の WCF 実装を提供する、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーション。 そのため、次のいずれかの方法でデータ サービスをホストできます。

-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション

-   自己ホスト型 WCF サービスをサポートするマネージ アプリケーション

-   その他のカスタム データ サービス ホスト

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>ASP.NET アプリケーションでのデータ サービスのホスト

使用すると、**新しい項目の追加**ダイアログ、ツール、ASP.NET アプリケーションでデータ サービスを定義する Visual Studio 2015 でプロジェクトの 2 つの新しいファイルが生成されます。 そのうち一方のファイル (拡張子は `.svc`) は、データ サービスのインスタンス化方法を WCF ランタイムに指示します。 完了したときに作成する Northwind サンプル データ サービスには、このファイルの例を次に、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 このディレクティブは、<xref:System.Data.Services.DataServiceHostFactory> クラスを使用して、名前付きのデータ サービス クラスのサービス ホストを作成するようアプリケーションに指示します。

 `.svc` ファイルの分離コード ページには、データ サービス自体の実装であるクラスが含まれます。Northwind サンプル データ サービスの場合、このクラスは次のように定義されます。

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 データ サービスは WCF サービスと同様に動作するため、データ サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と統合され、WCF Web プログラミング モデルに従います。 詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)と[WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)します。

## <a name="self-hosted-wcf-services"></a>自己ホスト型 WCF サービス
 WCF 実装が組み込まれて、ために、WCF Data Services は WCF サービスとしてデータ サービスを自己ホストをサポートします。 サービスは、コンソール アプリケーションなどの任意の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションで自己ホスト型とすることができます。 <xref:System.Data.Services.DataServiceHost> を継承する <xref:System.ServiceModel.Web.WebServiceHost> クラスを使用して、特定のアドレスでデータ サービスをインスタンス化します。

 自己ホストを使用するとサービスの配置とトラブルシューティングが容易になるので、開発時やテスト時に役立ちます。 ただし、この種類のホスティングでは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] またはインターネット インフォメーション サービス (IIS) に備わっている高度なホスト機能や管理機能を使用できません。 詳細については、次を参照してください。[マネージ アプリケーションでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)します。

## <a name="defining-a-custom-data-service-host"></a>カスタム データ サービス ホストの定義
 WCF ホストの実装の制限が厳格すぎる場合、データ サービスのカスタム ホストを定義することもできます。 <xref:System.Data.Services.IDataServiceHost> インターフェイスを実装する任意のクラスをデータ サービスのネットワーク ホストとして使用できます。 カスタム ホストは、<xref:System.Data.Services.IDataServiceHost> インターフェイスを実装し、データ サービス ホストの次の基本的な役割を果たすことができるようにする必要があります。

-   データ サービスにサービス ルート パスを提供する。

-   適切な <xref:System.Data.Services.IDataServiceHost> メンバーの実装に対する要求ヘッダーおよび応答ヘッダーの情報を処理する。

-   データ サービスで発生する例外を処理する。

-   クエリ文字列のパラメーターを検証する。

## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [サービスとしてのデータの公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
