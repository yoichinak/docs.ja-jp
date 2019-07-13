---
title: WCF と国際化ドメイン名
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: c53c22e388ec352b1275018c0b945c9608565084
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932523"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF と国際化ドメイン名
国際化ドメイン名 (IDN) を持つ WCF サービスを許可するためのサポートが追加されました。 国際化ドメイン名とは、非 ASCII 文字を含むドメイン名です。 このサポートには、IDN 名を持つ WCF サービスをホストする機能と、IDN 名を持つ Web サービスとの通信を行う WCF クライアントをホストする機能の両方が含まれます。  
  
## <a name="systemuri-and-idn"></a>System.Uri と IDN  
 <xref:System.Uri> には、<xref:System.Uri.Host%2A> および <xref:System.Uri.DnsSafeHost%2A> という 2 つのプロパティがあります。 これらのプロパティには、IDN 構成設定に応じて Unicode 値または Punycode 値が格納されます。  
  
 IDN をアプリケーションの構成ファイルで有効にするには、次の XML を使用します。  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<Idn > 要素には enabled 属性には、次の値のいずれかに設定することができますが含まれています。  
  
1. "None"  
  
2. 「Allexceptintranet"」  
  
3. 「すべて」  
  
 IDN 設定が"None"に設定されている場合、Uri.Host または Uri.DnsSafeHost によって変換は実行されません。 IDN 設定を"All"、uri に設定するとします。ホストは、Unicode と uri に残ります。DnsSafeHost は Punycode に変換されます。 IDN 設定を"AllExceptIntranet"、uri を設定するとします。DnsSafeHost では、インターネット アドレスの Punycode に変換され、イントラネットのアドレスには Unicode のままです。 この設定は、正しい DNS 名解決にとって重要です。 Windows 8 以降のバージョンでは、この設定を構成する必要はありません。  
  
> [!WARNING]
>  Punycode を使用してアドレスをハードコーディングしないようにしてください。 アドレスは、適用した構成設定に基づき、WCF によって自動的に変換されます。  
  
> [!WARNING]
>  Unicode 文字を applicationHost.exe.config に追加する場合は、UTF-8 エンコードを使用してファイルを保存してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Uri?displayProperty=nameWithType>
