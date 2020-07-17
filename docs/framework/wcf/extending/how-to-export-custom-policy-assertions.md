---
title: '方法: カスタム ポリシー アサーションをエクスポートする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795668"
---
# <a name="how-to-export-custom-policy-assertions"></a>方法: カスタム ポリシー アサーションをエクスポートする
ポリシー アサーションはサービス エンドポイントの機能と要件を説明します。 サービス アプリケーションは、サービス メタデータに含まれるカスタム ポリシー アサーションを使用して、エンドポイントのバインディングまたはコントラクトのカスタマイズ情報をクライアント アプリケーションに伝達します。 Windows Communication Foundation (WCF) を使用すると、通信する機能や要件に応じて、エンドポイント、操作、またはメッセージのサブジェクトで WSDL バインディングに結び付けられているポリシー式のアサーションをエクスポートできます。  
  
 カスタム ポリシー アサーションは、<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> に実装して、サービス エンドポイントのバインディングにバインド要素を直接挿入するか、またはアプリケーション構成ファイルにバインド要素を登録することによってエクスポートされます。 ポリシーのエクスポートの実装では、<xref:System.Xml.XmlElement?displayProperty=nameWithType> メソッドに渡された <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> の適切な <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> に、<xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> インスタンスとしてカスタム ポリシー アサーションを追加する必要があります。  
  
 また、<xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> クラスの <xref:System.ServiceModel.Description.WsdlExporter> プロパティをチェックし、入れ子になったポリシー表現およびポリシー フレームワーク属性を、指定されたポリシー バージョンに基づいた正しい名前空間にエクスポートする必要もあります。  
  
 カスタムポリシーアサーションをインポートするに<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>は[、「」および「」を参照してください。カスタムポリシーアサーション](how-to-import-custom-policy-assertions.md)をインポートします。  
  
### <a name="to-export-custom-policy-assertions"></a>カスタム ポリシー アサーションをエクスポートするには  
  
1. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> に <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> インターフェイスを実装します。 バインディング レベルでのカスタム ポリシー アサーションの実装を次のコード例に示します。  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. プログラムまたはアプリケーション構成ファイルを使用して、エンドポイントのバインディングにバインド要素を挿入します。 次の手順を参照してください。  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>アプリケーション構成ファイルを使用してバインディングを挿入するには  
  
1. カスタム ポリシー アサーション バインド要素の <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> を実装します。  
  
2. Bindingelementextensions > 要素を使用して[ \<](../../configure-apps/file-schema/wcf/bindingelementextensions.md) 、構成ファイルにバインド要素拡張を追加します。  
  
3. <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> を使用してカスタム バインドを作成します。  
  
### <a name="to-insert-a-binding-element-programmatically"></a>プログラムでバインド要素を挿入するには  
  
1. 新しい <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> を作成して <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> に追加します。  
  
2. 手順 1. のカスタム バインドを 新しいエンドポイントに追加し、<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出してその新しいサービス エンドポイントを <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。  
  
3. <xref:System.ServiceModel.ServiceHost>を開きます。 カスタム バインディングの作成と、プログラムによるバインド要素の挿入を次のコード例に示します。  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [方法: カスタムポリシーアサーションをインポートする](how-to-import-custom-policy-assertions.md)
