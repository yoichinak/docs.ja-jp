---
title: カスタム資格情報と資格情報の検証
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795808"
---
# <a name="custom-credential-and-credential-validation"></a>カスタム資格情報と資格情報の検証
Windows Communication Foundation (WCF) のセキュリティは、サービスとクライアント間の資格情報の交換に基づいています。 セキュリティ シナリオの多くは、Windows (Kerberos)、ユーザー名とパスワード、証明書などの共通の資格情報の種類を使用して満たされます。 ただし、新しい種類の資格情報が必要な場合があります。このセクションのこのトピックでは、その新しい種類の処理方法と検証方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: カスタム証明書の検証を使用するサービスを作成します。](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>クラスから継承することによって WCF 検証をカスタマイズする方法について説明します。  
  
 [チュートリアル: カスタムのクライアントおよびサービスの資格情報の作成](walkthrough-creating-custom-client-and-service-credentials.md)  
 新しい資格情報の種類<xref:System.ServiceModel.Description.ClientCredentials>に<xref:System.ServiceModel.Description.ServiceCredentials>対応するために、クラスとクラスを拡張する方法を示します。 これは、カスタム資格情報の種類の作成を実現するトピック シリーズの 1 番目です。  
  
 [方法: カスタムセキュリティトークンプロバイダーを作成する](how-to-create-a-custom-security-token-provider.md)  
 セキュリティ トークン プロバイダーを作成して新しい資格情報の種類を処理し、その資格情報の新しいトークンを返す方法を説明します。 これは、シリーズの 2 番目のトピックです。  
  
 [方法: カスタムセキュリティトークン認証システムを作成する](how-to-create-a-custom-security-token-authenticator.md)  
 カスタム認証システムを作成して新しい資格情報の種類を認証する方法を説明します。 これは、シリーズの 3 番目のトピックです。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>関連項目  
 [認証](../feature-details/authentication-in-wcf.md)  
  
 [フェデレーションと発行済みトークン](../feature-details/federation-and-issued-tokens.md)  
  
 [承認](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>関連項目

- [Security](../feature-details/security.md)
