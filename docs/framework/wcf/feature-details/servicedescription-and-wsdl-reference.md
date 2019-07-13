---
title: ServiceDescription と WSDL 参照
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 6690bea3d3df0f39a5581c3a6c14723c0f30f40c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748164"
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription と WSDL 参照
このトピックとの間に、Windows Communication Foundation (WCF) が Web サービス記述言語 (WSDL) ドキュメントをマップする方法について説明します<xref:System.ServiceModel.Description.ServiceDescription>インスタンス。  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>ServiceDescription から WSDL 1.1 へのマッピング  
 WCF を使用して、WSDL ドキュメントからのエクスポート、<xref:System.ServiceModel.Description.ServiceDescription>サービスのインスタンス。 WSDL ドキュメントは、メタデータ エンドポイントを公開したときに自動的にサービスに対して生成されます。  
  
 また、<xref:System.ServiceModel.Description.ServiceEndpoint> 型を使用して、WSDL ドキュメントから <xref:System.ServiceModel.Description.ContractDescription> インスタンス、<xref:System.ServiceModel.Channels.Binding> インスタンス、および `WsdlImporter` インスタンスをインポートできます。  
  
 WCF では、によってエクスポートされた WSDL ドキュメントでは、外部の XML スキーマ ドキュメントから使用する XML スキーマ定義をインポートします。 データ型がサービスで使用するターゲット名前空間ごとに、個別の XML スキーマ ドキュメントがエクスポートされます。 同様に、サービス コントラクトが使用するターゲット名前空間ごとに、個別の WSDL ドキュメントがエクスポートされます。  
  
### <a name="servicedescription"></a>ServiceDescription  
 <xref:System.ServiceModel.Description.ServiceDescription> インスタンスは `wsdl:service` 要素にマップされます。 <xref:System.ServiceModel.Description.ServiceDescription> インスタンスは、それぞれが個別の `wsdl:port` 要素にマップされる <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスのコレクションを格納します。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@nameサービスの値。|  
|`Namespace`|サービスの `wsdl:service` 定義の targetNamespace|  
|`Endpoints`|サービスの `wsdl:port` 定義|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスは `wsdl:port` 要素にマップされます。 <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスは、アドレス、バインディング、およびコントラクトを格納します。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension> インターフェイスを実装するエンドポイント動作は、その動作が関連付けられているエンドポイントの `wsdl:port` 要素を変更できます。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name 、エンドポイントの値と`wsdl:binding`/@nameエンドポイント バインドの値。|  
|`Address`|エンドポイントの `wsdl:port` 定義のアドレス<br /><br /> アドレスの形式は、エンドポイントのトランスポートによって決まります。 たとえば、トランスポートの WCF でサポートされている可能性があります、SOAP アドレスまたはエンドポイント参照。|  
|`Binding`|エンドポイントの `wsdl:binding` 定義<br /><br /> 異なり`wsdl:binding`wcf バインドの定義がどのコントラクトに関連付けられていません。|  
|`Contract`|エンドポイントの `wsdl:portType` 定義|  
|`Behaviors`|<xref:System.ServiceModel.Description.IWsdlExportExtension> インターフェイスを実装するエンドポイント動作は、エンドポイントの `wsdl:port` を変更できます。|  
  
### <a name="bindings"></a>バインディング  
 `ServiceEndpoint` インスタンスのバインディング インスタンスは、`wsdl:binding` 定義にマップされます。 異なり`wsdl:binding`定義で、特定の関連付けられている必要があります`wsdl:portType`定義、WCF バインドは、コントラクトに依存しません。  
  
 バインディングは、バインド要素のコレクションで構成されます。 各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。 また、バインディングには、エンドポイントの <xref:System.ServiceModel.Channels.MessageVersion> と <xref:System.ServiceModel.EnvelopeVersion> を示すための <xref:System.ServiceModel.Channels.AddressingVersion> があります。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|エンドポイントの既定の名前で使用されます。この名前は、バインディング名にコントラクト名を追加し、アンダースコアで区切った形で表記されます。|  
|`Namespace`|`targetNamespace` 定義の `wsdl:binding`。<br /><br /> インポートでは、WSDL ポートに関連付けられたポリシーがある場合、インポートされたバインディング名前空間は、`targetNamespace` 定義の `wsdl:port` にマップされます。|  
|`BindingElementCollection` (`CreateBindingElements`() メソッドによって返されるプロパティとして)|`wsdl:binding` 定義に対するさまざまなドメイン固有の拡張。通常は、ポリシー アサーション。|  
|`MessageVersion`|エンドポイントの `EnvelopeVersion` および `AddressingVersion`。<br /><br /> `MessageVersion.None` が指定されている場合、WSDL バインディングは SOAP バインディングを格納せず、WSDL ポートは WS-Addressing コンテンツを含みません。 この設定は、通常、Plain Old XML (POX) エンドポイントに対して使用されます。|  
  
#### <a name="bindingelements"></a>BindingElements  
 エンドポイント バインディングのバインド要素は、ポリシー アサーションなど、`wsdl:binding` のさまざまな WSDL 拡張にマップされます。  
  
 SOAP バインディングのトランスポート URI (Uniform Resource Identifier) は、バインディングの <xref:System.ServiceModel.Channels.TransportBindingElement> によって決まります。  
  
#### <a name="addressingversion"></a>AddressingVersion  
 バインディングの `AddressingVersion` は、`wsd:port` で使用されるアドレス指定のバージョンにマップされます。 WCF がサポートする SOAP 1.1 と SOAP 1.2 のアドレスおよび Ws-addressing 08/2004 と Ws-addressing 1.0 のエンドポイント参照。  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 バインディングの `EnvelopeVersion` は、`wsdl:binding` で使用される SOAP のバージョンにマップされます。 WCF では、SOAP 1.1 と SOAP 1.2 のバインディングをサポートします。  
  
### <a name="contracts"></a>コントラクト  
 <xref:System.ServiceModel.Description.ContractDescription> インスタンスの `ServiceEndpoint` インスタンスは、`wsdl:portType` にマップされます。 `ContractDescription` インスタンスは、特定のコントラクトのすべての操作を記述します。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@nameコントラクトの値。|  
|`Namespace`|`wsdl:portType` 定義の targetNamespace|  
|`SessionMode`|`wsdl:portType` /@msc:usingSessionコントラクトの値。 この属性は、WSDL 1.1 用の WCF 拡張機能です。|  
|`Operations`|コントラクトの `wsdl:operation` 定義|  
  
### <a name="operations"></a>操作  
 <xref:System.ServiceModel.Description.OperationDescription>インスタンスにマップする`wsdl:portType` /`wsdl:operation`します。 `OperationDescription` は、操作のメッセージを記述する `MessageDescription` インスタンスのコレクションを格納します。  
  
 主に、2 つの操作動作 `OperationDescription` および `DataContractSerializerOperationBehavior` が、`XmlSerializerOperationBehavior` を WSDL ドキュメントにマップする方法に関与しています。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name操作の値。|  
|`ProtectionLevel`|この操作の `wsdl:binding/wsdl:operation` メッセージに関連付けられたセキュリティ ポリシーの保護アサーション|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating操作の値。 この属性は、WSDL 1.1 用の WCF 拡張機能です。|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating操作の値。 この属性は、WSDL 1.1 用の WCF 拡張機能です。|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input`と`wsdl:portType` / `wsdl:operation` / `wsdl:output`操作のメッセージ。|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault`操作の定義。|  
|`Behaviors`|`DataContractSerializerOperationBehavior` および `XmlSerializerOperationBehavior` は、操作バインディングおよび操作メッセージを扱います。|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 操作の `DataContractSerializerOperationBehavior` は、その操作の WSDL メッセージとバインディングをエクスポートする `IWsdlExportExtension` の実装です。 XML スキーマ型は、`XsdDataContractExporter` を使用してエクスポートされます。 また、`DataContractSerializerOperationBehavior` では、その操作に使用する使用方法、スタイル、およびスキーマ エクスポーターとインポーターを決定します。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style`この属性のプロパティにマップ、 `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style操作の値。<br /><br /> `DataContractSerializerOperationBehavior` は、WSDL のスキーマ型のリテラル使用だけをサポートします。|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 操作の `XmlSerializerOperationBehavior` は、その操作の WSDL メッセージとバインディングをエクスポートする `IWsdlExportExtension` の実装です。 XML スキーマ型は、`XmlSchemaExporter` を使用してエクスポートされます。 また、`XmlSerializerOperationBehavior` では、その操作に使用する使用方法、スタイル、およびスキーマ エクスポーターとインポーターを決定します。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style`この属性のプロパティにマップ、 `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style操作の値。<br /><br /> `Use`この属性のプロパティにマップ、 `wsdl:binding` / `wsdl:operation` / `soap:operation`/*/@use操作ですべてのメッセージの値。|  
  
### <a name="messages"></a>メッセージ  
 A`MessageDescription`インスタンスにマップする`wsdl:message`によって参照される、 `wsdl:portType` / `wsdl:operation` / `wsdl:input`または`wsdl:portType` / `wsdl:operation` / `wsdl:output`操作内のメッセージ。 `MessageDescription` には、本文とヘッダーがあります。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Action`|メッセージの SOAP アクションまたは WS-Addressing アクション。<br /><br /> Action 文字列 "*" を使用する操作は、WSDL では表示されません。|  
|`Direction`|`MessageDirection.Input` マップ`wsdl:input`します。<br /><br /> `MessageDirection.Output` マップ`wsdl:output`します。|  
|`ProtectionLevel`|このメッセージの `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション|  
|`Body`|メッセージのメッセージ本文|  
|`Headers`|メッセージのヘッダー|  
|`ContractDescription.Name`, `OperationContract.Name`|エクスポートでは、派生に使用される、 `wsdl:message` /@name値。|  
  
#### <a name="message-body"></a>メッセージ本文  
 A`MessageBodyDescription`インスタンスにマッピングされます、 `wsdl:message` / `wsdl:part`メッセージの本文を定義します。 メッセージ本文は、ラップされている場合とベアの場合があります。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`WrapperName`|スタイルが RPC ではない場合、次に、`WrapperName`によって参照される要素名にマップされます、 `wsdl:message` / `wsdl:part`で@name"parameters"に設定します。|  
|`WrapperNamespace`|スタイルが RPC ではない場合、次に、`WrapperNamespace`の要素の名前空間にマップされます、 `wsdl:message` / `wsdl:part`で@name"parameters"に設定します。|  
|`Parts`|このメッセージ本文のメッセージ部分|  
|`ReturnValue`|ラッパー要素が存在する場合 (ドキュメント ラップ スタイルまたは RPC スタイル)、それ以外の場合は、ラッパー要素の子要素で最初の`wsdl:message` / `wsdl:part`メッセージにします。|  
  
#### <a name="message-parts"></a>メッセージ部分  
 A`MessagePartDescription`インスタンスにマップする`wsdl:message` / `wsdl:part`と XML スキーマ型またはメッセージ部分が指す要素。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@nameメッセージ部分とメッセージ部分が指す要素の名前の値。|  
|`Namespace`|メッセージ部分が指す要素の名前空間|  
|`Index`|インデックス、 `wsdl:message` / `wsdl:part`メッセージ。|  
|`ProtectionLevel`|このメッセージ部分の `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション。 ポリシーは、特定のメッセージ部分を指すためにパラメーター化されます。|  
|`MessageType`|メッセージ部分が指す要素の XML スキーマ型|  
  
#### <a name="message-headers"></a>メッセージ ヘッダー  
 `MessageHeaderDescription` インスタンスは、メッセージ部分の `soap:header` バインディングにもマップされるメッセージ部分です。  
  
### <a name="faults"></a>エラー  
 A`FaultDescription`インスタンスにマッピングされます、 `wsdl:portType` / `wsdl:operation` / `wsdl:fault`定義およびその関連`wsdl:message`定義します。 `wsdl:message` は、関連する WSDL ポートの種類と同じターゲット名前空間に追加されます。 `wsdl:message` には、`DefaultType` インスタンスの `FaultDescription` プロパティ値に相当する XML スキーマ要素を指す、"detail" という名前の 1 つのメッセージ部分があります。  
  
|プロパティ|WSDL マッピング|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@nameエラーの値。|  
|`Namespace`|エラー詳細メッセージ部分が指す XML スキーマ要素の名前空間|  
|`Action`|エラーの SOAP アクションまたは WS-Addressing アクション|  
|`ProtectionLevel`|このエラーの `wsdl:message` 定義に関連付けられたセキュリティ ポリシーの保護アサーション|  
|`DetailType`|詳細メッセージ部分が指す要素の XML スキーマ型|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|派生に使用される、 `wsdl:message` /@nameエラー メッセージの値。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description>
