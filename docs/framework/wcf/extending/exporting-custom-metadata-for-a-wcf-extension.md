---
title: WCF 拡張に対するカスタム メタデータのエクスポート
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797185"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>WCF 拡張に対するカスタム メタデータのエクスポート
Windows Communication Foundation (WCF) では、メタデータのエクスポートは、サービスエンドポイントを記述し、それらを並列的に投影するプロセスであり、クライアントがサービスの使用方法を理解するために使用できます。 カスタム メタデータは、システム指定のメタデータ エクスポーターでエクスポートできない XML 要素で構成されます。 通常、これは、ユーザー定義動作のカスタム WSDL 要素とバインド要素、およびバインディングとコントラクトの機能と要件に関するポリシー アサーションを含みます。  
  
 ここでは、カスタム WSDL またはポリシー アサーションのエクスポートについて説明し、エクスポート プロセス自体には重点を置きません。 メタデータがカスタムまたはシステムで構成されているかどうかに関係なく、メタデータをエクスポートおよびインポートする型の使用方法の詳細については、「[メタデータのエクスポートとインポート](../feature-details/exporting-and-importing-metadata.md)」を参照してください。  
  
## <a name="overview"></a>概要  
 を使用して<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType>メタデータが公開されると、が調べられ、XSD と WSDL (ポリシーアサーションを含む) が検証され、WCF がシステム指定の属性とバインディングを使用してサポートできるすべてのコントラクトとバインドに対して生成されます。 ただし、カスタム動作属性やバインド要素を適切にエクスポートするには、あらかじめサポートしておく必要があります。  
  
 ここでは、次の内容について説明します。  
  
1. WSDL を発行する前に WSDL の生成データを公開する <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。  
  
2. WSDL データに含まれるポリシー アサーションをエクスポートする前にポリシー データを公開する <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。  
  
 カスタム WSDL およびポリシーアサーションのインポートの詳細については、「 [WCF 拡張機能のカスタムメタデータのインポート](importing-custom-metadata-for-a-wcf-extension.md)」を参照してください。  
  
## <a name="exporting-custom-wsdl-elements"></a>カスタム WSDL 要素のエクスポート  
 操作の動作、コントラクトの動作、エンドポイントの動作、またはバインド要素 <xref:System.ServiceModel.Description.IWsdlExportExtension> (それぞれ <xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior>、<xref:System.ServiceModel.Description.IEndpointBehavior>、<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>) を実装し、エクスポートしようとしているサービスの説明に動作またはバインド要素を挿入します (ビヘイビアーの挿入の詳細については、「[ビヘイビアーを使用したランタイムの構成と拡張](configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください)。 <xref:System.ServiceModel.Description.IWsdlExportExtension> はエンドポイントごとに呼び出され、コントラクトがエクスポートされていない場合は、各エンドポイントによって最初にコントラクトがエクスポートされます。 必要に応じて、次のいずれかのエクスポート プロセスに参加できます。  
  
- <xref:System.ServiceModel.Description.WsdlContractConversionContext> を使用して、エクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドで変更する。  
  
- <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> を使用して、エンドポイントに対してエクスポートされたメタデータを <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドで変更する。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.IWsdlExportExtension> インスタンスに含まれるすべての <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 実装で呼び出されます。  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドは、エクスポートされる <xref:System.ServiceModel.Description.IWsdlExportExtension> インスタンスを持つすべての <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 実装で呼び出されます。  
  
 詳細については、「[方法 :カスタム wsdl](how-to-export-custom-wsdl.md)およびサンプルの[カスタム wsdl パブリケーション](../samples/custom-wsdl-publication.md)をエクスポートします。  
  
## <a name="exporting-custom-policy-assertions"></a>カスタム ポリシー アサーションのエクスポート  
 <xref:System.ServiceModel.Description.IPolicyExportExtension> に <xref:System.ServiceModel.Channels.BindingElement> を実装し、バインド要素をバインディングに追加して、バインディングのサポートとコントラクトの機能に関するカスタム ポリシー アサーションを WSDL に書き込みます。 バインディングに実装されたバインド要素をエクスポートすると、<xref:System.ServiceModel.Description.IPolicyExportExtension> が 1 回呼び出され、<xref:System.ServiceModel.Description.PolicyConversionContext> を <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> メソッドに渡します。 <xref:System.ServiceModel.Description.PolicyConversionContext> インスタンスに対してこのメソッドを使用すると、メッセージ、操作、またはエンドポイント サブジェクトで WSDL バインディングに結び付けられているポリシー アサーションを追加できます。  
  
 詳細については、「[方法 :カスタムポリシーアサーション](how-to-export-custom-policy-assertions.md)をエクスポートします。  
  
## <a name="see-also"></a>関連項目

- [方法: カスタム WSDL のエクスポート](how-to-export-custom-wsdl.md)
- [方法: カスタムポリシーアサーションのエクスポート](how-to-export-custom-policy-assertions.md)
- [WCF 拡張に対するカスタム メタデータのインポート](importing-custom-metadata-for-a-wcf-extension.md)
