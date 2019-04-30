---
title: '方法: メタデータの取得および準拠サービスの実装をする'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: edf8fe2f174202d19b075ec218f059ea9b988843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000793"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>方法: メタデータの取得および準拠サービスの実装をする
サービスのデザイン担当者と実装担当者が同じであるとは限りません。 アプリケーションの相互運用が重要な環境では、コントラクトを Web サービス記述言語 (WSDL) でデザインまたは記述した場合、開発者はそのコントラクトに準拠するサービスを実装する必要があります。 既存のサービスを移行するには、Windows Communication Foundation (WCF) には、ワイヤ形式を保持することもできます。 さらに、双方向コントラクトでは、呼び出し元でコールバック コントラクトを実装する必要もあります。  
  
 このようなケースにおいて、コントラクトの要件を満たしうる言語で サービス コントラクト インターフェイスを生成するためには、[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (または同等のツール) を使用する必要があります。 通常、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)および適切なバインディングを設定するクライアント構成ファイルとチャネル ファクトリまたは WCF クライアントの種類に使用されるサービス コントラクトを取得するために使用アドレス。 また、サービス コントラクトを変更する必要がある場合もあります。 また、サービス コントラクトを変更する必要もあります。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>データを取得して準拠サービスを実装するには  
  
1. メタデータ ファイルまたはコード ファイルを生成するメタデータ エンドポイントに対して [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。  
  
2. 出力コード ファイルを検索し、<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされた対象のインターフェイス (複数ある場合) 部分を見つけます。 次のコード例は、によって生成された 2 つのインターフェイスを示しています。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 最初の例 (`ISampleService`) は、準拠サービスを作成するために実装するサービス コントラクト インターフェイスです。 2 番目の例 (`ISampleServiceChannel`) は、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイスです。これはクライアント アプリケーションでも使用されます。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. すべての操作に対する応答アクションを WSDL で指定していない場合、生成後の操作コントラクトでは、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティがワイルドカード文字 (*) に設定される場合があります。 このプロパティの設定を削除します。 削除しない場合は、サービス コントラクト メタデータを実装するときに、それらの操作のメタデータをエクスポートできません。  
  
4. クラスにインターフェイスを実装してサービスをホストします。 例については、「[方法: サービス コントラクトを実装する](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)、または次の例のセクションでは単純な実装を参照してください。  
  
5. [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) が生成したクライアント構成ファイルで、[\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) 構成セクションを[\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) 構成セクションへ変更します。 (生成されたクライアント アプリケーション構成ファイルの例は、次の「例」セクションを参照してください)。  
  
6. [\<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) 構成セクションの中で、サービス実装の`name`属性を[\<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)構成セクションに作成します。  
  
7. サービスの `name` 属性をユーザーのサービス実装の構成名に設定します。  
  
8. 実装するサービス コントラクトを使用するエンドポイント構成要素をサービス構成セクションに追加します。  
  
## <a name="example"></a>例  
 次のコード例を実行して生成されたコード ファイルの大部分を示しています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)メタデータ ファイルに対して。  
  
 このコードには、次の項目が示されています。  
  
- コントラクトの要件に準拠するサービス コントラクト インターフェイス (実装する場合) (`ISampleService`)。  
  
- サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> の両方を拡張するクライアント用のヘルパー インターフェイス。これはクライアント アプリケーションでも使用されます(`ISampleServiceChannel`)。  
  
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> を拡張するヘルパー クラス。クライアント アプリケーションで使用されます。(`SampleServiceClient`)  
  
- サービスから生成された構成ファイル。  
  
- `ISampleService` サービスの簡単な実装。  
  
- クライアント側の構成ファイルからサービス側バージョンへの変換。  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
