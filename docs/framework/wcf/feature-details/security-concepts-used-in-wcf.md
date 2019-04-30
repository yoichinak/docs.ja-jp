---
title: WCF で使用されるセキュリティの概要
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 3ef2b9c104fa15de17a769c9ca9354e5cef085bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990874"
---
# <a name="security-concepts-used-in-wcf"></a>WCF で使用されるセキュリティの概要
Windows Communication Foundation (WCF) のセキュリティは既に使用されている概念に基づいて構築されており、さまざまなセキュリティ インフラストラクチャにデプロイされています。  
  
 WCF など Secure Sockets Layer (SSL) over HTTP (HTTPS)、これらのインフラストラクチャの一部サポートしています。 ただし、WCF はを超えて (Ws-security) などの新しい相互運用可能なセキュリティ標準を実装することで既存のセキュリティ インフラストラクチャをサポートしている SOAP エンコード済みメッセージの上に移動します。 既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。 既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web サービスのセキュリティの概要  
 Microsoft Patterns and Practices グループは、これは、ここでダウンロード可能な WCF セキュリティ ガイダンスに関する、詳細なホワイト ペーパーを作成しました。[WCF セキュリティ ガイド](https://go.microsoft.com/fwlink/?LinkId=210210)します。 このホワイト ペーパーでは、Web サービス、WCF セキュリティの主な概念、イントラネット アプリケーション シナリオ、およびインターネット アプリケーション シナリオに関連するセキュリティの基本概念について説明しています。  
  
## <a name="industry-wide-security-specifications"></a>業界標準のセキュリティ仕様  
  
### <a name="public-key-infrastructure"></a>公開キー基盤  
 公開キー基盤 (PKI: Public Key Infrastructure) は、デジタル証明書、証明機関、およびその他の登録機関で構成されるシステムです。PKI では、公開キー暗号化を使用して、電子取引に関与する各当事者の検証と認証を行います。 詳細については、次を参照してください。 [Windows Server 2008 R2 の証明書サービス](https://go.microsoft.com/fwlink/?LinkId=210211)します。  
  
### <a name="kerberos-protocol"></a>Kerberos プロトコル  
 *Kerberos プロトコル*仕様は、Windows ドメインでユーザーを認証するセキュリティ メカニズムを作成します。 ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。 Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。 システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。 さらに、以降、 *Web Services Security Kerberos Binding*が広く、発行されたことができます、Kerberos プロトコルを使用するインターネット クライアントと通信 (つまり、Kerberos プロトコルが相互運用可能な)。 Windows での Kerberos プロトコルの実装方法の詳細については、次を参照してください。 [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212)します。  
  
### <a name="x509-certificates"></a>X.509 証明書  
 X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。 詳細については、X.509 証明書を参照してください[X.509 公開キー証明書](https://go.microsoft.com/fwlink/?LinkId=210213)します。 X.509 証明書は証明書ストア内に格納されます。 Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。 異なるストアの詳細については、次を参照してください。[証明書ストア](https://go.microsoft.com/fwlink/?LinkID=87787)します。  
  
## <a name="web-services-security-specifications"></a>Web サービスのセキュリティ仕様  
 システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。 システム指定のバインディングと web サービスの仕様の完全な一覧についてサポートを参照してください。[システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>アクセス制御機構  
 WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。 次に例を示します。  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. ASP.NET メンバーシップ プロバイダー  
  
3. ASP.NET ロール プロバイダー  
  
4. 承認マネージャー  
  
5. ID モデル  
  
 詳細については、これらのトピックは、「[アクセス制御メカニズム](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>関連項目

- [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric のセキュリティ モデル](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
