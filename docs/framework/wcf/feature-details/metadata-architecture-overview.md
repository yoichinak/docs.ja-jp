---
title: メタデータ アーキテクチャの概要
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], overview
ms.assetid: 1d37645e-086d-4d68-a358-f3c5b6e8205e
ms.openlocfilehash: f9c903dd520f1aa85fc0577264288ecbc8c62a7f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111476"
---
# <a name="metadata-architecture-overview"></a>メタデータ アーキテクチャの概要
Windows Communication Foundation (WCF) は、エクスポート、公開、取得、およびサービスのメタデータをインポートするためのさまざまなインフラストラクチャを提供します。 WCF サービスでは、メタデータを使用して、Svcutil.exe などのツールが、サービスにアクセスするためのクライアント コードを自動的に生成されるように、サービスのエンドポイントと対話する方法について説明します。  
  
 WCF メタデータ インフラストラクチャを構成する型のほとんどが <xref:System.ServiceModel.Description> 名前空間に存在しています。  
  
 WCF は <xref:System.ServiceModel.Description.ServiceEndpoint> クラスを使用して、サービスのエンドポイントを記述します。 WCF を使用して、サービス エンドポイントのメタデータを生成、あるいは <xref:System.ServiceModel.Description.ServiceEndpoint>インスタンスを生成するためにサービス メタデータをインポートすることができます。  
  
 WCF では、サービスのメタデータを表すのインスタンスとして、<xref:System.ServiceModel.Description.MetadataSet>型、構造が厳密に Ws-metadataexchange で定義されているメタデータのシリアル化形式に関連付けられています。 <xref:System.ServiceModel.Description.MetadataSet> 型は、Web サービス記述言語 (WSDL: Web Services Description Language) ドキュメント、XML スキーマ ドキュメント、WS-Policy 表現などの実際のサービス メタデータを <xref:System.ServiceModel.Description.MetadataSection> インスタンスのコレクションとしてバンドルします。 各 <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> インスタンスには、特定のメタデータ言語と識別子が含まれます。 <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> はその <xref:System.ServiceModel.Description.MetadataSection.Metadata%2A?displayProperty=nameWithType> プロパティに、次のアイテムを含むことができます。  
  
- 生のメタデータ。  
  
- <xref:System.ServiceModel.Description.MetadataReference> のインスタンス。  
  
- <xref:System.ServiceModel.Description.MetadataLocation> のインスタンス。  
  
 <xref:System.ServiceModel.Description.MetadataReference?displayProperty=nameWithType> インスタンスは別のメタデータ交換 (MEX) エンドポイントをポイントし、<xref:System.ServiceModel.Description.MetadataLocation?displayProperty=nameWithType> インスタンスは HTTP URL を使用してメタデータ ドキュメントをポイントします。 WCF サービス エンドポイント、サービス コントラクト、バインディング、メッセージ交換パターン、メッセージおよびサービスによって実装されるエラー メッセージを記述する WSDL ドキュメントの使用をサポートします。 サービスで使用されるデータ型は、XML スキーマを使用して WSDL ドキュメントに記述されます。 詳細については、次を参照してください。[スキーマのインポートとエクスポート](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)します。 WCF は、サービス動作、コントラクト動作、およびサービスの機能を拡張するバインド要素の WSDL 拡張エクスポートおよびインポートに使用できます。 詳細については、次を参照してください。 [WCF 拡張機能のカスタム メタデータのエクスポート](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)します。  
  
## <a name="exporting-service-metadata"></a>サービス メタデータのエクスポート  
 WCF では、*メタデータのエクスポート*はサービス エンドポイントを記述して、クライアントを使用してサービスを使用する方法を理解する標準化表現に移し替えたりするプロセスです。 メタデータを <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスからエクスポートするには、<xref:System.ServiceModel.Description.MetadataExporter> 抽象クラスの実装を使用します。 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> の実装によって、<xref:System.ServiceModel.Description.MetadataSet> インスタンスにカプセル化されたメタデータが生成されます。  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> クラスには、エンドポイント バインディングの機能と要件、エンドポイントに関連付けられた処理、メッセージ、エラーを記述するポリシー式を生成するためのフレームワークが用意されています。 これらのポリシー式は、<xref:System.ServiceModel.Description.PolicyConversionContext> インスタンスにキャプチャされます。 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> を実装すると、生成したメタデータにこれらのポリシー式を結び付けることができます。  
  
 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> は、<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> オブジェクトを <xref:System.ServiceModel.Description.IPolicyExportExtension> の実装で使用するために生成するときに、<xref:System.ServiceModel.Description.ServiceEndpoint> のバインディングで <xref:System.ServiceModel.Description.PolicyConversionContext> インターフェイスを実装する各 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> を呼び出します。 <xref:System.ServiceModel.Description.IPolicyExportExtension> 型のカスタム実装の <xref:System.ServiceModel.Channels.BindingElement> インターフェイスを実装することで、新規のポリシー アサーションをエクスポートできます。  
  
 <xref:System.ServiceModel.Description.WsdlExporter>型の実装は、 <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> WCF に含まれているクラスを抽象化します。 <xref:System.ServiceModel.Description.WsdlExporter> 型は、結び付けられたポリシー式を使用して WSDL メタデータを生成します。  
  
 サービス エンドポイントでのエンドポイント動作、コントラクト動作、またはバインディング要素のカスタム WSDL メタデータまたは WSDL 拡張をエクスポートするには、<xref:System.ServiceModel.Description.IWsdlExportExtension> インターフェイスを実装する必要があります。 <xref:System.ServiceModel.Description.WsdlExporter> は WSDL ドキュメントの生成時に、<xref:System.ServiceModel.Description.ServiceEndpoint> インターフェイスを実装するバインディング要素、処理動作、コントラクト動作、およびエンドポイント動作の <xref:System.ServiceModel.Description.IWsdlExportExtension> インスタンスを参照します。  
  
## <a name="publishing-service-metadata"></a>サービス メタデータの公開  
 WCF サービスは、1 つまたは複数のメタデータ エンドポイントを公開することで、メタデータを公開します。 サービス メタデータを公開すると、サービス メタデータで MEX や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。 メタデータ エンドポイントは、アドレス、バインディング、およびコントラクトを持つという点で、他のサービス エンドポイントと似ています。 メタデータ エンドポイントは、構成またはコードを使用してサービス ホストに追加できます。  
  
 WCF サービスのメタデータ エンドポイントを公開するのインスタンスを最初に追加する必要があります、<xref:System.ServiceModel.Description.ServiceMetadataBehavior>サービス、サービスに動作します。 サービスに <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> インスタンスを追加することによって、1 つ以上のメタデータ エンドポイントを公開することでメタデータを公開する機能がサービスに追加されます。 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> サービス動作を追加すると、MEX プロトコルをサポートするメタデータ エンドポイント、または HTTP/GET 要求に応答するメタデータ エンドポイントを公開できます。  
  
 MEX プロトコルを使用するメタデータ エンドポイントを追加するには、名前付き IMetadataExchange.WCF を定義するサービス コントラクトを使用するサービス ホストにサービス エンドポイントを追加、<xref:System.ServiceModel.Description.IMetadataExchange>このサービス コントラクト名を持つインターフェイスです。 Ws-metadataexchange のエンドポイント、または、MEX エンドポイントはで静的ファクトリ メソッドによって公開されている 4 つの既定のバインディングのいずれかで使用できます、<xref:System.ServiceModel.Description.MetadataExchangeBindings>クラス Svcutil.exe などの WCF ツールで使用される既定のバインディングを照合します。 また、カスタム バインドを使用して MEX メタデータ エンドポイントを構成することもできます。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> は <xref:System.ServiceModel.Description.WsdlExporter?displayProperty=nameWithType> を使用して、サービス内のすべてのサービス エンドポイント用のメタデータをエクスポートします。 サービスからメタデータをエクスポートする方法の詳細については、次を参照してください。[エクスポートおよびインポートするメタデータ](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)します。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> は、<xref:System.ServiceModel.Description.ServiceMetadataExtension> インスタンスを拡張としてサービス ホストに追加することで、サービス ホストを拡張します。 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> により、メタデータ公開プロトコルを実装することができます。 また、<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> を使用して、<xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A> プロパティにアクセスすることにより、実行時にサービスのメタデータを取得できます。  
  
> [!CAUTION]
> MEX エンドポイントをアプリケーション構成ファイルに追加した後で、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> をコード内のサービス ホストに追加しようとすると、次の例外が発生します。  
>
> System.InvalidOperationException:コントラクト名 'IMetadataExchange' は、サービス Service1 によって実装されるコントラクトの一覧で見つかりませんでした。 ServiceMetadataBehavior を構成ファイルまたは ServiceHost ディレクトリに直接追加してこのコントラクトのサポートを有効にしてください。  
>
> <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を構成ファイルに追加するか、またはエンドポイントと <xref:System.ServiceModel.Description.ServiceMetadataBehavior> の両方をコードに追加することにより、この問題を回避できます。  
>
> 追加の例については<xref:System.ServiceModel.Description.ServiceMetadataBehavior>、アプリケーション構成ファイルで、次を参照してください。、 [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)します。 追加の例については<xref:System.ServiceModel.Description.ServiceMetadataBehavior>コードでは、次を参照してください。、[セルフホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプル。  

> [!CAUTION]
> それぞれに同じ名前の操作が含まれている 2 つ異なるサービス コントラクトを公開するサービスのメタデータを公開すると、例外がスローされます。 たとえば、Get(Car c) 操作を含む ICarService という名前のサービス コントラクトを公開するサービスがあり、その同じサービスが Get(Book b) 操作を含む IBookService という名前のサービス コントラクトを公開する場合、サービスのメタデータを生成するときに、例外がスローされるか、エラー メッセージが表示されます。 この問題を回避するには、次のいずれかの操作を実行します。  
>
> - 操作の名前を変更する。
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。  
> - <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。  
  
## <a name="retrieving-service-metadata"></a>サービス メタデータの取得  
 WCF では、Ws-metadataexchange、HTTP などの標準化プロトコルを使用してサービス メタデータを取得できます。 これらのプロトコルはいずれも、<xref:System.ServiceModel.Description.MetadataExchangeClient> 型でサポートされます。 アドレスとオプションのバインディングを提供することによって、<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 型を使用して、サービス メタデータを取得します。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> インスタンスで使用するバインディングは、<xref:System.ServiceModel.Description.MetadataExchangeBindings> 静的クラスの既定のバインディング、ユーザー指定のバインディング、`IMetadataExchange` コントラクト用のエンドポイント構成から読み込まれたバインディングのいずれかです。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> は同様に、<xref:System.Net.HttpWebRequest> 型を使用して、メタデータへの HTTP URL 参照を解決できます。  
  
 既定では、<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> インスタンスは、1 つの <xref:System.ServiceModel.Channels.ChannelFactoryBase> インスタンスに結び付けられています。 <xref:System.ServiceModel.Channels.ChannelFactoryBase> によって使用される <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> インスタンスは、<xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> 仮想メソッドをオーバーライドすることによって変更または置換することができます。 同様に、<xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 仮想メソッドをオーバーライドすることによって、HTTP/GET 要求を行うために <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> が使用する <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> インスタンスを変更または置換できます。  
  
 Svcutil.exe ツールを使用し、渡すことによって、Ws-metadataexchange または HTTP/GET 要求を使用してサービス メタデータを取得することができます、 **/target:metadata**スイッチとアドレス。 Svcutil.exe は指定したアドレスでメタデータをダウンロードし、ディスクにファイルを保存します。 Svcutil.exe は、<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> インスタンスを内部的に使用し、Svcutil.exe に渡されたアドレスのスキームに一致する名前を持つ MEX エンドポイント構成が存在する場合は、これをアプリケーション構成ファイルから読み込みます。 存在しない場合、Svcutil.exe は、<xref:System.ServiceModel.Description.MetadataExchangeBindings> 静的ファクトリ型によって定義されたバインディングの 1 つを既定で使用します。  
  
## <a name="importing-service-metadata"></a>サービス メタデータのインポート  
 WCF では、メタデータのインポートは、そのメタデータからサービスまたはコンポーネントの抽象表現を生成するプロセスです。 たとえば、WCF をインポートできます<xref:System.ServiceModel.Description.ServiceEndpoint>インスタンス、<xref:System.ServiceModel.Channels.Binding>インスタンスまたは<xref:System.ServiceModel.Description.ContractDescription>サービスの WSDL からインスタンスを文書化します。 Wcf サービス メタデータをインポートするには、実装を使用、<xref:System.ServiceModel.Description.MetadataImporter>抽象クラス。 派生する型、<xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>クラスは、Ws-policy を利用したメタデータ形式をインポートする WCF のロジックをインポートするためのサポートを実装します。  
  
 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> の実装は、<xref:System.ServiceModel.Description.PolicyConversionContext> オブジェクトでサービス メタデータに結び付けられたポリシー表現を収集します。 その後、<xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> は、<xref:System.ServiceModel.Description.IPolicyImportExtension> プロパティ内の <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> インターフェイスの実装を呼び出すことによって、メタデータのインポートの一部として、ポリシーを処理します。  
  
 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> インスタンスの <xref:System.ServiceModel.Description.IPolicyImportExtension> コレクションに <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> インターフェイスの独自の実装を追加することによって、新しいポリシー アサーションをインポートするためのサポートを <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> に追加できます。 または、クライアント アプリケーション構成ファイルにポリシー インポート拡張を登録できます。  
  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>型の実装は、 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType> WCF に含まれているクラスを抽象化します。 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> 型は、<xref:System.ServiceModel.Description.MetadataSet> オブジェクトにまとめられた、結び付けられているポリシーを使用して WSDL メタデータをインポートします。  
  
 <xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスを実装し、この実装を <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> インスタンスの <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> プロパティに追加することで、WSDL 拡張のインポートのサポートを追加できます。 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> は、クライアント アプリケーション構成ファイルに登録された <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> インターフェイスの実装を読み込むこともできます。  
  
## <a name="dynamic-bindings"></a>動的なバインド  
 エンドポイントのバインドが変化するイベントでサービス エンドポイントへのチャネルを作成する、または、同じコントラクトを使用しているがバインドが異なるエンドポイントへのチャネルを作成するために使用するバインドを動的に更新することができます。 <xref:System.ServiceModel.Description.MetadataResolver> 静的クラスを使用して、特定のコントラクトを実装しているサービス エンドポイントのメタデータを、実行時に取得またはインポートできます。 その後、インポートした <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> オブジェクトを使用して、必要なエンドポイントに対するクライアントまたはチャネル ファクトリを作成できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description>
- [メタデータ形式](../../../../docs/framework/wcf/feature-details/metadata-formats.md)
- [メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
- [メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [メタデータを取得する](../../../../docs/framework/wcf/feature-details/retrieving-metadata.md)
- [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [メタデータを使用する場合のセキュリティ上の考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
