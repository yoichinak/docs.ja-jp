---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779993"
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5

WCF Data Services (旧称 "ADO.NET Data Services" と呼ばれていた) は、を使用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]して Web またはイントラネット上のデータを公開および使用するサービスを作成できるようにする、.NET Framework のコンポーネントです。 [転送 (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)。 OData は、URI でアドレス指定できるリソースとしてデータを公開します。 標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。 OData は、 [Entity Data Model](../adonet/entity-data-model.md)のエンティティとリレーションシップの規則を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。

WCF Data Services は、OData プロトコルを使用してリソースのアドレス指定と更新を行います。 このようにして、OData をサポートする任意のクライアントからこれらのサービスにアクセスできます。 OData を使用すると、よく知られている転送形式を使用して、リソースにデータを要求して書き込むことができます。Atom は、データを XML として交換および更新するための標準のセットであり、AJAX アプリケーションで幅広く使用されるテキストベースのデータ交換形式である JavaScript Object Notation (JSON) です。

WCF Data Services は、さまざまなソースから送信されたデータを OData フィードとして公開できます。 Visual Studio tools を使用すると、ADO.NET Entity Framework データモデルを使用して、OData ベースのサービスを簡単に作成できます。 また、共通言語ランタイム (CLR) クラスに基づいて OData フィードを作成したり、遅延バインディングまたは型指定されていないデータを作成したりすることもできます。

WCF Data Services には、一般的な .NET Framework クライアントアプリケーション用と Silverlight ベースのアプリケーション用のクライアントライブラリのセットも含まれています。 これらのクライアントライブラリは、.NET Framework や Silverlight などの環境から OData フィードにアクセスするときに、オブジェクトベースのプログラミングモデルを提供します。

## <a name="where-should-i-start"></a>開始すべき場所

興味に応じて、次のトピックのいずれかで WCF Data Services の使用を開始することを検討してください。

すぐに使用を開始する…

- [クイック スタート](quickstart-wcf-data-services.md)

- [はじめに](getting-started-with-wcf-data-services.md)

- [Silverlight クイックスタート](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Windows Phone 開発用の Silverlight クイック スタート](https://go.microsoft.com/fwlink/?LinkID=214535)

コードを表示するだけです...

- [クイック スタート](quickstart-wcf-data-services.md)

- [方法: データサービスクエリの実行](how-to-execute-data-service-queries-wcf-data-services.md)

- [方法: Windows Presentation Foundation 要素にデータをバインドする](bind-data-to-wpf-elements-wcf-data-services.md)

OData の詳細を知りたい...

- [ホワイトOData の概要](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Open Data Protocol Web サイト](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData』](https://go.microsoft.com/fwlink/?LinkID=185248)

- [ODataよく寄せられる質問](https://go.microsoft.com/fwlink/?LinkId=185867)

ビデオを見ています...

- [WCF Data Services のビギナーズ ガイド](https://go.microsoft.com/fwlink/?LinkId=220864)

- [WCF Data Services 開発者用ビデオ](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData開発者向け Web サイト](https://go.microsoft.com/fwlink/?LinkId=185866)

エンドツーエンドのサンプルを確認するには...

- [MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル](https://go.microsoft.com/fwlink/?LinkID=220865)

- [MSDN サンプル ギャラリーのその他の WCF Data Services サンプル](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData』](https://go.microsoft.com/fwlink/?LinkID=185248)

Visual Studio との統合について知りたい

- [データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)

- [データ サービスの作成](creating-the-data-service.md)

- [Entity Framework プロバイダー](entity-framework-provider-wcf-data-services.md)

何に使用できるかを知りたい

- [概要](wcf-data-services-overview.md)

- [ホワイトOData の概要](https://go.microsoft.com/fwlink/?LinkId=220867)

- [アプリケーション シナリオ](application-scenarios-wcf-data-services.md)

Silverlight を使用するには...

- [Silverlight クイックスタート](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Silverlight について](https://go.microsoft.com/fwlink/?LinkId=148366)

LINQ...

- [データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)

- [LINQ に関する留意点](linq-considerations-wcf-data-services.md)

- [方法: データサービスクエリの実行](how-to-execute-data-service-queries-wcf-data-services.md)

まだいくつかの情報が必要です...

- [WCF Data Services チームのブログ](https://go.microsoft.com/fwlink/?LinkID=150511)

- [リソース](wcf-data-services-resources.md)

- [WCF Data Services デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Open Data Protocol Web サイト](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>このセクションの内容

[概要](wcf-data-services-overview.md)

WCF Data Services で使用できる機能の概要について説明します。

[WCF Data Services 5.0 の新機能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

WCF Data Services の新機能と、新しい OData 機能のサポートについて説明します。

[はじめに](getting-started-with-wcf-data-services.md)

WCF Data Services を使用して OData フィードを公開および使用する方法について説明します。

[WCF Data Services の定義](defining-wcf-data-services.md)

OData フィードを公開するデータサービスを作成および構成する方法について説明します。

[WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)

クライアントライブラリを使用して、.NET Framework クライアントアプリケーションから OData フィードを使用する方法について説明します。

## <a name="see-also"></a>関連項目

- [Representational State Transfer (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)
