---
title: '方法: X.509 証明書の秘密キーの暗号化サービス プロバイダーを変更します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 4e11dd90d1cc57f3f2f559c22e1548b8fbcedaea
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261913"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a>方法: X.509 証明書の秘密キーの暗号化サービス プロバイダーを変更します。
このトピックでは、X.509 証明書の秘密キーを提供するために使用する暗号化サービス プロバイダーを変更する方法と、Windows Communication Foundation (WCF) のセキュリティ フレームワークにプロバイダーを統合する方法を示します。 証明書の使用に関する詳細については、[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)を参照してください。  
  
 WCF のセキュリティ フレームワークは」の説明に従って、新しいセキュリティ トークンの種類を導入する方法を提供します。[方法。カスタム トークンを作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。 また、カスタム トークンを使用して既存のシステム指定のトークンを置き換えることも可能です。  
  
 このトピックでは、システム指定の X.509 セキュリティ トークンが、証明書の秘密キーに別の実装を提供するカスタムの X.509 トークンによって置き換えられます。 これは、実際の秘密キーが、既定の Windows 暗号化プロバイダーとは異なる暗号化プロバイダーから提供されるシナリオで役立ちます。 別の暗号化プロバイダーの例として、ハードウェア セキュリティ モジュールがあります。このモジュールでは、すべての秘密キー関連の暗号操作を実行し、メモリに秘密キーを格納しないので、システムのセキュリティが向上します。  
  
 次の例は、デモンストレーションのためだけに作成されています。 この例では、既定の Windows 暗号化プロバイダーを置き換えていませんが、Windows 暗号化プロバイダーをどこで統合できるかを示します。  
  
## <a name="procedures"></a>手順  
 セキュリティ キーが関連付けられているセキュリティ トークンごとに、セキュリティ トークンのインスタンスからキーのコレクションを返す <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> プロパティを実装する必要があります。 トークンが X.509 セキュリティ トークンの場合、コレクションには、証明書に関連付けられた公開キーと秘密キーの両方を表す <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> クラスのインスタンスが 1 つ追加されます。 証明書のキーの提供に使用する既定の暗号化プロバイダーを置き換えるには、このクラスの新しい実装を作成します。  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>カスタムの X.509 非対称キーを作成するには  
  
1.  <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> クラスから派生する新しいクラスを定義します。  
  
2.  <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> 読み取り専用プロパティをオーバーライドします。 このプロパティは、証明書の公開キーと秘密キーのペアの実際のキー サイズを返します。  
  
3.  <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> メソッドをオーバーライドします。 このメソッドは、証明書の秘密キーで対称キーを復号化する WCF のセキュリティ フレームワークによって呼び出されます。 (このキーは、以前に証明書の公開キーで暗号化されています)。  
  
4.  <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> メソッドをオーバーライドします。 このメソッドのインスタンスを取得するために WCF のセキュリティ フレームワークによって呼び出されます、<xref:System.Security.Cryptography.AsymmetricAlgorithm>メソッドに渡されるか、証明書のプライベートまたはパブリック キー、によって、パラメーターの暗号化サービス プロバイダーを表すクラス。  
  
5.  任意。 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> メソッドをオーバーライドします。 <xref:System.Security.Cryptography.HashAlgorithm> クラスの別の実装が必要な場合は、このメソッドをオーバーライドします。  
  
6.  <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> メソッドをオーバーライドします。 このメソッドは、証明書の秘密キーに関連付けられた <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> クラスのインスタンスを返します。  
  
7.  <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> メソッドをオーバーライドします。 このメソッドを使用して、特定の暗号アルゴリズムがセキュリティ キー実装によってサポートされているかどうかを示します。  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 次の手順は、トークンのカスタム X.509 非対称セキュリティ キー実装システム指定の X.509 セキュリティを置換するには、WCF のセキュリティ フレームワーク、前の手順で作成したを統合する方法を示します。  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>システム指定の X.509 セキュリティ トークンをカスタムの X.509 非対称セキュリティ キー トークンで置き換えるには  
  
1.  次の例に示すように、システム指定のセキュリティ キーではなく、カスタムの X.509 非対称セキュリティ キーを返すカスタムの X.509 非対称セキュリティ トークンを作成します。 カスタム セキュリティ トークンの詳細については、次を参照してください。[方法。カスタム トークンを作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  次の例に示すように、カスタムの X.509 セキュリティ トークンを返すカスタムのセキュリティ トークン プロバイダーを作成します。 カスタム セキュリティ トークン プロバイダーの詳細については、次を参照してください。[方法。カスタム セキュリティ トークン プロバイダーを作成](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)です。  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  イニシエーター側でカスタム セキュリティ キーを使用する必要がある場合、次の例に示すように、カスタムのクライアント セキュリティ トークン マネージャーとカスタムのクライアント資格情報クラスを作成します。 カスタム クライアント資格情報とクライアント セキュリティ トークン マネージャーの詳細については、次を参照してください。[チュートリアル。カスタムのクライアントとサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)します。  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  受信側でカスタム セキュリティ キーを使用する必要がある場合、次の例に示すように、カスタムのサービス セキュリティ トークン マネージャーとカスタムのサービス資格情報クラスを作成します。 カスタム サービス資格情報とサービス セキュリティ トークン マネージャーの詳細については、次を参照してください。[チュートリアル。カスタムのクライアントとサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)します。  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [チュートリアル: カスタムのクライアントとサービスの資格情報を作成します。](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [カスタム セキュリティ トークン オーセンティケーターを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [カスタム セキュリティ トークン プロバイダーを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [カスタム トークンを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
