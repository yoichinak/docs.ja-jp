---
title: '方法: WCF クライアントと WSE3.0 サービスを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699553"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>方法: WCF クライアントと WSE3.0 サービスを相互運用するために構成する
Windows Communication Foundation (WCF) クライアントと Microsoft .NET (WSE) サービスの Web サービス拡張 3.0 とネットワーク レベル互換性は、Ws-addressing 仕様の 2004 年 8 月バージョンを使用する WCF クライアントが構成されている場合。  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>WSE 3.0 Web サービスと相互運用するように WCF クライアントを構成するには  
  
1. 実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web サービスの WCF クライアントを作成します。  
  
     WSE Web サービス、WCF クライアント クラスが作成されます。  
  
     WCF クライアントを作成する方法については、次を参照してください。、[方法。クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)します。  
  
2. WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。  
  
     次のクラスの一部である、 [WSE との相互運用](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)サンプル。  
  
    1. <xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。  
  
         `WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. WSE の設定不要アサーションを指定するクラスに、派生キーが必要か、セキュリティで保護されたセッションが使用されるか、署名の確認が必要かどうかの指定、およびメッセージ保護設定などのプロパティを追加します。  
  
         次のコード例を定義、 `SecurityAssertion`、 `RequireDerivedKeys`、 `EstablishSecurityContext`、および`MessageProtectionOrder`プロパティ。 WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうかおよびメッセージ保護設定をそれぞれ指定します。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。  
  
         `SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。  
  
     次のコード例では、ことは、WSE 3.0 で定義されていると、WCF クライアントにそのメッセージの保護と認証の設定が使用する必要がありますを指定します`AnonymousForCertificate`設定不要のセキュリティ アサーション。 また、セキュリティで保護されたセッションと派生キーが必要です。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>例  
 WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。 名前は、カスタムのバインディング`WseHttpBinding`、使用して、WCF クライアントのバインドのプロパティを指定します。  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.Binding>
- [WSE との相互運用](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
