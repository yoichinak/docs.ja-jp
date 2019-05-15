---
title: データ サービスのバージョン管理 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: fd3be8a60048b10bbd94ac5b3bfadaee954943ef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583586"
---
# <a name="data-service-versioning-wcf-data-services"></a>データ サービスのバージョン管理 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]クライアントは、Uri を使用してデータ モデルに基づくリソースとしてデータをアクセスできるように、データ サービスを作成することができます。 OData では、サービス操作の定義もサポートしています。 ビジネス ニーズの変化、情報テクノロジの要件、その他の問題への対処などのさまざまな理由により、サービスの初期導入後と、場合によっては有効期間中に数回、これらのデータ サービスを変更することが必要になる場合があります。 既存のデータ サービスに変更を加える場合は、新しいバージョンのデータ サービスを定義する必要性や、既存のクライアント アプリケーションへの影響を最小限に抑える最善の方法を検討する必要があります。 ここでは、新しいバージョンのデータ サービスをいつどのように作成するかに関するガイダンスを示します。 また、WCF Data Services がクライアントと、OData プロトコルの異なるバージョンをサポートするデータ サービスの間の交換を処理する方法についても説明します。

## <a name="versioning-a-wcf-data-service"></a>WCF Data Service のバージョン管理
 データ サービスが配置され、データが使用されている状況では、データ サービスに変更を加えることで、既存のクライアント アプリケーションとの間に互換性の問題が発生する可能性があります。 ただし、サービスの全体的なビジネス ニーズを受けて変更が求められることも多いため、クライアント アプリケーションへの影響を最小限に抑えながらデータ サービスの新しいバージョンをいつどのように作成するかを検討する必要があります。

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>新しいバージョンのデータ サービスが推奨されるデータ モデルの変更
 データ サービスの新しいバージョンを発行するかどうかを検討する際は、さまざまな種類の変更がクライアント アプリケーションに与える影響を理解することが重要です。 データ サービスの新しいバージョンを作成する必要があるデータ サービスへの変更は、次の 2 つのカテゴリに分類できます。

- サービス コントラクトに対する変更。これには、サービス操作の更新、エンティティ セット (フィード) のアクセシビリティへの変更、バージョンの変更、およびサービスの動作に対するその他の変更が含まれます。

- データ コントラクトに対する変更。これには、データ モデル、フィード形式、またはフィードのカスタマイズが含まれます。

 次の表に、データ サービスの新しいバージョンの発行を考慮する必要がある変更の種類を示します。

|変更の種類|新しいバージョンが必要|新しいバージョンは不要|
|--------------------|----------------------------|----------------------------|
|サービス操作|-新しいパラメーターを追加します。<br />戻り値の型の変更<br />-サービスの操作を削除します。|-既存のパラメーターを削除します。<br />-新しいサービス操作を追加します。|
|サービスの動作|-カウント要求を無効にします。<br />-投影のサポートを無効にします。<br />-必要なデータ サービスのバージョンを増やす|-カウント要求を有効にします。<br />-投影のサポートを有効にします。<br />-必要なデータ サービスのバージョンを小さきます。|
|エンティティ セットのアクセス許可|-エンティティ セットのアクセス許可を制限します。<br />-応答コードを変更する (新しい最初の桁の値) <sup>1</sup>|-エンティティ セットのアクセス許可を緩和します。<br />-応答コードを変更する (同じ最初の桁の値)|
|エンティティのプロパティ|-既存のプロパティまたはリレーションシップを削除します。<br />-Null 非許容のプロパティを追加します。<br />-既存のプロパティを変更します。|-Null 許容のプロパティを追加する<sup>2</sup>|
|エンティティ セット|-エンティティ セットを削除します。|派生型を追加します。<br />-基本型を変更します。<br />エンティティ セットを追加します。|
|フィードのカスタマイズ|-エンティティ プロパティのマッピングを変更します。||

 <sup>1</sup>よって固有のエラー コードを受信するクライアント アプリケーションがどの程度厳密に依存します。

 <sup>2</sup>を設定することができます、<xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A>プロパティを`true`クライアントがクライアントで定義されていないデータ サービスによって送信された新しいプロパティを無視します。 ただし、挿入の場合、クライアントによって POST 要求に含められていないプロパティは既定値に設定されます。 更新の場合、クライアントが識別できないプロパティ内の既存のデータは、既定値で上書きされます。 この場合は、更新を MERGE 要求として送信する必要があります (これは既定の動作です)。 詳細については、次を参照してください。[データ サービス コンテキストの管理](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)します。

### <a name="how-to-version-a-data-service"></a>データ サービスのバージョンの管理
 必要に応じて、サービス コントラクトまたはデータ モデルが更新されたサービスの新しいインスタンスを作成して、データ サービスの新しいバージョンを定義します。 次に、この新しいサービスを、以前のバージョンと区別する新しい URI エンドポイントを使用して公開します。 次に例を示します。

- 古いバージョン: `http://services.odata.org/Northwind/v1/Northwind.svc/`

- 新しいバージョン: `http://services.odata.org/Northwind/v2/Northwind.svc/`

 データ サービスをアップグレードした場合、新しいルート URI を使用するには、新しいデータ サービス メタデータに基づいてクライアントも更新する必要があります。 可能な場合は、新しいバージョンを使用するためのアップグレードが行われていないクライアントをサポートするために、データ サービスの以前のバージョンを保持してください。 データ サービスの古いバージョンは、必要でなくなった時点で削除できます。 データ サービスのエンドポイント URI を外部の構成ファイルに保持することを検討する必要があります。

## <a name="odata-protocol-versions"></a>OData プロトコルのバージョン
 OData の新しいバージョンがリリースされるは、クライアント アプリケーションが同じバージョンのデータ サービスによってサポートされている OData プロトコルを使用していない可能性があります。 以前のバージョンのクライアント アプリケーションは、OData の新しいバージョンをサポートするデータ サービスにアクセスできます。 クライアント アプリケーションは、新しいバージョンにアクセスしているデータ サービスよりも新しいバージョンの OData をサポートする WCF Data Services クライアント ライブラリの使用可能性があります。

 WCF Data Services では、このようなバージョン管理シナリオを処理する OData で提供されるサポートを利用します。 生成と、クライアントが OData のデータとは異なるバージョンを使用する場合、クライアント データ サービス クラスを作成するデータ モデルのメタデータの使用はサポートされてもサービスが使用されます。 詳細については、次を参照してください[OData:。プロトコルのバージョン管理](https://go.microsoft.com/fwlink/?LinkId=186071)します。

### <a name="version-negotiation"></a>バージョンのネゴシエーション
 クライアントによって要求されたバージョンに関係なく、サービスによって使用される OData プロトコルの最高バージョンを定義するデータ サービスを構成できます。 指定することでこれを行う、<xref:System.Data.Services.Common.DataServiceProtocolVersion>値、<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>のプロパティ、<xref:System.Data.Services.DataServiceBehavior>データ サービスで使用します。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。

 アプリケーションでは、データ サービスにアクセスする、WCF Data Services クライアント ライブラリを使用するときに、ライブラリはこれらのヘッダーを自動的に OData と、アプリケーションで使用されている機能のバージョンに応じて、適切な値に設定します。 既定では、WCF Data Services は、要求された操作をサポートする最も低いプロトコル バーションを使用します。

 次の表に、.NET Framework のバージョンと[!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]OData プロトコルの特定のバージョンの WCF Data Services のサポートが含まれる。

|OData プロトコルのバージョン|サポートが用意されているバージョン|
|-----------------------------------------------------------------------------------|----------------------------|
|バージョン 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] バージョン 3|
|バージョン 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-更新プログラムを[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]SP1。 ダウンロードしてから、更新プログラムをインストールすることができます、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?LinkId=158125)します。<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] バージョン 4|
|バージョン 3|-ダウンロードしてから OData バージョン 3 をサポートするプレリリース バージョンをインストール、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?LinkId=203885)します。|

### <a name="metadata-versions"></a>メタデータのバージョン
 既定では、WCF Data Services は、CSDL のバージョン 1.1 を使用して、データ モデルを表します。 リフレクション プロバイダーまたはカスタム データ サービス プロバイダーに基づくデータ モデルの場合は、常にこの CSDL バージョンが使用されます。 ただし、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を使用してデータ モデルを定義している場合は、返される CSDL のバージョンは [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] で使用されるバージョンと同じになります。 CSDL のバージョンの名前空間が続く、 [Schema 要素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)します。

 返されたメタデータの `DataServices` 要素には `DataServiceVersion` 属性も含まれます。この属性は、応答メッセージの `DataServiceVersion` ヘッダーの値と同じです。 クライアント アプリケーションなど、**サービス参照の追加** ダイアログ ボックス Visual Studio は、この情報を使用してデータ サービスをホストする WCF Data Services のバージョンと正しく連動するクライアント データ サービス クラスを生成します。 詳細については、次を参照してください[OData:。プロトコルのバージョン管理](https://go.microsoft.com/fwlink/?LinkId=186071)します。

## <a name="see-also"></a>関連項目

- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
