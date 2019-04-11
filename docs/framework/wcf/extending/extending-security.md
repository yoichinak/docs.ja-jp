---
title: セキュリティの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 95dacf3ef975be1ddd56db747936cca35db50625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099639"
---
# <a name="extending-security"></a>セキュリティの拡張
新しいクレームの種類とカスタム トークンに対応するためには、Windows Communication Foundation (WCF) のセキュリティ インフラストラクチャを拡張できます。 このセクションの各トピックでは、この方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
 [カスタム資格情報と資格情報の検証](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 カスタム資格情報の検証中に ID モデルを使用する方法について説明します。  
  
 [カスタム トークン](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 通常、セキュリティ トークン サービス (STS) から発行されるトークンは SAML トークンです。 ここでは、カスタムのトークンの種類を作成する方法について説明します。  
  
 [カスタム承認](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 カスタム承認を実装する方法について説明します。  
  
 [認証のためのサービスの ID のオーバーライド](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 認証のためにサービスの ID をオーバーライドする方法について説明します。  
  
 [方法: カスタム クライアント ID 検証機能を作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 カスタム エンドポイント ID を検証する方法について説明します。  
  
 [方法: 署名および暗号化に個別の X.509 証明書を使用する](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 通常、メッセージの署名および暗号化は 1 つの証明書を使用して行われます。 ここでは、必要に応じて 2 つの証明書を使用する方法について説明します。  
  
 [方法: X.509 証明書の秘密キーの暗号化プロバイダーを変更する](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 X.509 証明書の秘密キーを提供するために使用する暗号化サービス プロバイダーを変更する方法と、Windows Communication Foundation (WCF) フレームワークにプロバイダーを統合する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>関連項目  
 [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
