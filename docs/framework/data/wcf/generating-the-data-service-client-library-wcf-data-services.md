---
title: データ サービス クライアント ライブラリの生成 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780291"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>データ サービス クライアント ライブラリの生成 (WCF Data Services)
を実装[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]するデータサービスは、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードによって公開されるデータモデルを記述したサービスメタデータドキュメントを返すことができます。 詳細については[、「OData:サービスメタデータ](https://go.microsoft.com/fwlink/?LinkId=186070)ドキュメント。 Visual Studio の **[サービス参照の追加]** ダイアログボックスを使用して、ベースの[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]サービスへの参照を追加できます。 このツールを使用して、クライアントプロジェクトの[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードによって返されるメタデータへの参照を追加すると、次のアクションが実行されます。  
  
- データ サービスからのサービス メタデータ ドキュメントが要求され、返されたメタデータが解釈されます。  
  
    > [!NOTE]
    > 返されたメタデータは、クライアント プロジェクトに .edmx ファイルとして保存されます。 .edmx ファイルは、Entity Framework で使用される .edmx ファイルと形式が異なるので、Entity Data Model デザイナーを使用して開くことができません。 このメタデータ ファイルは、XML エディターまたは任意のテキスト エディターを使用して表示できます。 詳細については、 [「 \[MC-\]EDMX:Data Services パッケージング形式](https://go.microsoft.com/fwlink/?LinkID=178833)の仕様の Entity Data Model  
  
- <xref:System.Data.Services.Client.DataServiceContext> から継承するエンティティ コンテナー クラスとしてサービスの表現が生成されます。 この生成されたエンティティ コンテナー クラスは、Entity Data Model ツールが生成するエンティティ コンテナーに似ています。 詳細は、[Object Services の概要 (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)) をご覧ください。  
  
- サービス メタデータ内で見つかったデータ モデル型のデータ クラスが生成されます。  
  
- `System.Data.Services.Client` アセンブリへの参照がプロジェクトに追加されます。  
  
 詳細については、「[方法 :データサービス参照](how-to-add-a-data-service-reference-wcf-data-services.md)を追加します。  
  
 クライアントデータサービスクラスは、コマンドプロンプトで[datasvcutil.exe](wcf-data-service-client-utility-datasvcutil-exe.md)ツールを使用して生成することもできます。 詳細については、「[方法 :クライアントデータサービスクラス](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)を手動で生成します。  
  
## <a name="client-data-type-mapping"></a>クライアント データ型のマッピング  
 Visual Studio の **[サービス参照の追加]** ダイアログボックスまたは`DataSvcUtil.exe`ツールを使用して、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードに基づくクライアントデータクラスを生成する場合、次のように、.NET Framework データ型がデータモデルのプリミティブ型にマップされます。  
  
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
  
 詳細については[、「OData:プリミティブデータ型](https://go.microsoft.com/fwlink/?LinkId=186072)。  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
- [クイック スタート](quickstart-wcf-data-services.md)
