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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec411039363cfb118fee06dff88daf50bbc97a86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314777"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy > 要素
偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。  
  
 \<configuration>  
\<runtime>  
\<alwaysFlowImpersonationPolicy>  
  
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
|`enabled`|必須の属性です。<br /><br /> Windows id が非同期ポイント間でフローするかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|管理されているメソッドをなどで、権限の借用を実行しない限り、id が、非同期ポイント間でフローしない Windows<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>します。 既定値です。|  
|`true`|Windows id は、偽装の実行方法に関係なく、非同期ポイント間で常にフローします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework バージョン 1.0 および 1.1 では、Windows id が非同期ポイント間をフローしません。 .NET Framework version 2.0 では、<xref:System.Threading.ExecutionContext>オブジェクトを現在実行中のスレッドに関する情報を含み、アプリケーション ドメイン内での非同期ポイント間でフローします。 <xref:System.Security.Principal.WindowsIdentity>またメソッドの管理を使用して、権限の借用が行われた指定された、非同期ポイント間をフロー情報の一部としてフローなど<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>platform などの他の方法ではなくネイティブ メソッドを呼び出すとします。 この要素を使用して、Windows id は、権限借用の実現方法に関係なく、非同期ポイント間でフローことを指定します。  
  
 他の 2 つの方法でこの既定の動作を変更することができます。  
  
1. スレッドごとにマネージ コードは。  
  
     スレッドごとのフローを抑制するには変更することによって、<xref:System.Threading.ExecutionContext>と<xref:System.Security.SecurityContext>設定を使用して、 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>、または<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>メソッド。  
  
2. で、共通言語ランタイム (CLR) を読み込むアンマネージ ホスト インターフェイスへの呼び出し。  
  
     呼び出しで特別なフラグを指定するには、CLR を読み込めません (単純なマネージ実行可能ファイル) ではなく、アンマネージ ホスト インターフェイスを使用する場合、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数。 プロセス全体の互換モードを有効にするには設定、`flags`パラメーター [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)に`STARTUP_ALWAYSFLOW_IMPERSONATION`します。  
  
## <a name="configuration-file"></a>構成ファイル  
 .NET Framework アプリケーションでは、この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
 見つかった aspnet.config ファイルで、ASP.NET アプリケーションの権限借用のフローを構成できます、 \<Windows フォルダー > \Microsoft.NET\Framework\vx.x.xxxx ディレクトリ。  
  
 既定では ASP.NET では、次の構成設定を使用して、aspnet.config ファイルで権限借用のフローを無効にします。  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET では、代わりに、権限借用のフローを許可する場合は、する必要があります明示的に使用する次の構成設定。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例では、Windows id を権限の借用は、マネージ メソッド以外の方法によって実現している場合でも、非同期ポイント間でフローするかを指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<legacyImpersonationPolicy > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
