---
title: '軽減策: X509CertificateClaimSet.FindClaims メソッド'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc03e6c88a2aabb967587d8b1ee7d0b784b4e7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778942"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>軽減策: X509CertificateClaimSet.FindClaims メソッド
<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、.NET Framework 4.6.1 を対象とするアプリから、`claimType` 引数と SAN フィールド内のすべての DNS エントリとの照合を試みます。  
  
## <a name="impact"></a>影響  
 この変更によって影響を受けるのは、.NET Framework 4.6.1 以降のバージョンの .NET Framework を対象とするアプリのみです。  
  
 .NET Framework の以前のバージョンを対象とするアプリの場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、`claimType` 引数と最後の DNS エントリのみの照合を試みます。  
  
## <a name="mitigation"></a>軽減策  
 この変更が望ましくない場合は、.NET Framework 4.6.1 バージョン以降の .NET Framework を対象とするアプリで無効にできます。これは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>関連項目

- [変更の再ターゲット](retargeting-changes-in-the-net-framework-4-6-1.md)
