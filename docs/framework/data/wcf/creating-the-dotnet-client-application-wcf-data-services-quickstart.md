---
title: .NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 2f48f9486c5d29fc0b70e4487a12a1c499235cba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732649"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>.NET Framework クライアント アプリケーションの作成 (WCF Data Services クイック スタート)

これは、WCF Data Services クイック スタートの最後のタスクです。 このタスクでは、ソリューションにコンソール アプリケーションを追加への参照を追加、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]この新しいクライアント アプリケーションにフィードおよびフィードの生成されたクライアント データ サービス クラスおよびクライアント ライブラリを使用して、クライアント アプリケーションから OData へのアクセス.

> [!NOTE]
> データ フィードへのアクセスには .NET Framework ベースのクライアント アプリケーションは必要ありません。 データ サービスは、OData フィードを使用する任意のアプリケーション コンポーネントによってアクセスできます。 詳細については、[クライアント アプリケーションでデータ サービスを使用して](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)を参照してください。

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Visual Studio を使用してクライアント アプリケーションを作成するには

1.  **ソリューション エクスプ ローラー**は、ソリューションを右クリックし、[**追加**、] をクリックし、**新しいプロジェクト**します。

2.  左側のウィンドウで次のように選択します。**インストール済み**> [**Visual C#** または**Visual Basic**] > **Windows デスクトップ**、し、を選択します。**WPF アプリ**テンプレート。

3.  入力`NorthwindClient`プロジェクト名、およびクリックの**OK**。

4.  ファイル MainWindow.xaml を開き、XAML コードを次のコードに置き換えます。

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>データ サービス参照をプロジェクトに追加するには

1.  **ソリューション エクスプ ローラー**NorthwindClient プロジェクトを右クリックをクリックし、**追加** > **サービス参照の**、 をクリックし、**検出**.

     最初のタスクで作成した Northwind データ サービスが表示されます。

2.  **Namespace**テキスト ボックスに「 `Northwind`、 をクリックし、 **OK**。

     プロジェクトに新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。 データ クラスは、名前空間 `NorthwindClient.Northwind` で作成されます。

## <a name="to-access-data-service-data-in-the-wpf-application"></a>WPF アプリケーションのデータ サービスにアクセスするには

1.  **ソリューション エクスプ ローラー**  **NorthwindClient**プロジェクトを右クリックし、クリックして、**参照の追加**します。

2.  **参照の追加**ダイアログ ボックスで、をクリックして、 **.NET**  タブで、System.Data.Services.Client.dll アセンブリを選択し、順にクリックします**OK**。

3. **ソリューション エクスプ ローラー**  **NorthwindClient**、MainWindow.xaml ファイルのコード ページを開き、次の追加`using`ステートメント (`Imports` Visual Basic で)。

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3.  次のコードを挿入します。このコードは、データ サービスをクエリし、<xref:System.Data.Services.Client.DataServiceCollection%601> に対する結果を `MainWindow` クラスにバインドします。

    > [!NOTE]
    > ホスト名 `localhost:12345` を Northwind データ サービスのインスタンスをホストするサーバーとポートで置き換えます。

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4.  次のコードを挿入します。このコードは、変更内容を `MainWindow` クラスに保存します。

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>NorthwindClient アプリケーションをビルドして実行するには

1.  **ソリューション エクスプ ローラー**NorthwindClient プロジェクトを右クリックし、選択、**スタートアップ プロジェクトとして設定**します。

2.  キーを押して**F5**アプリケーションを起動します。

     ソリューションがビルドされ、クライアント アプリケーションが起動します。 データがサービスから要求され、コンソールに表示されます。

3.  値を編集、**数量**列のデータ グリッド、およびクリック**保存**します。

     変更内容はデータ サービスに保存されます。

    > [!NOTE]
    > このバージョンの NorthwindClient アプリケーションでは、エンティティの追加と削除はサポートされません。

## <a name="next-steps"></a>次の手順

サンプルの Northwind OData フィードにアクセスするクライアント アプリケーションが正常に作成しました。 WCF Data Services クイック スタートも完了しました。

OData へのアクセスの詳細についてはフィードから、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションを参照してください[WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)します。

## <a name="see-also"></a>関連項目

- [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [リソース](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
