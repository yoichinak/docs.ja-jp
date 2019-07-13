---
title: サンプル ビジネス シナリオとユース ケースのサーバーレス アプリ
description: イメージ処理からモバイル バックエンドとの ETL パイプラインに範囲のサンプルにアクセスして実践的なアプローチとサーバーレスについて説明します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: adc4e1f3249cd72c423430ad4cb5dbb8eea8baf9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638823"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>サーバーレスのビジネス シナリオとユース ケース

多くのユース ケースとサーバーレス アプリケーションのシナリオがあります。 この章には、さまざまなシナリオを示すサンプルが含まれます。 このシナリオでは関連するドキュメントとパブリックなソース コード リポジトリへのリンクを使用します。 この章のサンプルには、構築して、サーバーレス ソリューションを実装する、自分で開始することが有効にします。

## <a name="analyze-and-archive-images"></a>分析し、イメージのアーカイブ

このサンプルでは、サーバーレスのイベント (Event Grid)、ワークフロー (ロジック アプリ)、およびコード (Azure Functions) を示します。 このケースの Cognitive Services のイメージの分析のための別のリソースと統合する方法も示します。

コンソール アプリケーションを使用すると、web 上のリンクを URL に渡すことができます。 アプリは、イベント グリッド メッセージとして URL を発行します。 並列でサーバーレスの関数アプリとロジック アプリは、メッセージをサブスクライブします。 サーバーレスの関数アプリには、blob ストレージにイメージがシリアル化します。 Azure Table storage の情報も格納します。 メタデータには、元の画像の URL と blob のイメージの名前が格納されます。 ロジック アプリは、画像を分析し、マシン生成のキャプションを作成するカスタム Vision API と対話します。 キャプションは、メタデータ テーブルに格納されます。

![分析し、イメージのアーキテクチャのアーカイブ](./media/image-processing-example.png)

別の単一ページ アプリケーション (SPA) は、イメージおよびメタデータの一覧を取得するサーバーレス関数を呼び出します。 イメージごとに、アーカイブから画像データを提供する別の関数を呼び出します。 字幕を自動でギャラリーを最後になります。

![自動化されたイメージ ギャラリー](./media/automated-image-gallery.png)

完全なリポジトリとロジック アプリをビルドする手順については。[イベント グリッド グルー](https://github.com/JeremyLikness/Event-Grid-Glue)します。

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Xamarin.Forms と関数を使用してクロス プラットフォーム モバイル クライアント

Azure の Web ポータルで、または Visual Studio では、単純なサーバーレス Azure 関数を実装する方法を参照してください。 Android、iOS、および Windows で実行されている Xamarin.Forms を使用するクライアントをビルドします。 アプリケーションは、サーバーとサーバーレス バックエンドをモバイル クライアント間の通信中として JavaScript Object Notation (JSON) を使用する、絞り込みます。

詳細については、次を参照してください[Xamarin.Forms クライアントの単純な Azure 関数を実装する。](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>サーバーレス画像認識と写真モザイクを生成します。

サンプルでは、Azure Functions と Microsoft Cognitive Services Custom Vision Service を使用して、入力の画像からフォト mosaic を生成します。 イメージを認識するモデルがトレーニングされます。 イメージがアップロードされると、そのイメージを認識して、Bing で検索します。 検索結果を使用して、元のイメージが再合成します。

![オーランド目の写真と mosaic](./media/orlando-eye-both.png)

たとえば、オーランド ランドマーク、オーランド目などを使用してモデルをトレーニングできます。 Custom Vision オーランド目のイメージが認識され、関数はフォト mosaic Bing の画像検索結果で構成の作成「オーランド目です」

詳細については、次を参照してください。 [Azure Functions フォト mosaic ジェネレーター](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)します。

## <a name="migrate-an-existing-application-to-the-cloud"></a>既存のアプリケーションをクラウドに移行します。

前の章で既に説明した、オンプレミス アプリケーションをホストする N 層アーキテクチャを採用する一般的です。 「現状有姿のリソースの移行クラウドへのリスクの小さいパスは、仮想マシンを使用して、自分のアプリケーションをリファクタリングする機会を使用する多くの企業を選択します。 さいわい、リファクタリングを「オール_オア_ナッシング」残存作業がありません。 実際には、アプリを移行し、段階的な部分に対応するクラウド ネイティブ コンポーネントを交換することができます。

アプリケーションでは、Azure Functions のプロキシ機能を使用して、リファクタリングでオンプレミスでレガシ コードからサーバーレスのエンドポイントにエンドポイントを有効にします。

![移行のアーキテクチャ](./media/migration-architecture.png)

プロキシは、サーバーレスの関数に移動すると、個々 の要求を再ルーティングするように更新する 1 つの API エンドポイントを提供します。

全体の移行について説明するビデオを表示することができます。[リフト アンド シフト サーバーレス Azure functions による](https://channel9.msdn.com/Events/Connect/2017/E102)します。 サンプル コードにアクセスします。[アプリケーションの持ち込み](https://github.com/JeremyLikness/bring-own-app-connect-17)します。

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>CSV ファイルを解析し、データベースに挿入

抽出、変換、および読み込み (ETL) は、さまざまなシステムを統合する共通のビジネス関数。 従来のアプローチは、多くの場合、専用の FTP サーバーをセットアップし、ファイルを解析し、業務用に変換するスケジュールされたジョブを展開する必要があります。 サーバーレス アーキテクチャ簡単ジョブ ファイルがアップロードされたときにトリガーを起動できるためです。 Azure Functions あたってタスクなどの特定の問題に焦点を少量のコードの最適な構成で ETL。

![Csv 解析プロセスを示すスクリーン ショット。](./media/serverless-business-scenarios/csv-parse-database-import.png)

ソース コードとハンズオン ラボでは、次を参照してください。 [CSV インポート ラボ](https://github.com/JeremyLikness/azure-fn-file-process-hol)します。

## <a name="shorten-links-and-track-metrics"></a>リンクを短縮し、メトリックの追跡

Twitter の 140 文字の制限に対応する投稿をリンク短くするツールの最初の Url を簡単に言えばエンコードを支援します。 いくつかの用途を最もよく分析のためには、クリックスルーの追跡を可能にし、拡大しました。 リンクの shortener シナリオは、リンクを管理し、メトリックを報告するすべてサーバーレス アプリケーションです。

Azure Functions を使用して、シングル ページ アプリケーション (SPA) を使用すると、長い URL を貼り付けて、短縮 Url を生成するサービスを提供します。 Url は、キャンペーン (トピック) とメディアへのリンクが掲載されているソーシャル ネットワーク) などのようなものを追跡するためにタグ付けされます。 含まれるショート コードは、値として、長い URL を使用して、キーとして Azure Table Storage に格納されます。 短いリンクをクリックすると別の関数は長い URL を検索、リダイレクトを送信し、イベントに関する情報をキューに配置します。 別の Azure 関数は、キューを処理し、Azure Cosmos DB に情報を格納します。

![リンク shortener アーキテクチャ](./media/link-shortener-architecture.png)

収集されたデータに関する洞察を収集するために Power BI ダッシュ ボードを作成できます。 バックエンドでは、Application Insights は、重要なメトリックを提供します。 製品利用統計情報には、平均的なユーザーをリダイレクトするのにかかると、Azure Table Storage へのアクセスにかかる時間が含まれています。

![Power BI の使用例](./media/power-bi-example.png)

指示をフル リンク shortener リポジトリは、ここで使用できます。[サーバーレス URL 短縮ツール](https://github.com/jeremylikness/serverless-url-shortener)します。 ここでは、簡略化されたバージョンについてを参照することができます。[.NET アプリを数分でサーバーレスの azure Storage](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)します。

## <a name="verify-device-connectivity-using-a-ping"></a>Ping を使用してデバイスの接続を確認します。

Azure IoT Hub と Azure 関数のサンプルを構成します。 IoT Hub での新しいメッセージは、Azure 関数をトリガーします。 サーバーレス コードでは、元のメッセージ送信元デバイスにコンテンツと同じメッセージを送信します。 プロジェクトは、ソリューションに必要なすべてのコードと展開構成にします。

詳細については、次を参照してください。 [Azure IoT Hub の ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)します。

## <a name="recommended-resources"></a>推奨リソース

* [Azure Functions の写真 mosaic ジェネレーター](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT Hub の ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [.NET アプリを数分でサーバーレスの azure Storage](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [アプリケーションを持ち込み](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV インポート ラボ](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [イベント グリッド グルー](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Xamarin.Forms クライアントの単純な Azure 関数を実装します。](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [リフト アンド シフトとサーバーレス Azure 関数](https://channel9.msdn.com/Events/Connect/2017/E102)
* [サーバーレス URL 短縮ツール](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[前へ](orchestration-patterns.md)
>[次へ](serverless-conclusion.md)
