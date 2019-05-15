---
title: WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: bf812f45e4a4090becd8dfafe035d39d1d851860
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583643"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)

DataSvcUtil.exe は、コマンド ライン ツールを使用する WCF Data Services によって提供される、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードし、.NET Framework クライアント アプリケーションからデータ サービスにアクセスするために必要なクライアント データ サービス クラスを生成します。 このユーティリティでは、以下のメタデータ ソースを使用してデータ クラスを生成できます。

- データ サービスのルート URI。 ユーティリティは、データ サービスによって公開されるデータ モデルが記述されたサービス メタデータ ドキュメントを要求します。 詳細については、次を参照してください[OData:。サービス メタデータ ドキュメント](https://go.microsoft.com/fwlink/?LinkId=186070)します。

- 定義されている概念スキーマ定義言語 (CSDL) を使用して定義されているデータ モデル ファイル (.csdl)、 [ \[MC-CSDL\]:概念スキーマ定義ファイル形式](https://go.microsoft.com/fwlink/?LinkID=159072)仕様。

- Entity Framework に付属する Entity Data Model ツールを使用して作成された .edmx ファイル。 詳細については、次を参照してください、 [ \[MC-EDMX\]:。データ サービス パッケージング形式のエンティティ データ モデル](https://go.microsoft.com/fwlink/?LinkID=178833)仕様。

詳細については、「[方法 :クライアント データ サービス クラスを手動で生成](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)します。

DataSvcUtil.exe ツールは、.NET Framework ディレクトリにインストールされます。 多くの場合、これにある*C:\Windows\Microsoft.NET\Framework\v4.0*します。 64 ビット システムでは、これにある*C:\Windows\Microsoft.NET\Framework64\v4.0*します。 アクセスすることできますも DataSvcUtil.exe ツール開発者コマンド プロンプトから Visual Studio の。

## <a name="syntax"></a>構文

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>パラメーター

|オプション|説明|
|------------|-----------------|
|`/dataservicecollection`|オブジェクトをコントロールにバインドするために必要なコードも生成することを指定します。|
|`/help`<br /><br /> または<br /><br /> `/?`|このツールのコマンド構文とオプションを表示します。|
|`/in:` *\<file>*|.csdl ファイルまたは .edmx ファイル、またはファイルがあるディレクトリを指定します。|
|`/language:`[VB&#124;CSharp]|生成されるソース コード ファイルの言語を指定します。 既定の言語は C# です。|
|`/nologo`|著作権メッセージが表示されないようにします。|
|`/out:` *\<file>*|生成されたクライアント データ サービス クラスを含むソース コード ファイルの名前を指定します。|
|`/uri:` *\<string>*|OData フィードの URI。|
|`/version:`[1.0&#124;2.0]|OData の許容される最上位のバージョンを指定します。 バージョンはに基づいて決定されます、`DataServiceVersion`返されたデータ サービス メタデータの DataService 要素の属性。 詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)します。 指定した場合、`/dataservicecollection`パラメーターも指定`/version:2.0`データ バインディングを有効にします。|

## <a name="see-also"></a>関連項目

- [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [方法: データ サービス参照を追加します。](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
