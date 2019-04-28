---
title: WIF API リファレンス
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: c94ccd3f25be576c57fda798c6b2b8cc25357022
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645891"
---
# <a name="wif-api-reference"></a>WIF API リファレンス
Windows Identity Foundation (WIF) クラスは、`mscorlib` (mscorlib.dll)、`System.IdentityModel` (System.IdentityModel.dll)、`System.IdentityModel.Services` (System.IdentityModel.Services.dll)、および `System.ServiceModel` (System.ServiceModel.dll) というアセンブリに分割されています。 このトピックでは、WIF 名前空間のリンクを紹介し、各名前空間に含まれるクラスについて簡単に説明します。  
  
> [!IMPORTANT]
>  `System.IdentityModel`、<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、および <xref:System.IdentityModel.Policy?displayProperty=nameWithType> という <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> 名前空間には、WCF クレーム ベースの ID モデルを実装するクラスが含まれます。 .NET Framework 4.5 以降、WCF クレーム ベース ID モデルは WIF に置き換えられています。 WIF に基づいてソリューションをビルドする際は、これら 3 つの名前空間でクラスを使用しないでください。  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 クッキーの変換、セキュリティ トークン サービス、および特殊な XML ディクショナリ リーダーを表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Windows Identity Foundation (WIF) を使用して構築されたアプリケーションとサービスの構成を提供するクラスが含まれます。 この名前空間のクラスは、[\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 要素の設定を表しています。  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 フェデレーション メタデータ ドキュメントの要素を表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 WS-Trust 成果物を表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 受動的な (WS-Federation) シナリオで使用されるクラスが含まれます。 また、[\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 要素の設定を表すクラスもいくつか含まれています。 この要素の設定で、アプリケーションの WS-Federation を構成します。 `System.IdentityModel.Services.Configuration` 名前空間には、WS-Federation の構成に使用されるほとんどのクラスが含まれます。  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 WS-Federation プロトコルを使用する WIF アプリケーションに構成を提供するクラスが含まれます。 この名前空間内のクラスは、[\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 要素の設定を表します。 また、`System.IdentityModel.Services` 名前空間には、WS-Federation の構成に使用されるいくつかのクラスが含まれます。  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Web ファーム シナリオの特殊なセキュリティ トークン ハンドラーが含まれます。  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 セキュリティ トークン、セキュリティ トークン ハンドラー、およびその他のセキュリティ トークンの成果物を表すクラスが含まれます。  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 クレーム、クレーム ベースの ID、クレーム ベースの原則、およびその他のクレーム ベースの ID モデル成果物を表すクラスが含まれます。  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 アクティブな (WS-Trust) シナリオで使用される WCF のコントラクト、チャネル、サービス ホスト、およびその他の成果物を表すクラスが含まれています。 この名前空間には、Windows Communication Foundation (WCF) 固有で、WIF が使用していないクラスも含まれています。  
  
## <a name="see-also"></a>関連項目

- [WIF 構成のリファレンス](../../../docs/framework/security/wif-configuration-reference.md)
- [WIF 3.5 と WIF 4.5 間での名前空間マッピング](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
