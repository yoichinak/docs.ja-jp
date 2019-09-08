---
title: WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 97e9502176e0cc2f36d67ee3dc8e8d0739a009b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790196"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)

Datasvcutil.exe は、 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードを使用し、.NET Framework クライアントアプリケーションからデータサービスにアクセスするために必要なクライアントデータサービスクラスを生成する WCF Data Services によって提供されるコマンドラインツールです。 このユーティリティでは、以下のメタデータ ソースを使用してデータ クラスを生成できます。

- データ サービスのルート URI。 ユーティリティは、データ サービスによって公開されるデータ モデルが記述されたサービス メタデータ ドキュメントを要求します。 詳細については[、「OData:サービスメタデータ](https://go.microsoft.com/fwlink/?LinkId=186070)ドキュメント。

- データモデルファイル (.csdl) は、次のように、 [ \[MC-csdl\]で定義されているように、概念スキーマ定義言語 (csdl) を使用して定義されます。概念スキーマ定義ファイル形式](https://go.microsoft.com/fwlink/?LinkID=159072)の仕様。

- Entity Framework に付属する Entity Data Model ツールを使用して作成された .edmx ファイル。 詳細については、 [「 \[MC-\]EDMX:Data Services パッケージング形式](https://go.microsoft.com/fwlink/?LinkID=178833)の指定に Entity Data Model します。

詳細については、「[方法 :クライアントデータサービスクラス](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)を手動で生成します。

Datasvcutil.exe ツールは、.NET Framework ディレクトリにインストールされます。 多くの場合、これは*c:\windows\ microsoft.net \framework\v4.0*にあります。 64ビットシステムの場合は、 *C:\Windows\Microsoft.NET\Framework64\v4.0*にあります。 開発者コマンドプロンプトの Visual Studio では、Datasvcutil.exe ツールにアクセスすることもできます。

## <a name="syntax"></a>構文

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>パラメーター

|オプション|説明|
|------------|-----------------|
|`/dataservicecollection`|オブジェクトをコントロールにバインドするために必要なコードも生成することを指定します。|
|`/help`<br /><br /> または<br /><br /> `/?`|このツールのコマンド構文とオプションを表示します。|
|`/in:`*ファイル\<>*|.csdl ファイルまたは .edmx ファイル、またはファイルがあるディレクトリを指定します。|
|`/language:`[VB&#124;CSharp]|生成されるソース コード ファイルの言語を指定します。 既定の言語は C# です。|
|`/nologo`|著作権メッセージが表示されないようにします。|
|`/out:`*ファイル\<>*|生成されたクライアント データ サービス クラスを含むソース コード ファイルの名前を指定します。|
|`/uri:`*文字列\<>*|OData フィードの URI。|
|`/version:`[1.0&#124;2.0]|OData の許容される最大バージョンを指定します。 バージョンは、返されるデータサービス`DataServiceVersion`メタデータ内の DataService 要素の属性に基づいて決定されます。 詳細については、「[データサービスのバージョン管理](data-service-versioning-wcf-data-services.md)」を参照してください。 パラメーターを指定する`/dataservicecollection`場合は、も指定し`/version:2.0`てデータバインディングを有効にする必要があります。|

## <a name="see-also"></a>関連項目

- [データ サービス クライアント ライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)
- [方法: データサービス参照の追加](how-to-add-a-data-service-reference-wcf-data-services.md)
