---
title: WCF 拡張に対するカスタム メタデータのインポート
ms.date: 03/30/2017
ms.assetid: 78beb28f-408a-4c75-9c3c-caefe9595b1a
ms.openlocfilehash: f6f858cbe86bd2965decf42be5daa7b3f7d3c8c2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796930"
---
# <a name="importing-custom-metadata-for-a-wcf-extension"></a>WCF 拡張に対するカスタム メタデータのインポート
Windows Communication Foundation (WCF) では、メタデータのインポートは、サービスまたはそのコンポーネントの部分の抽象表現をメタデータから生成するプロセスです。 たとえば、WCF では、 <xref:System.ServiceModel.Description.ServiceEndpoint>サービスの<xref:System.ServiceModel.Channels.Binding> WSDL ドキュメント<xref:System.ServiceModel.Description.ContractDescription>からインスタンス、インスタンス、またはインスタンスをインポートできます。 WCF でサービスメタデータをインポートするには、 <xref:System.ServiceModel.Description.MetadataImporter?displayProperty=nameWithType>抽象クラスの実装を使用します。 クラスから派生する型<xref:System.ServiceModel.Description.MetadataImporter>は、WCF の ws-policy インポートロジックを利用するメタデータ形式をインポートするためのサポートを実装します。  
  
 カスタム メタデータは、システム指定のメタデータ インポーターでインポートできない XML 要素で構成されます。 通常、これにはカスタム WSDL 拡張とカスタム ポリシー アサーションが含まれます。  
  
 ここでは、カスタム WSDL 拡張とカスタム ポリシー アサーションをインポートする方法について説明します。 インポート プロセス自体には重点を置きません。 メタデータがカスタムまたはシステムでサポートされているかどうかに関係なく、メタデータをエクスポートおよびインポートする型の使用方法の詳細については、「[メタデータのエクスポートとインポート](../feature-details/exporting-and-importing-metadata.md)」を参照してください。  
  
## <a name="overview"></a>概要  
 型は、WCF に含まれる<xref:System.ServiceModel.Description.MetadataImporter>抽象クラスの実装です。 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlImporter> 型は、<xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> オブジェクトにまとめられた、結び付けられているポリシーを使用して WSDL メタデータをインポートします。 既定のインポーターが認識しないポリシー アサーションおよび WSDL 拡張は、インポートに使用される登録済みのカスタム ポリシーおよびカスタム WDSL インポーターに渡されます。 通常、インポーターは、ユーザー定義のバインド要素をサポートしたりインポートされたコントラクトを変更したりする目的で実装されます。  
  
 ここでは、次の内容について説明します。  
  
1. 説明の生成とコードの生成を行う前に、カスタム インポーターに WSDL データを公開する <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。 このインターフェイスは、特定のメタデータ セットを使用して実行される説明の種類とコードのコンパイルを確認または変更するために使用できます。  
  
2. 説明オブジェクトを生成する前に、インポーターにポリシー アサーションを公開する <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装して使用する方法。 このインターフェイスは、ダウンロードしたポリシーに基づいてバインディングまたはコントラクトを確認または変更するために使用できます。  
  
 カスタム WSDL およびポリシーアサーションのエクスポートの詳細については、「 [WCF 拡張機能のカスタムメタデータのエクスポート](exporting-custom-metadata-for-a-wcf-extension.md)」を参照してください。  
  
## <a name="importing-custom-wsdl-extensions"></a>カスタム WSDL 拡張のインポート  
 WSDL 拡張のインポートをサポートするには、<xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスを実装し、その実装を <xref:System.ServiceModel.Description.WsdlImporter.WsdlImportExtensions%2A> プロパティに追加します。 <xref:System.ServiceModel.Description.WsdlImporter> は、アプリケーション構成ファイルに登録された <xref:System.ServiceModel.Description.IWsdlImportExtension> インターフェイスの実装を読み込むこともできます。 いくつかの WSDL インポーターが既定で登録されること、および登録された WSDL インポーターの順序に意味があることに注意してください。  
  
 <xref:System.ServiceModel.Description.WsdlImporter> は、カスタム WSDL インポーターを読み込んで使用する場合、インポート プロセスの前にメタデータを変更できるように、まず <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%2A> メソッドを呼び出します。 次に、コントラクトがインポートされたら、メタデータからインポートされたコントラクトを変更できるように <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%2A> メソッドを呼び出します。 最後に、インポートされたエンドポイントを変更できるように <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%2A> メソッドを呼び出します。  
  
 詳細については、「[方法 :カスタム WSDL](how-to-import-custom-wsdl.md)をインポートします。  
  
### <a name="importing-custom-policy-assertions"></a>カスタム ポリシー アサーションのインポート  
 型<xref:System.ServiceModel.Description.WsdlImporter>と[ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)は、WSDL ドキュメントに関連付けられているポリシー式に含まれるさまざまな種類のポリシーアサーションの処理を自動的に処理します。 これらのツールは、WSDL バインディングや WSDL ポートに結び付けられたポリシー表現の収集、正規化、およびマージを行います。  
  
 カスタム ポリシー アサーションのインポートをサポートするには、<xref:System.ServiceModel.Description.IPolicyImportExtension> インターフェイスを実装し、その実装を <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A> プロパティに追加します。 <xref:System.ServiceModel.Description.MetadataImporter> は、アプリケーション構成ファイルに登録された <xref:System.ServiceModel.Description.IPolicyImportExtension> インターフェイスの実装を読み込むこともできます。 いくつかのポリシー インポーターが既定で登録されること、および登録されたポリシー インポーターの順序に意味があることに注意してください。  
  
 メタデータ システムは、登録されたすべてのポリシー インポート拡張で <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> メソッドを呼び出します。これは、メッセージ、操作、およびエンドポイント ポリシーのサブジェクトに結び付けられたポリシー代替手段の各組み合わせに対して行われます。 WSDL ポートをインポートする場合、ポリシー インポート拡張を呼び出す前に、ポートおよび対応する WSDL バインディングに結び付けられているポリシーがマージされます。 このポリシー代替手段は、<xref:System.ServiceModel.Description.PolicyConversionContext> を通じて、<xref:System.ServiceModel.Description.PolicyAssertionCollection> オブジェクトとして使用可能になります。 各 <xref:System.ServiceModel.Description.PolicyAssertionCollection> は、<xref:System.Xml.XmlElement> オブジェクトによって表されるポリシー アサーションのコレクションです。  
  
 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A> オブジェクトの <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A> プロパティと <xref:System.ServiceModel.Description.PolicyConversionContext> プロパティは、WSDL からインポートされた <xref:System.ServiceModel.Description.ContractDescription> オブジェクトと <xref:System.ServiceModel.Channels.BindingElement> オブジェクトを公開します。 ポリシー アサーションを処理する場合、ポリシー インポート拡張は、特定のポリシー アサーション型のインスタンスを見つけ、対応する変更を <xref:System.ServiceModel.Description.ContractDescription> オブジェクトまたは <xref:System.ServiceModel.Channels.BindingElement> オブジェクトに加えてから、対応する <xref:System.ServiceModel.Description.PolicyAssertionCollection> からそのポリシー アサーションを削除します。  
  
 `wsp:Optional` 属性および入れ子になったポリシー表現は正規化されないため、ポリシー インポート拡張はこれらのポリシー構文を処理する必要があります。 また、ポリシー インポート拡張は、同じ <xref:System.ServiceModel.Description.ContractDescription> オブジェクトと <xref:System.ServiceModel.Channels.BindingElement> オブジェクトで何度でも呼び出される可能性があるため、この動作に対して強固である必要があります。  
  
> [!IMPORTANT]
> 無効なメタデータまたは不適切なメタデータがインポーターに渡される可能性があります。 カスタム インポーターがすべての形式の XML に対して強固であることを確認してください。  
  
## <a name="see-also"></a>関連項目

- [方法: カスタム WSDL のインポート](how-to-import-custom-wsdl.md)
- [方法: カスタムポリシーアサーションをインポートする](how-to-import-custom-policy-assertions.md)
- [方法: ServiceContractGenerator の拡張機能を作成する](how-to-write-an-extension-for-the-servicecontractgenerator.md)
