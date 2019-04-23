---
title: '方法: MetadataExchangeClient を使用してメタデータを取得する'
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 32acef65ee30d7b80b37c11bdd024e3c09a935ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977672"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>方法: MetadataExchangeClient を使用してメタデータを取得する
WS-MetadataExchange (MEX) プロトコルを使用してメタデータをダウンロードするには、<xref:System.ServiceModel.Description.MetadataExchangeClient> クラスを使用します。 取得されたメタデータ ファイルは、<xref:System.ServiceModel.Description.MetadataSet> オブジェクトとして返されます。 返された <xref:System.ServiceModel.Description.MetadataSet> オブジェクトには、<xref:System.ServiceModel.Description.MetadataSection> オブジェクトのコレクションが含まれ、コレクションの各オブジェクトには、特定のメタデータの言語と識別子が含まれます。 返されたメタデータはファイルに書き込むことができます。また、返されたメタデータに Web サービス記述言語 (WSDL: Web Services Description Language) ドキュメントが含まれている場合は、<xref:System.ServiceModel.Description.WsdlImporter> を使用してメタデータをインポートできます。  
  
 アドレスを取得する <xref:System.ServiceModel.Description.MetadataExchangeClient> コンストラクターは、アドレスの URI (Uniform Resource Identifier) スキームに一致する <xref:System.ServiceModel.Description.MetadataExchangeBindings> 静的クラスでバインディングを使用します。 または、使用するバインディングを明示的に指定できるようにする <xref:System.ServiceModel.Description.MetadataExchangeClient> コンストラクターを使用することもできます。 指定したバインディングは、すべてのメタデータ参照を解決するために使用されます。  
  
 その他の Windows Communication Foundation (WCF) クライアントと同様、<xref:System.ServiceModel.Description.MetadataExchangeClient>型のエンドポイント構成名を使用してクライアント エンドポイント構成を読み込んでコンス トラクターを提供します。 指定したエンドポイント構成では、<xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを指定する必要があります。 エンドポイント構成のアドレスは読み込まれないため、アドレスを受け取る <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> オーバーロードのいずれかを使用する必要があります。 <xref:System.ServiceModel.EndpointAddress> インスタンスを使用してメタデータ アドレスを指定した場合、<xref:System.ServiceModel.Description.MetadataExchangeClient> は、指定したアドレスが MEX エンドポイントを指すものと想定します。 メタデータ アドレスを URL として指定した場合は、使用する <xref:System.ServiceModel.Description.MetadataExchangeClientMode> として、MEX または HTTP GET のいずれかを指定する必要もあります。  
  
> [!IMPORTANT]
>  既定では、<xref:System.ServiceModel.Description.MetadataExchangeClient> は、WSDL と XML スキーマのインポートおよびインクルードを含むすべての参照を解決します。 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> プロパティを `false` に設定すると、この機能を無効にできます。 解決する参照の最大数を制御するには、<xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> プロパティを使用します。 バインディングでこのプロパティと `MaxReceivedMessageSize` プロパティを組み合わせて使用すると、取得するメタデータのサイズを制御できます。  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>MetadataExchangeClient を使用してメタデータを取得するには  
  
1. 新しい <xref:System.ServiceModel.Description.MetadataExchangeClient> オブジェクトを作成するには、バインディング、エンドポイント構成名、またはメタデータのアドレスを明示的に指定します。  
  
2. 必要に応じて <xref:System.ServiceModel.Description.MetadataExchangeClient> を構成します。 たとえば、メタデータを要求するときに使用する証明書を指定したり、メタデータ参照の解決方法を制御したり、<xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> プロパティを設定してメタデータ要求がタイムアウトするまでの待機時間を制御したりできます。  
  
3. <xref:System.ServiceModel.Description.MetadataSet> メソッドのいずれかを呼び出して、取得されたメタデータを含む <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> オブジェクトを取得します。 <xref:System.ServiceModel.Description.MetadataExchangeClient> の構築時にアドレスを明示的に指定した場合は、引数を受け取らない <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> オーバーロードしか使用できません。  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.Description.MetadataExchangeClient> を使用してメタデータ ファイルをダウンロードし、列挙する方法を次のコード例に示します。  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例をコンパイルするには、System.ServiceModel.dll アセンブリを参照し、<xref:System.ServiceModel.Description> 名前空間をインポートする必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
