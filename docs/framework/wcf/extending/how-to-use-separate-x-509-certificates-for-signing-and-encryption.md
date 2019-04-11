---
title: '方法: 署名および暗号化に個別の X.509 証明書を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: f95274861f58d1581e4c5439861ebf186b1b3489
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332561"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>方法: 署名および暗号化に個別の X.509 証明書を使用する
このトピックでは、メッセージの署名と暗号化がクライアントとサービスの両方で異なる証明書を使用するように、Windows Communication Foundation (WCF) を構成する方法を示します。  
  
 署名と暗号化に使用する別の証明書を有効にするには、WCF が複数のクライアントまたはサービスの証明書を設定するための API を提供しないためには、カスタムのクライアントまたはサービスの資格情報 (または両方) を作成する必要があります。 さらに、複数の証明書の情報を利用し、指定されたキーの使用方法やメッセージの方向について適切なセキュリティ トークン プロバイダーを作成するために、セキュリティ トークン マネージャーを用意する必要があります。  
  
 使用される主要なクラス、そのクラスの継承元のクラス (上向きの矢印で表示)、および特定のメソッドおよびプロパティの戻り値の型を次の図に示します。  
  
-   `MyClientCredentials` カスタム実装は、<xref:System.ServiceModel.Description.ClientCredentials>します。  
  
    -   図に示されたすべてのプロパティは、すべて <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> のインスタンスを返します。  
  
    -   メソッド <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> は、`MyClientCredentialsSecurityTokenManager` のインスタンスを返します。  
  
-   `MyClientCredentialsSecurityTokenManager` カスタム実装は、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>します。  
  
    -   メソッド <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> は、<xref:System.IdentityModel.Selectors.X509SecurityTokenProvider> のインスタンスを返します。  
  
 ![クライアントの資格情報を使用する方法を示す図](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 カスタム資格情報の詳細については、次を参照してください。[チュートリアル。カスタムのクライアントとサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)します。  
  
 また、カスタム ID 検証機能を作成し、カスタム バインドのセキュリティ バインド要素にリンクする必要があります。 さらに、既定の資格情報の代わりにカスタム資格情報を使用する必要があります。  
  
 カスタム バインドに関連したクラス、およびカスタム ID 検証機能のリンク方法を次の図に示します。 関連するバインド要素はいくつかありますが、そのすべてが <xref:System.ServiceModel.Channels.BindingElement> から継承されています。 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> には、<xref:System.ServiceModel.Channels.LocalClientSecuritySettings> プロパティがあります。このプロパティは、<xref:System.ServiceModel.Security.IdentityVerifier> のカスタマイズの元となる `MyIdentityVerifier` のインスタンスを返します。  
  
 ![カスタム バインド要素を示す図](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 カスタム id 検証機能を作成する方法の詳細については、次を参照してください。 方法。[方法: カスタムのクライアント Id 検証機能作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)です。  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>署名と暗号化に別個の証明書を使用するには  
  
1. <xref:System.ServiceModel.Description.ClientCredentials> クラスを継承する新しいクライアント資格情報クラスを定義します。 複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。 また、<xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2. <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承する新しいクライアント セキュリティ トークン マネージャーを定義します。 適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。 メッセージの方向とキーの使用方法は、`requirement` パラメーター (<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) で提供されます。  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3. <xref:System.ServiceModel.Description.ServiceCredentials> クラスを継承する新しいサービス資格情報クラスを定義します。 複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。 また、<xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4. <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスを継承する新しいサービス セキュリティ トークン マネージャーを定義します。 渡されたメッセージの方向とキーの使用方法について適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>クライアントで複数の証明書を使用するには  
  
1. カスタム バインドの作成 セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。 これを行うには、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。 次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.IdentityVerifier> をセキュリティ バインド要素にリンクします。 既定のクライアント資格情報を、事前に作成したカスタマイズ済みのクライアント資格情報に置き換えます。  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2. カスタム <xref:System.ServiceModel.Security.IdentityVerifier> を定義します。 要求の暗号化と応答への署名で異なる証明書が使用されるため、サービスには複数の ID があります。  
  
    > [!NOTE]
    >  次のサンプルで用意されたカスタム ID 検証方法では、デモンストレーション用であるため、エンドポイント ID 検査がまったく行われません。 これは製品版のコードでは、お勧めしません。  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>サービスで複数の証明書を使用するには  
  
1. カスタム バインドの作成 セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。 クライアントの場合と同様に、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。 既定のサービス資格情報を、事前に作成したカスタマイズ済みのサービス資格情報に置き換えます。  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
