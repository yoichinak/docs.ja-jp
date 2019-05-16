---
title: '方法: 手動で生成するクライアント データ サービス クラス (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: fdca85360e34d6854604103c9d0ac22c5b829cf5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634007"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>方法: 手動で生成するクライアント データ サービス クラス (WCF Data Services)
WCF Data Services を使用する場合、クライアント データ サービス クラスを自動的に生成するための Visual Studio と統合、**サービス参照の追加**ダイアログ ボックスを Visual Studio プロジェクトにデータ サービスへの参照を追加します。 詳細については、「[方法 :データ サービス参照を追加](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)します。 コード生成ツールの `DataSvcUtil.exe` を使用して、同じクライアント データ サービス クラスを手動で生成することもできます。 WCF Data Services に含まれるこのツールは、データ サービス定義から .NET Framework のクラスを生成します。 このツールを使用して、概念モデル (.csdl) ファイル、および Visual Studio プロジェクトの Entity Framework モデルを表す .edmx ファイルからデータ サービス クラスを生成することもできます。

 このトピックの例は、Northwind サンプル データ サービスに基づいてクライアント データ サービス クラスを作成します。 このサービスの作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。 このトピックのいくつかの例では、Northwind モデルの概念モデル ファイルが必要です。 詳細については、「[方法 :EdmGen.exe を使用して、モデルとマッピング ファイルを生成する](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)します。 このトピックのいくつかの例では、Northwind モデルの .edmx ファイルが必要です。 詳細については、次を参照してください。 [.edmx ファイルの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))します。

### <a name="to-generate-c-classes-that-support-data-binding"></a>データ バインディングをサポートする C# クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>データ バインディングをサポートする Visual Basic クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>サービス URI に基づいて C# クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>サービス URI に基づいて Visual Basic クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>概念モデル ファイル (CSDL) に基づいて C# を生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>概念モデル ファイル (CSDL) に基づいて Visual Basic を生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>.edmx ファイルに基づいて C# クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>.edmx ファイルに基づいて Visual Basic クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>関連項目

- [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [方法: データ サービス参照を追加します。](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe) ](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
