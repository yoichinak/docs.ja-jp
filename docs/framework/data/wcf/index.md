---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 6910bfbc94f69292bb8c2a52bf3ebef8fcfb3a8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500240"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

(旧称"ADO.NET Data Services")、WCF Data Services を使用するサービスを作成することができます、.NET Framework のコンポーネントである、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]公開およびのセマンティクスを使用して、Web またはイントラネット上のデータを使用する[(REST) representational state transfer](https://go.microsoft.com/fwlink/?LinkId=113919)します。 OData は、URI でアドレス指定できるリソースとしてデータを公開します。 標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。 OData エンティティとリレーションシップの規則を使用して、 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。

WCF Data Services は、アドレス指定およびリソースを更新するための OData プロトコルを使用します。 この方法では、これらのサービスを OData をサポートする任意のクライアントからアクセスできます。 OData では要求をリソースに知られている転送形式を使用してデータを書き込むことができます。Atom、交換および JavaScript Object Notation (JSON) と、XML としてデータを更新するための標準のセット AJAX アプリケーションで広く使用されて、テキスト ベースのデータ交換形式。

WCF Data Services は OData フィードとしてさまざまなソースから取得したデータを公開できます。 Visual Studio tools を容易に ADO.NET Entity Framework データ モデルを使用して、OData ベースのサービスを作成するためです。 共通言語ランタイム (CLR) クラスとも遅延バインディングまたは型指定されていないデータに基づいて OData フィードを作成することもできます。

WCF Data Services には、一般的な .NET Framework クライアント アプリケーションと Silverlight ベース アプリケーション用のクライアント ライブラリのセットも含まれています。 これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から OData フィードにアクセスするときに、オブジェクト ベースのプログラミング モデルを提供します。

## <a name="where-should-i-start"></a>開始すべき場所

ご自分の興味に応じて、次のトピックのいずれかで WCF Data Services の概要を検討してください。

すぐに使用を開始する…

- [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

- [Silverlight クイックスタート](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Windows Phone 開発用の Silverlight クイック スタート](https://go.microsoft.com/fwlink/?LinkID=214535)

だけ私にいくつかのコードを表示してください.

- [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

- [方法: データ サービス クエリを実行します。](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [方法: Windows Presentation Foundation 要素にデータをバインドします。](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

OData の詳細を理解する.

- [ホワイト ペーパー:OData の概要](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Open Data Protocol Web サイト](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData:SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData:よく寄せられる質問](https://go.microsoft.com/fwlink/?LinkId=185867)

いくつかのビデオを視聴する.

- [WCF Data Services のビギナーズ ガイド](https://go.microsoft.com/fwlink/?LinkId=220864)

- [WCF Data Services 開発者用ビデオ](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData:開発者 Web サイト](https://go.microsoft.com/fwlink/?LinkId=185866)

エンド ツー エンドのサンプルを表示する.

- [MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル](https://go.microsoft.com/fwlink/?LinkID=220865)

- [MSDN サンプル ギャラリーのその他の WCF Data Services サンプル](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData:SDK](https://go.microsoft.com/fwlink/?LinkID=185248)

Visual Studio との統合について知りたい

- [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

- [データ サービスの作成](../../../../docs/framework/data/wcf/creating-the-data-service.md)

- [Entity Framework プロバイダー](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

何に使用できるかを知りたい

- [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

- [ホワイト ペーパー:OData の概要](https://go.microsoft.com/fwlink/?LinkId=220867)

- [アプリケーション シナリオ](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

Silverlight を使用する.

- [Silverlight クイックスタート](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Silverlight について](https://go.microsoft.com/fwlink/?LinkId=148366)

LINQ を使用する.

- [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

- [LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [方法: データ サービス クエリを実行します。](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

詳細についてはいくつか必要があります.

- [WCF Data Services チームのブログ](https://go.microsoft.com/fwlink/?LinkID=150511)

- [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

- [WCF Data Services デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Open Data Protocol Web サイト](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>このセクションの内容

[概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

WCF Data Services で利用できる機能と機能の概要を示します。

[WCF Data Services 5.0 の新機能新機能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

WCF Data Services と OData の新機能のサポートで新しい機能をについて説明します。

[はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

公開および WCF Data Services を使用して OData フィードを使用する方法について説明します。

[WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

作成して、OData フィードを公開するデータ サービスを構成する方法について説明します。

[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

クライアント ライブラリを使用して、.NET Framework クライアント アプリケーションから OData フィードを使用する方法について説明します。

## <a name="see-also"></a>関連項目

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
