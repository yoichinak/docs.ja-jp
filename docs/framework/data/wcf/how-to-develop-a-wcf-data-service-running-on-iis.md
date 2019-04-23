---
title: '方法: IIS 上で実行する WCF Data Service を開発する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 78e8c3cacd89f88cbfa062cb30e5b3474c2614ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517839"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>方法: IIS で実行されている WCF データ サービスを開発します。

このトピックでは、WCF Data Services を使用して、インターネット インフォメーション サービス (IIS) を実行している ASP.NET Web アプリケーションによってホストされる Northwind サンプル データベースに基づくデータ サービスを作成する方法を示します。 ASP.NET 開発サーバーで実行されている ASP.NET Web アプリケーションとして同じ Northwind データ サービスを作成する方法の例は、次を参照してください。、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。

> [!NOTE]
> Northwind データ サービスを作成するには、ローカル コンピューターに Northwind サンプル データベースをインストールしておく必要があります。 このサンプル データベースをダウンロードするには、ダウンロード ページ「 [SQL Server 用サンプル データベース](https://go.microsoft.com/fwlink/?linkid=24758)」を参照してください。

 このトピックでは、Entity Framework プロバイダーを使用してデータ サービスを作成する方法を示します。 その他のデータ サービス プロバイダーを利用することもできます。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)します。

 サービスを作成した後に、データ サービス リソースへのアクセスを明示的に提供する必要があります。 詳細については、「[方法 :データ サービスへのアクセスを有効にする](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)します。

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>IIS で実行されている ASP.NET web アプリケーションを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. **新しいプロジェクト**ダイアログ ボックスで、**インストール済み**> [**Visual C#** または**Visual Basic**] > **Web**カテゴリ。

3. 選択、 **ASP.NET Web アプリケーション**テンプレート。

1. 入力`NorthwindService`としてプロジェクトの名前。

5. **[OK]** をクリックします。

6. **プロジェクト**メニューの  **NorthwindService プロパティ**します。

7. 選択、 **Web** 、タブを選び**ローカル IIS Web サーバーを使用**します。

8. クリックして**仮想ディレクトリの作成**順にクリックします**OK**します。

9. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。

    -   32 ビット システム: 

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   64 ビット システム: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     これにより、コンピューターに Windows Communication Foundation (WCF) が登録されます。

10. 管理特権を持つコマンド プロンプトから、次のコマンドを実行します (オペレーティング システムによって異なります)。

    -   32 ビット システム: 

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   64 ビット システム: 

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     これにより、WCF がコンピューターにインストールされた後、IIS は正常に実行されます。 IIS の再起動が必要になる場合があります。

11. ASP.NET アプリケーションが IIS7 で実行されると、次の手順も実行する必要があります。

    1. IIS マネージャーを開き、下にある PhotoService アプリケーションに移動します**既定の Web サイト**します。

    2. **機能ビュー**、ダブルクリックして**認証**します。

    3. **認証**] ページで、[**匿名認証**します。

    4. **アクション**ウィンドウで、をクリックして**編集**を設定するセキュリティ プリンシパルを匿名ユーザー で、サイトに接続します。

    5. **匿名認証資格情報の編集**ダイアログ ボックスで、**アプリケーション プール id**します。

    > [!IMPORTANT]
    > ネットワーク サービス アカウントを使用する際、そのアカウントに関連するすべての内部ネットワーク アクセス権を匿名ユーザーに付与します。

12. SQL Server Management Studio、sqlcmd.exe ユーティリティ、または Visual Studio の Transact-SQL エディターを使用して、Northwind データベースがアタッチされた SQL Server のインスタンスに対して次の Transact-SQL コマンドを実行します。

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    これにより、IIS の実行に使用される Windows アカウントに対して、SQL Server インスタンスのログインが作成されます。 IIS は、これを使用して SQL Server インスタンスに接続できるようになります。

13. Northwind データベースをアタッチして、次の Transact-SQL コマンドを実行します。

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    これにより、新しいログインに権限が付与され、IIS は Northwind データベースに対してデータの読み取りおよび書き込みを行うことができるようになります。

## <a name="define-the-data-model"></a>データ モデルを定義する

1. **ソリューション エクスプ ローラー**ASP.NET プロジェクトの名前を右クリックし、クリックして**追加** > **新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、 **ADO.NET Entity Data Model**します。

3. データ モデルの名前を入力`Northwind.edmx`します。

4. Entity Data Model ウィザード、選択**データベースから生成**、順にクリックします**次**。

5. 次の手順のいずれかの手順を実行して、データ モデルをデータベースに接続し、**次**:

    -   データベース接続が既に構成されていない場合は、クリックして**新しい接続**し、新しい接続を作成します。 詳細については、「[方法 :SQL Server データベースへの接続を作成する](https://go.microsoft.com/fwlink/?LinkId=123631)します。 この SQL Server インスタンスには、Northwind サンプル データベースがアタッチされている必要があります。

         \- または -

    -   Northwind データベースに接続するようにデータベース接続が既に構成されている場合は、一覧からその接続を選択します。

6. ウィザードの最終ページで、データベース内のすべてのテーブルのチェック ボックスをオンにし、ビューおよびストアド プロシージャのチェック ボックスをオフにします。

7. クリックして**完了**ウィザードを閉じます。

## <a name="create-the-data-service"></a>データ サービスを作成する

1. **ソリューション エクスプ ローラー**、ASP.NET プロジェクトの名前を右クリックし、クリックして**追加** > **新しい項目の**します。

2. **新しい項目の追加**ダイアログ ボックスで、 **WCF Data Service**します。

   ![Visual Studio 2015 での WCF データ サービス項目テンプレート](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF Data Service**テンプレートは、Visual Studio 2015 ではなく Visual Studio 2017 で使用できます。

3. サービスの名前を入力`Northwind`します。

     Visual Studio で新しいサービスの XML マークアップおよびコード ファイルが作成されます。 既定では、コード エディターのウィンドウが開きます。 **ソリューション エクスプ ローラー**サービスが、名前、Northwind、および拡張機能。 は.svc.cs または.svc.vb になります。

4. データ サービスのコードで、データ サービスを定義するクラスの定義にあるコメント `/* TODO: put your data source class name here */` をデータ モデルのエンティティ コンテナーである型 (この場合は `NorthwindEntities`) で置き換えます。 クラス定義は次のようになります。

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>関連項目

- [サービスとしてのデータの公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
