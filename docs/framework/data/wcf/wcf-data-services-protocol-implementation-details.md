---
title: WCF Data Services プロトコル実装の詳細
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: fdaaa95bdcffa3ae053cc856753faa1a224eebc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728753"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>WCF Data Services プロトコル実装の詳細
## <a name="odata-protocol-implementation-details"></a>OData プロトコル実装の詳細  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] では、プロトコルを実装するデータ サービスが、特定の機能の最小セットを提供する必要があります。 これらの機能は、"should"と「必要があります」の観点からプロトコルのドキュメントに記述されます。 "May"の観点から説明は省略可能なその他の機能 このトピックでは、現在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で実装されていないオプション機能について説明します。 詳細については、[OData プロトコル ドキュメント](https://go.microsoft.com/fwlink/?LinkID=184554)を参照してください。  
  
### <a name="support-for-the-format-query-option"></a>$format クエリ オプションのサポート  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルは、JavaScript Notation (JSON) と Atom フィードの両方をサポートしており、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の `$format` システム クエリ オプションを使用すると、クライアントは応答フィードの形式を要求できます。 このシステム クエリ オプションは、データ サービスでサポートされている場合、要求の Accept ヘッダーの値をオーバーライドする必要があります。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、JSON と Atom フィードのどちらでも返すことができます。 ただし、既定の実装では `$format` クエリ オプションをサポートしておらず、Accept ヘッダーの値だけを使用して応答の形式を決定します。 クライアントが Accept ヘッダーを設定できない場合のように、データ サービスで `$format` クエリ オプションをサポートしなければならないこともあります。 このようなシナリオをサポートするには、このオプションを URI で処理するように、データ サービスを拡張する必要があります。 ダウンロードして、データ サービスにこの機能を追加することができます、 [ADO.NET データ サービスの JSONP および URL 制御の形式をサポート](https://go.microsoft.com/fwlink/?LinkId=208228)サンプル プロジェクトから、MSDN コード ギャラリー web サイトと、データ サービス プロジェクトに追加します。 このサンプルは、`$format` クエリ オプションを削除し、Accept ヘッダーを `application/json` に変更します。 サンプル プロジェクトを含めるときに、`JSONPSupportBehaviorAttribute` をデータ サービス クラスに追加すると、サービスが `$format` クエリ オプションの `$format=json` を処理できるようになります。 `$format=atom` や他のカスタム形式も処理するには、このサンプル プロジェクトをさらにカスタマイズする必要があります。  
  
## <a name="wcf-data-services-behaviors"></a>WCF Data Services の動作  
 次の [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の動作は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルでは明示的に定義されていません。  
  
### <a name="default-sorting-behavior"></a>既定の並べ替え動作  
 データ サービスに送信されるクエリ要求に、`$top` または `$skip` システム クエリ オプションが含まれ、`$orderby` システム クエリ オプションが含まれていない場合、返されるフィードはキー プロパティで昇順に並べ替えられます。 これは、結果を正しくページングするには並べ替えが必要であるためです。 そのために、データ サービスがクエリに並べ替え式を追加します。 この動作は、データ サービスでサーバー ドリブン ページングが有効になっている場合にも発生します。 詳細については、[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)を参照してください。返されるフィードの順序を制御するには、含める必要がある`$orderby`でクエリの URI。  
  
## <a name="see-also"></a>関連項目
- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
