---
title: <alwaysFlowImpersonationPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154484"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> 要素
偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<常にフロー偽装ポリシー>**\  
  
## <a name="syntax"></a>構文  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> Windows ID が非同期ポイントをまたいでフローするかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|Windows ID は、偽装がなどの<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>マネージ メソッドを通じて実行されない限り、非同期ポイントをまたいでフローしません。 これは既定値です。|  
|`true`|Windows ID は、偽装の実行方法に関係なく、常に非同期ポイント間でフローします。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 .NET Framework バージョン 1.0 および 1.1 では、Windows ID は非同期ポイントを渡ってフローしません。 .NET Framework Version 2.0 には、<xref:System.Threading.ExecutionContext>現在実行中のスレッドに関する情報を格納し、アプリケーション ドメイン内の非同期ポイントを渡ってその情報を格納するオブジェクトがあります。 また<xref:System.Security.Principal.WindowsIdentity>、ネイティブ メソッドへのプラットフォーム呼び出しなどの<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>他の方法ではなくマネージ メソッドを使用して偽装が実現された場合、非同期ポイントを流れる情報の一部としてもフローします。 この要素は、偽装の実行方法に関係なく、Windows ID が非同期ポイントを渡ってフローすることを指定するために使用されます。  
  
 このデフォルトの動作は、他の 2 つの方法で変更できます。  
  
1. スレッド単位でのマネージ コード。  
  
     <xref:System.Threading.ExecutionContext>の<xref:System.Security.SecurityContext>設定を変更して、スレッド単位でフローを<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>抑制できます。  
  
2. 共通言語ランタイム (CLR) を読み込むためのアンマネージ ホスト インターフェイスの呼び出しで。  
  
     CLR の読み込みに、単純なマネージ実行可能ファイルではなく、アンマネージ ホスト インターフェイスを使用する場合は[、CorBindToRuntimeEx 関数関数関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)の呼び出しで特別なフラグを指定できます。 プロセス全体の互換モードを有効にするには`flags`[、CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)のパラメーターを に`STARTUP_ALWAYSFLOW_IMPERSONATION`設定します。  
  
## <a name="configuration-file"></a>構成ファイル  
 .NET Framework アプリケーションでは、この要素はアプリケーション構成ファイルでのみ使用できます。  
  
 ASP.NET アプリケーションの場合、偽装フローは\<、Windows フォルダ>\Microsoft.NET\Framework\vx.x.xxxx ディレクトリにある aspnet.config ファイルで構成できます。  
  
 既定では、ASP.NET、次の構成設定を使用して aspnet.config ファイルの偽装フローを無効にします。  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NETでは、偽装のフローを許可する場合は、次の構成設定を明示的に使用する必要があります。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例は、マネージ メソッド以外の方法で偽装が実現された場合でも、Windows ID が非同期ポイントをまたいで流れるよう指定する方法を示しています。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [\<要素>偽装ポリシー](legacyimpersonationpolicy-element.md)
