---
title: WIF 構成スキーマの規則
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: c02d467260a5197cdd01a3819f8a323655a8a08f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045094"
---
# <a name="wif-configuration-schema-conventions"></a>WIF 構成スキーマの規則
このトピックでは、Windows Identity Foundation (WIF) 構成トピックを通して利用される規則について説明し、[\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) セクションと [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) セクションで利用されるいくつかの一般的な機能と属性について説明します。  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>モード  
 WIF 構成要素の多くに `mode` 属性があります。 この属性は通常、処理の特定の部分に使用されるクラスと、現在の要素の子要素として許可される構成要素を制御します。 構成ファイルに含まれる要素がモード設定により無視される場合、構成エラーが生成されます。  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>TimeSpan 値  
 <xref:System.TimeSpan> は属性の種類として使用されます。許可される形式については、<xref:System.TimeSpan.Parse%28System.String%29> メソッドをご覧ください。 この形式は、次の仕様に準拠しています。  
  
`[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]`  
  
 たとえば、"30"、"30.00:00"、"30.00:00:00" はすべて 30 日を意味します。"00:05"、"00:05:00"、"0.00:05:00.00" はすべて 5 分を意味します。  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>証明書参照  
 いくつかの要素は、`<certificateReference>` 要素を利用し、証明書参照を受け取ります。 証明書を参照するとき、次の属性が利用できます。  
  
|||  
|-|-|  
|`storeLocation`|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> 列挙の値: `CurrentUser` または `CurrentMachine`。|  
|`storeName`|<xref:System.Security.Cryptography.X509Certificates.StoreName> 列挙の値。このコンテキストで最も有用なものは `My` と `TrustedPeople` です。|  
|`x509FindType`|<xref:System.Security.Cryptography.X509Certificates.X509FindType> 列挙の値。このコンテキストで最も有用なものは `FindBySubjectName` と `FindByThumbprint` です。 エラーの可能性をなくすために、運用環境では `FindByThumbprint` 型を使用することが推奨されます。|  
|`findValue`|`x509FindType` 属性に基づき、証明書を検出するために使用される値。 エラーの可能性をなくすために、運用環境では `FindByThumbprint` 型を使用することが推奨されます。 `FindByThumbPrint` が指定されると、この属性は、"97249e1a5fa6bee5e515b82111ef524a4c91583f" のような、16 進数文字列形式の証明書拇印である値を受け取ります。|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>カスタム型の参照  
 いくつかの要素は、`type` 属性を利用し、カスタム型を参照します。 この属性では、カスタム型の名前を指定する必要があります。 グローバル アセンブリ キャッシュ (GAC) から型を参照するには、厳密な名前を使用する必要があります。 Bin/ ディレクトリのアセンブリから型を参照するために、単純なアセンブリ修飾参照を利用できます。 App_Code/ ディレクトリに定義されている型は、アセンブリ修飾のない型名を指定することでも参照できます。  
  
 カスタム型は、指定された型から派生する必要があります。`public` の既定 (0 引数) コンストラクターを提供する必要があります。  
  
## <a name="see-also"></a>関連項目

- [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
