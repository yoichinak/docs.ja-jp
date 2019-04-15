---
ms.openlocfilehash: 878aef544b2706bfd10a3dddce1b902655ef003a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761043"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims は、すべての claimTypes を考慮します

|   |   |
|---|---|
|説明|X509 クレーム セットがその SAN フィールド内の複数の DNS エントリを含む証明書から初期化される場合は、.NET Framework 4.6.1 を対象とするアプリで、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name>メソッドをすべての DNS エントリの claimType 引数と一致を試みます。 .NET Framework の以前のバージョンを対象とするアプリに対して、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name>メソッドは claimType 引数と最後の DNS エントリのみを一致させようとしています。|
|提案される解決策|この変更は、.NET Framework 4.6.1 を対象とするアプリケーションのみに影響します。 この変更は、[DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 互換性スイッチで無効にできます (または、4.6.1 より前を対象としている場合は、有効にできます)。|
|スコープ|マイナー|
|Version|4.6.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

