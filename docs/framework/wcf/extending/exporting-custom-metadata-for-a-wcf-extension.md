---
title: WCF 拡張に対するカスタム メタデータのエクスポート
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 5134b57c59268b139239021bc2b4f6f4538ad27d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334511"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF 拡張に対するカスタム メタデータのエクスポート
Windows Communication Foundation (WCF) では、メタデータのエクスポートはサービス エンドポイントを記述して、クライアントを使用してサービスを使用する方法を理解する標準化表現に投影するそれらのプロセスです。 カスタム メタデータは、システム指定のメタデータ エクスポーターでエクスポートできない XML 要素で構成されます。 通常、これは、ユーザー定義動作のカスタム WSDL 要素とバインド要素、およびバインディングとコントラクトの機能と要件に関するポリシー アサーションを含みます。  
  
 ここでは、カスタム WSDL またはポリシー アサーションのエクスポートについて説明し、エクスポート プロセス自体には重点を置きません。 型をエクスポートおよびインポートのメタデータがカスタムであるか、システムによって作成されたかどうかに関係なくメタデータを使用する方法の詳細については、次を参照してください。[エクスポートおよびインポートするメタデータ](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)します。  
  
## <a name="overview"></a>概要  
 使用してメタデータが公開されるときに、 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType>が調べられるすべてのコントラクトと WCF は、システム指定の属性とバインドを使用してサポートできるバインドに対して XSD と WSDL のポリシー アサーションを含む--を生成します。 ただし、カスタム動作属性やバインド要素を適切にエクスポートするには、あらかじめサポートしておく必要があります。  
  
 ここでは、次の内容について説明します。  
  
1. WSDL を発行する前に WSDL の生成データを公開する <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。  
  
2. WSDL データに含まれるポリシー アサーションをエクスポートする前にポリシー データを公開する <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。  
  
 カスタム WSDL とポリシー アサーションをインポートする方法の詳細については、次を参照してください。 [WCF 拡張機能のカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)します。  
  
## <a name="exporting-custom-wsdl-elements"></a>カスタム WSDL 要素のエクスポート  
 操作の動作、コントラクトの動作、エンドポイントの動作、またはバインド要素 <xref:System.ServiceModel.Description.IWsdlExportExtension> (それぞれ <xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior>、<xref:System.ServiceModel.Description.IEndpointBehavior>、<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>) を実装し、エクスポートしようとしているサービスの説明に動作またはバインド要素を挿入します  (動作を挿入する方法の詳細については、次を参照してください。[構成と、ランタイムの動作を拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md))。 <xref:System.ServiceModel.Description.IWsdlExportExtension> はエンドポイントごとに呼び出され、コントラクトがエクスポートされていない場合は、各エンドポイントによって最初にコントラクトがエクスポートされます。 必要に応じて、次のいずれかのエクスポート プロセスに参加できます。  
  
-   <xref:System.ServiceModel.Description.WsdlContractConversionContext> を使用して、エクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドで変更する。  
  
-   <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> を使用して、エンドポイントに対してエクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドで変更する。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.IWsdlExportExtension> インスタンスに含まれるすべての <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 実装で呼び出されます。  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.IWsdlExportExtension> インスタンスを持つすべての <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 実装で呼び出されます。  
  
 詳細については、「[方法 :カスタム WSDL をエクスポート](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)サンプルとサンプル[カスタム WSDL パブリケーション](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)します。  
  
## <a name="exporting-custom-policy-assertions"></a>カスタム ポリシー アサーションのエクスポート  
 <xref:System.ServiceModel.Description.IPolicyExportExtension> に <xref:System.ServiceModel.Channels.BindingElement> を実装し、バインド要素をバインディングに追加して、バインディングのサポートとコントラクトの機能に関するカスタム ポリシー アサーションを WSDL に書き込みます。 バインディングに実装されたバインド要素をエクスポートすると、<xref:System.ServiceModel.Description.IPolicyExportExtension> が 1 回呼び出され、<xref:System.ServiceModel.Description.PolicyConversionContext> を <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> メソッドに渡します。 <xref:System.ServiceModel.Description.PolicyConversionContext> インスタンスに対してこのメソッドを使用すると、メッセージ、操作、またはエンドポイント サブジェクトで WSDL バインディングに結び付けられているポリシー アサーションを追加できます。  
  
 詳細については、「[方法 :カスタム ポリシー アサーションをエクスポート](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)します。  
  
## <a name="see-also"></a>関連項目

- [方法: カスタム WSDL をエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [方法: カスタム ポリシー アサーションをエクスポートする](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)
- [WCF 拡張に対するカスタム メタデータのインポート](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
