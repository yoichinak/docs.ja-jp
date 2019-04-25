---
title: メタデータを使用する場合のセキュリティ上の考慮事項
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: 0dc060475f868923e8c7e4c87ef43ef5912c7ac5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172966"
---
# <a name="security-considerations-with-metadata"></a>メタデータを使用する場合のセキュリティ上の考慮事項
Windows Communication Foundation (WCF) をメタデータ機能を使用する場合は、公開、取得、およびサービスのメタデータを使用してのセキュリティの影響を検討してください。  
  
## <a name="when-to-publish-metadata"></a>メタデータを公開する場合と公開しない場合  
 WCF サービスは、既定ではメタデータを公開しません。 サービスにメタデータ エンドポイントを追加して、WCF サービスのメタデータを公開するメタデータの公開に有効にする必要があります明示的にする (を参照してください[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md))。 メタデータの公開を無効のままにしておけば、攻撃者にとっては侵入経路が少ないことになり、したがって情報漏洩の危険を減らすことができます。 メタデータを公開する必要のないサービスもあります。 必要ないのであれば無効のままにしておくようお勧めします。 使用して、サービス アセンブリから直接メタデータやクライアント コードを生成することもできますに注意してください、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 Svcutil.exe を使用してメタデータをエクスポートする方法の詳細については、次を参照してください。[方法。Svcutil.exe を使用してコンパイル済みサービス コードからメタデータをエクスポート](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)します。  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>セキュリティ保護されたバインディングによるメタデータの公開  
 WCF は、セキュリティで保護されていない既定のメタデータ バインディングと、メタデータへの匿名アクセスを許可します。 WCF サービスを発行するサービスのメタデータでは、サービスに関する詳細な説明が含まれています、意図的または意図せず機密情報を格納します。 たとえば、一般に公開するべきではない、インフラストラクチャ操作に関する情報が入った状態で発行される可能性があるのです。 権限のないアクセスを拒否する方法として、メタデータ エンドポイントで、セキュリティ保護されたバインディングを使う、というものがあります。 メタデータ エンドポイントは HTTP/GET 要求に応答しますが、ここに SSL (Secure Sockets Layer) を使用すれば、メタデータを保護できます。 詳細については、「[方法 :メタデータ エンドポイントをセキュリティで保護された](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)します。  
  
 メタデータ エンドポイントを保護することで、正当なユーザーが、改ざんやなりすましを恐れずに安全にサービス メタデータを取得できる手段も提供されます。  
  
## <a name="using-only-trusted-metadata"></a>信頼できるメタデータのみを使用  
 サービス メタデータを使用すると、サービスの呼び出しに必要なランタイム コンポーネントを自動構築できます。 たとえば、設計時には、クライアント アプリケーションを開発するためにメタデータを利用できます。また、実行時には、メタデータを利用して、クライアントがサービス呼び出しのために使用するバインディングを動的に更新できます。  
  
 サービス メタデータを取得する際、セキュリティ保護された方法を使わないと、改ざんやなりすましのおそれがあります。 メタデータが改ざんされると、知らない間に悪質なサービスに接続されたり、セキュリティ上問題のある設定に切り替えられたり、XML 構造が破壊されたりすることがあります。 メタデータ ドキュメントはかなりの容量になることがあるので、多くの場合、ファイル システムに保存することになります。 改ざんやなりすましを防ぐために、サービス メタデータを要求するときには、できるだけセキュリティで保護されたバインディングを使用してください。  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>安全な技術を使ってメタデータを処理  
 サービス メタデータは多くの場合、MEX (WS-Metadata Exchange) などの標準的なプロトコルを使用して、ネットワーク経由で伝送されます。 メタデータの形式を見ると、多くの場合、他のメタデータを参照する旨の記述ができるようになっています。 <xref:System.ServiceModel.Description.MetadataExchangeClient> 型は、Web サービス記述言語 (WSDL) ドキュメント、XML スキーマ、および MEX ドキュメント内の参照を自動的に処理します。 取得したメタデータから生成される <xref:System.ServiceModel.Description.MetadataSet> オブジェクトのサイズは、使用されている <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> インスタンスの <xref:System.ServiceModel.Description.MetadataExchangeClient> の値と、この `MaxReceivedMessageSize` インスタンスが使用するバインディングの <xref:System.ServiceModel.Description.MetadataExchangeClient> の値に比例します。 動作環境に合わせてこのクォータ値を適切に設定してください。  
  
 WCF では、サービス メタデータは、XML として処理されます。 XML ドキュメントを処理するアプリケーションは、悪質な XML 構造が現れても破綻しないようになっていなければなりません。 使用して、<xref:System.Xml.XmlDictionaryReader>でクォータを適切な XML を処理するときに、設定も、<xref:System.Xml.XmlTextReader.DtdProcessing%2A>プロパティを<xref:System.Xml.DtdProcessing.Prohibit>します。  
  
 WCF では、メタデータ システムは拡張とメタデータの拡張機能は、アプリケーション構成ファイルに登録することができます (を参照してください[メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md))。 メタデータ拡張はどのようなコードでも実行できるので、適切なアクセス制御リスト (ACL) でアプリケーション構成ファイルを保護し、信頼できるメタデータ拡張以外は登録しないようにする必要があります。  
  
## <a name="validating-generated-clients"></a>生成されたクライアントの検証  
 信頼できないソースから取得したメタデータを基にクライアント コードを生成した場合、これがクライアント アプリケーションのセキュリティ ポリシーに合致しているかどうか検証する必要があります。 動作を検証するための専用クライアントを使うか、あるいはツールが生成したコードを目視で検査してください。 クライアントの動作の検証を実装する方法の例は、次を参照してください。[クライアント検証](../../../../docs/framework/wcf/samples/client-validation.md)です。  
  
## <a name="protecting-application-configuration-files"></a>アプリケーション構成ファイルの保護  
 サービスのアプリケーション構成ファイルでは、メタデータを公開する方法、および公開の有無を制御できます。 攻撃者が設定を変更できないように、適切なアクセス制御リスト (ACL) でアプリケーション構成ファイルを保護することをお勧めします。  
  
## <a name="see-also"></a>関連項目

- [方法: メタデータ エンドポイントをセキュリティで保護します。](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
- [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)
