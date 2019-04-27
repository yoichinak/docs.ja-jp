---
title: フェデレーションと発行済みトークン
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 5ea30c2e9593f289c91a47cc082becf47dedc450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856454"
---
# <a name="federation-and-issued-tokens"></a>フェデレーションと発行済みトークン
Windows Communication Foundation (WCF) で、Ws-federation および Ws-trust 仕様を実装するサービスを安全に通信するクライアントを作成できます。 これらの仕様では、異なる信頼領域間での認証と承認を可能にする機構を提供するために、XML、SOAP、および Web サービス記述言語 (WSDL: Web Services Description Language) が使用されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)  
 フェデレーションの概要を説明します。  
  
 [フェデレーションと信頼](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 フェデレーション サービスまたはクライアントを作成するときに注意する必要がある設計上の問題を示します。  
  
 [方法: フェデレーション クライアントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 WCF を使用したフェデレーション クライアントの作成の基本について説明します。  
  
 [方法: フェデレーション サービスで資格情報を構成します。](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 フェデレーション サービスを作成する手順を説明します。  
  
 [方法: WSFederationHttpBinding を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 `WSFederationHttpBinding` を使用するクライアントおよびサービスを構成する方法を説明します。  
  
 [方法: セキュリティ トークン サービスを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 セキュリティ トークン サービスを作成する手順を説明します。  
  
 [SAML (Security Assertions Markup Language) トークンとクレーム](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 多様なクレームの種類を作成できる拡張可能な SAML (Security Assertions Markup Language) トークンについて説明します。  
  
 [方法: ローカル発行者を構成します。](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 セキュリティ トークンのローカル発行者の作成方法を説明します。  
  
 [方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にします。](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 `WSFederationHttpBinding` のセキュリティで保護されたセッションを無効にする方法を説明します。 クライアントごとにセッションが必要になる Web ファームを作成する場合には、セキュリティで保護されたセッションを無効化する必要があります。  
  
## <a name="reference"></a>参照  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>関連項目

- [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [カスタム トークン](../../../../docs/framework/wcf/extending/custom-tokens.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
