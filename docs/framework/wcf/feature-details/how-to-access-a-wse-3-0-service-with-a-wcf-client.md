---
title: '方法: WSE 3.0 へのアクセス、WCF クライアントとサービス'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 1b8b344c713fdd27c67cf98c51c8c69198fd508f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127465"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>方法: WSE 3.0 へのアクセス、WCF クライアントとサービス
Windows Communication Foundation (WCF) クライアントは、Ws-addressing 仕様の 2004 年 8 月バージョンを使用する WCF クライアントが構成されている場合、Microsoft .NET services のワイヤレベルの互換性のある Web Services Enhancements (WSE) 3.0 が。 ただし、WSE 3.0 サービスは、メタデータ交換 (MEX) プロトコルをサポートしないので使用すると、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WCF クライアント クラスを作成するセキュリティ設定は適用されませんを生成されました。WCF クライアントです。 そのため、セキュリティの設定を指定する必要があります、WCF クライアントが生成された後に、WSE 3.0 サービスが必要であります。  
  
 これらのセキュリティ設定を適用するには、カスタム バインドを使用して、WSE 3.0 サービスの要件と WSE 3.0 サービスと WCF クライアントの間の相互運用可能な要件を考慮します。 これらの相互運用性要件には、前述の 2004 年 8 月版 WS-Addressing 仕様の使用と、WSE 3.0 の既定のメッセージ保護が <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> であることが含まれます。 WCF の既定のメッセージ保護は<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>します。 このトピックでは、WSE 3.0 サービスと相互運用する WCF バインドを作成する方法について説明します。 WCF には、このバインディングが組み込まれているサンプルも用意されています。 このサンプルの詳細については、次を参照してください。 [ASMX Web サービスとの相互運用](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)します。  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>WCF クライアントで WSE 3.0 サービスにアクセスするには  
  
1.  実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web サービスの WCF クライアントを作成します。  
  
     WSE 3.0 Web サービスの場合、WCF クライアントが作成されます。 WSE 3.0 は MEX プロトコルをサポートしていないため、このツールを使用して Web サービスのセキュリティ要件を取得することはできません。 アプリケーション開発者は、クライアントのセキュリティ設定を追加する必要があります。  
  
     WCF クライアントを作成する方法の詳細については、次を参照してください。、[方法。クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)します。  
  
2.  WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。  
  
     次のクラスの一部である、 [WSE との相互運用](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)サンプル。  
  
    1.  <xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。  
  
         `WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  WSE サービスで使用する WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定するプロパティを、このクラスに追加します。 WSE 3.0 では、設定不要アサーションは、クライアントまたは Web サービスのセキュリティ要件を指定します: WCF のバインドの認証モードと似ています。  
  
         WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定をそれぞれ指定する、`SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext`、および `MessageProtectionOrder` の各プロパティを定義するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。  
  
         `SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。  
  
     次のコード例では、ことは、WSE 3.0 で定義されていると、WCF クライアントにそのメッセージの保護と認証の設定が使用する必要がありますを指定します`AnonymousForCertificate`設定不要のセキュリティ アサーション。 また、セキュリティで保護されたセッションと派生キーが必要です。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>例  
 WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。 という名前のカスタムのバインディング、 `WseHttpBinding`、使用して、WSSecurityAnonymous WSE 3.0 QuickStart サンプルと通信する WCF クライアントのバインドのプロパティを指定します。  

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- [WSE との相互運用性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
