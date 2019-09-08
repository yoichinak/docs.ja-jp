---
title: '方法: クライアントデータサービスクラスを手動で生成する (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 106f1cedb33c0c1b333df0b9f2b8c2a70d458a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790429"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>方法: クライアントデータサービスクラスを手動で生成する (WCF Data Services)
WCF Data Services を Visual Studio と統合すると、 **[サービス参照の追加]** ダイアログボックスを使用して visual studio プロジェクトのデータサービスへの参照を追加するときに、クライアントデータサービスクラスが自動的に生成されるようになります。 詳細については、「[方法 :データサービス参照](how-to-add-a-data-service-reference-wcf-data-services.md)を追加します。 コード生成ツールの `DataSvcUtil.exe` を使用して、同じクライアント データ サービス クラスを手動で生成することもできます。 このツールは WCF Data Services に含まれており、データサービス定義から .NET Framework クラスを生成します。 このツールを使用して、概念モデル (.csdl) ファイル、および Visual Studio プロジェクトの Entity Framework モデルを表す .edmx ファイルからデータ サービス クラスを生成することもできます。

 このトピックの例は、Northwind サンプル データ サービスに基づいてクライアント データ サービス クラスを作成します。 このサービスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。 このトピックのいくつかの例では、Northwind モデルの概念モデル ファイルが必要です。 詳細については、「[方法 :Edmgen.exe を使用して、モデルファイルとマッピングファイル](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)を生成します。 このトピックのいくつかの例では、Northwind モデルの .edmx ファイルが必要です。 詳細については、「 [.Edmx ファイルの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))」を参照してください。

### <a name="to-generate-c-classes-that-support-data-binding"></a>データ バインディングをサポートする C# クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>データ バインディングをサポートする Visual Basic クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>サービス URI に基づいて C# クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>サービス URI に基づいて Visual Basic クラスを生成するには

- コマンド プロンプトで、次のコマンド (改行なし) を実行します。

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。

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

- [データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)
- [方法: データサービス参照の追加](how-to-add-a-data-service-reference-wcf-data-services.md)
- [WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe) ](wcf-data-service-client-utility-datasvcutil-exe.md)
