---
title: WCF 拡張に対するカスタム メタデータのインポート
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: 830829be98202c97a9fc2b34e31da25967292efb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339971"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF 拡張に対するカスタム メタデータのインポート
Windows Communication Foundation (WCF) では、メタデータのインポートは、メタデータからサービスまたはコンポーネントの抽象表現を生成するプロセスです。 たとえば、WCF をインポートできます<xref:System.ServiceModel.Description.ServiceEndpoint>インスタンス、<xref:System.ServiceModel.Channels.Binding>インスタンスまたは<xref:System.ServiceModel.Description.ContractDescription>サービスの WSDL からインスタンスを文書化します。 Wcf サービス メタデータをインポートするには、実装を使用、<xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>抽象クラス。 派生する型、<xref:System.ServiceModel.Description.MetadataImporter>クラスは、Ws-policy を利用したメタデータ形式をインポートする WCF のロジックをインポートするためのサポートを実装します。  
  
 カスタム メタデータは、システム指定のメタデータ インポーターでインポートできない XML 要素で構成されます。 通常、これにはカスタム WSDL 拡張とカスタム ポリシー アサーションが含まれます。  
  
 ここでは、カスタム WSDL 拡張とカスタム ポリシー アサーションをインポートする方法について説明します。 インポート プロセス自体には重点を置きません。 型をエクスポートおよびインポートのメタデータがカスタムであるか、システムでサポートされているかどうかに関係なくメタデータを使用する方法の詳細については、次を参照してください。[エクスポートおよびインポートするメタデータ](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)します。  
  
## <a name="overview"></a>概要  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>型の実装は、 <xref:System.ServiceModel.Description.MetadataImporter> WCF に含まれているクラスを抽象化します。 <xref:System.ServiceModel.Description.WsdlImporter> 型は、<xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> オブジェクトにまとめられた、結び付けられているポリシーを使用して WSDL メタデータをインポートします。 既定のインポーターが認識しないポリシー アサーションおよび WSDL 拡張は、インポートに使用される登録済みのカスタム ポリシーおよびカスタム WDSL インポーターに渡されます。 通常、インポーターは、ユーザー定義のバインド要素をサポートしたりインポートされたコントラクトを変更したりする目的で実装されます。  
  
 ここでは、次の内容について説明します。  
  
1. 説明の生成とコードの生成を行う前に、カスタム インポーターに WSDL データを公開する <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。 このインターフェイスは、特定のメタデータ セットを使用して実行される説明の種類とコードのコンパイルを確認または変更するために使用できます。  
  
2. 説明オブジェクトを生成する前に、インポーターにポリシー アサーションを公開する <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。 このインターフェイスは、ダウンロードしたポリシーに基づいてバインディングまたはコントラクトを確認または変更するために使用できます。  
  
 カスタム WSDL とポリシー アサーションをエクスポートする方法の詳細については、次を参照してください。 [WCF 拡張機能のカスタム メタデータのエクスポート](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)します。  
  
## <a name="importing-custom-wsdl-extensions"></a>カスタム WSDL 拡張のインポート  
 WSDL 拡張のインポートをサポートするには、<xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスを実装し、その実装を <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> プロパティに追加します。 <xref:System.ServiceModel.Description.WsdlImporter> は、アプリケーション構成ファイルに登録された <xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスの実装を読み込むこともできます。 いくつかの WSDL インポーターが既定で登録されること、および登録された WSDL インポーターの順序に意味があることに注意してください。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> は、カスタム WSDL インポーターを読み込んで使用する場合、インポート プロセスの前にメタデータを変更できるように、まず <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> メソッドを呼び出します。 次に、コントラクトがインポートされたら、メタデータからインポートされたコントラクトを変更できるように <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> メソッドを呼び出します。 最後に、インポートされたエンドポイントを変更できるように <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> メソッドを呼び出します。  
  
 詳細については、「[方法 :カスタム WSDL をインポート](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)します。  
  
### <a name="importing-custom-policy-assertions"></a>カスタム ポリシー アサーションのインポート  
 <xref:System.ServiceModel.Description.WsdlImporter>型と[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)さまざまな WSDL ドキュメントに結び付けられたポリシー表現でのポリシー アサーションの種類を自動的に処理します。 これらのツールは、WSDL バインディングや WSDL ポートに結び付けられたポリシー表現の収集、正規化、およびマージを行います。  
  
 カスタム ポリシー アサーションのインポートをサポートするには、<xref:System.ServiceModel.Description.IPolicyImportExtension> インターフェイスを実装し、その実装を <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> プロパティに追加します。 <xref:System.ServiceModel.Description.MetadataImporter> は、アプリケーション構成ファイルに登録された <xref:System.ServiceModel.Description.IPolicyImportExtension> インターフェイスの実装を読み込むこともできます。 いくつかのポリシー インポーターが既定で登録されること、および登録されたポリシー インポーターの順序に意味があることに注意してください。  
  
 メタデータ システムは、登録されたすべてのポリシー インポート拡張で <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> メソッドを呼び出します。これは、メッセージ、操作、およびエンドポイント ポリシーのサブジェクトに結び付けられたポリシー代替手段の各組み合わせに対して行われます。 WSDL ポートをインポートする場合、ポリシー インポート拡張を呼び出す前に、ポートおよび対応する WSDL バインディングに結び付けられているポリシーがマージされます。 このポリシー代替手段は、<xref:System.ServiceModel.Description.PolicyConversionContext> を通じて、<xref:System.ServiceModel.Description.PolicyAssertionCollection> オブジェクトとして使用可能になります。 各 <xref:System.ServiceModel.Description.PolicyAssertionCollection> は、<xref:System.Xml.XmlElement> オブジェクトによって表されるポリシー アサーションのコレクションです。  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> オブジェクトの <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> プロパティと <xref:System.ServiceModel.Description.PolicyConversionContext> プロパティは、WSDL からインポートされた <xref:System.ServiceModel.Description.ContractDescription> オブジェクトと <xref:System.ServiceModel.Channels.BindingElement> オブジェクトを公開します。 ポリシー アサーションを処理する場合、ポリシー インポート拡張は、特定のポリシー アサーション型のインスタンスを見つけ、対応する変更を <xref:System.ServiceModel.Description.ContractDescription> オブジェクトまたは <xref:System.ServiceModel.Channels.BindingElement> オブジェクトに加えてから、対応する <xref:System.ServiceModel.Description.PolicyAssertionCollection> からそのポリシー アサーションを削除します。  
  
 `wsp:Optional` 属性および入れ子になったポリシー表現は正規化されないため、ポリシー インポート拡張はこれらのポリシー構文を処理する必要があります。 また、ポリシー インポート拡張は、同じ <xref:System.ServiceModel.Description.ContractDescription> オブジェクトと <xref:System.ServiceModel.Channels.BindingElement> オブジェクトで何度でも呼び出される可能性があるため、この動作に対して強固である必要があります。  
  
> [!IMPORTANT]
>  無効なメタデータまたは不適切なメタデータがインポーターに渡される可能性があります。 カスタム インポーターがすべての形式の XML に対して強固であることを確認してください。  
  
## <a name="see-also"></a>関連項目

- [方法: カスタム WSDL をインポートします。](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
- [方法: カスタム ポリシー アサーションをインポートします。](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
- [方法: ServiceContractGenerator の拡張を作成します。](../../../../docs/framework/wcf/extending/how-to-write-an-extension-for-the-servicecontractgenerator.md)
