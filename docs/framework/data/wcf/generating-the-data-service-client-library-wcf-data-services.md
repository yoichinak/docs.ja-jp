---
title: データ サービス クライアント ライブラリの生成 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 96b7bfabef589464e99e808d19f0dee6cfb23536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225821"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>データ サービス クライアント ライブラリの生成 (WCF Data Services)
実装するデータ サービス、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]によって公開されているデータ モデルを説明するサービス メタデータ ドキュメントを返すことができます、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。 詳細については、次を参照してください[OData:。サービス メタデータ ドキュメント](https://go.microsoft.com/fwlink/?LinkId=186070)します。 使用することができます、**サービス参照の追加**への参照を追加する Visual Studio でのダイアログ、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのサービスです。 によって返されるメタデータへの参照を追加するこのツールを使用する場合、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]クライアント プロジェクトでのフィードを次の操作を実行します。  
  
-   データ サービスからのサービス メタデータ ドキュメントが要求され、返されたメタデータが解釈されます。  
  
    > [!NOTE]
    >  返されたメタデータは、クライアント プロジェクトに .edmx ファイルとして保存されます。 .edmx ファイルは、Entity Framework で使用される .edmx ファイルと形式が異なるので、Entity Data Model デザイナーを使用して開くことができません。 このメタデータ ファイルは、XML エディターまたは任意のテキスト エディターを使用して表示できます。 詳細については、次を参照してください、 [ \[MC-EDMX\]:。データ サービス パッケージング形式のエンティティ データ モデル](https://go.microsoft.com/fwlink/?LinkID=178833)仕様  
  
-   <xref:System.Data.Services.Client.DataServiceContext> から継承するエンティティ コンテナー クラスとしてサービスの表現が生成されます。 この生成されたエンティティ コンテナー クラスは、Entity Data Model ツールが生成するエンティティ コンテナーに似ています。 詳細は、[Object Services の概要 (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)) をご覧ください。  
  
-   サービス メタデータ内で見つかったデータ モデル型のデータ クラスが生成されます。  
  
-   `System.Data.Services.Client` アセンブリへの参照がプロジェクトに追加されます。  
  
 詳細については、「[方法 :データ サービス参照を追加](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)します。  
  
 使用して、クライアント データ サービス クラスを生成することことも、 [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)コマンド プロンプト ツールです。 詳細については、「[方法 :クライアント データ サービス クラスを手動で生成](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)します。  
  
## <a name="client-data-type-mapping"></a>クライアント データ型のマッピング  
 使用すると、**サービス参照の追加**Visual Studio でダイアログまたは`DataSvcUtil.exe`に基づくクライアント データ クラスを生成するためのツール、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework のデータ型は、フィードからプリミティブ型にマップされます、データは、次のようにモデルします。  
  
|データ モデル型|.NET Framework データ型|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 詳細については、次を参照してください[OData:。プリミティブ データ型](https://go.microsoft.com/fwlink/?LinkId=186072)します。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
