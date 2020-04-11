---
title: クイック スタート (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121224"
---
# <a name="quickstart-wcf-data-services"></a>クイック スタート (WCF Data Services)

このクイック スタートを使用すると、「[はじめに](getting-started-with-wcf-data-services.md)」のトピックをサポートする一連のタスクを通じて、 WCF データ サービスとオープン データ プロトコル (OData) について理解するのに役立ちます。

## <a name="what-youll-learn"></a>学習内容

このクイック スタートの最初のタスクでは、データ サービスを作成して、Northwind サンプル データベースから OData フィードを公開する方法を示します。 後のトピックでは、Web ブラウザーを使用して OData フィードにアクセスし、クライアント ライブラリを使用して OData フィードを使用する Windows プレゼンテーション 基盤 (WPF) クライアント アプリケーションを作成します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了するには、次のコンポーネントをインストールします。

- Visual Studio

- SQL サーバーのインスタンス。 これには、Visual Studio 2015 の既定のインストールに含まれている SQL Server Express、または Visual Studio 2017 以降の**データストレージと処理**ワークロードの一部として含まれます。

- Northwind サンプル データベース。 データベースをインストールするには、ノースウィンドから Transact-SQL スクリプト[を実行し、Microsoft SQL Server のサンプル データベースを pubs](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)します。

## <a name="wcf-data-services-quickstart-tasks"></a>WCF データ サービスのクイック スタート タスク

 [データ サービスの作成](creating-the-data-service.md)

 ASP.NET アプリケーションの定義、データ モデルの定義、データ サービスの作成、およびリソースへのアクセスの有効化を行います。

 [Web ブラウザからサービスにアクセスする](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Visual Studio からサービスを開始し、公開されているフィードに対して Web ブラウザーから HTTP GET 要求を送信してサービスにアクセスします。

 [NET Framework クライアント アプリケーションを作成する](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 OData フィードを使用する WPF アプリを作成し、Windows コントロールにデータをバインドし、バインドされたコントロールのデータを変更して、変更をデータ サービスに返送します。

> [!NOTE]
> 完成したバージョンのクイック スタートのプロジェクト ファイルは[、GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))からダウンロードできます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クイック スタートを開始する](creating-the-data-service.md)

## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../adonet/ef/index.md)
