---
title: <legacyImpersonationPolicy> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c39ee551dde19d87a75403f3db7433d1ef829f3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333991"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy > 要素
Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。  
  
 \<configuration>  
\<runtime>  
\<legacyImpersonationPolicy>  
  
## <a name="syntax"></a>構文  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 指定します、<xref:System.Security.Principal.WindowsIdentity>が非同期ポイント間をフローしないに関係なく、<xref:System.Threading.ExecutionContext>フローの現在のスレッドで設定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> に応じて非同期ポイント間のフロー、<xref:System.Threading.ExecutionContext>フロー、現在のスレッドを設定します。 既定値です。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> 非同期ポイント間をフローしないに関係なく、<xref:System.Threading.ExecutionContext>フローの現在のスレッドで設定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework バージョン 1.0 および 1.1 で、<xref:System.Security.Principal.WindowsIdentity>任意のユーザー定義の非同期ポイント間をフローしません。 以降、.NET Framework version 2.0 では、ある、<xref:System.Threading.ExecutionContext>と現在実行中のスレッドに関する情報を含むオブジェクトがアプリケーション ドメイン内での非同期ポイント間でフローします。 <xref:System.Security.Principal.WindowsIdentity>この実行コンテキストが用意されており、したがってもポイント間をフロー、非同期、つまり、権限借用コンテキストが存在する場合、これがフローするもします。  
  
 以降、.NET Framework 2.0 を使えば、`<legacyImpersonationPolicy>`ことを指定する要素<xref:System.Security.Principal.WindowsIdentity>非同期ポイント間をフローしません。  
  
> [!NOTE]
>  共通言語ランタイム (CLR) は、プラットフォームを通じてなど、マネージ コードの外部で実行する権限借用のではありませんのマネージ コードを使用して実行される操作は、アンマネージ コードに、または Win32 関数への直接の呼び出しを呼び出す権限借用に注意してください。 マネージのみ<xref:System.Security.Principal.WindowsIdentity>しない限り、非同期ポイント間でオブジェクトが流れることができる、`alwaysFlowImpersonationPolicy`要素が設定されているを true に (`<alwaysFlowImpersonationPolicy enabled="true"/>`)。 設定、 `alwaysFlowImpersonationPolicy` true 要素では、Windows id が偽装の実行方法に関係なく、非同期ポイント間で常にフローを指定します。 詳細についてはフローの情報では、権限借用をアンマネージ非同期ポイント間を参照してください[ \<alwaysFlowImpersonationPolicy > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)します。  
  
 他の 2 つの方法でこの既定の動作を変更することができます。  
  
1. スレッドごとにマネージ コードは。  
  
     スレッドごとのフローを抑制するには変更することによって、<xref:System.Threading.ExecutionContext>と<xref:System.Security.SecurityContext>設定を使用して、 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>、<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>または<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>メソッド。  
  
2. で、共通言語ランタイム (CLR) を読み込むアンマネージ ホスト インターフェイスへの呼び出し。  
  
     呼び出しで特別なフラグを指定するには、CLR を読み込めません (単純なマネージ実行可能ファイル) ではなく、アンマネージ ホスト インターフェイスを使用する場合、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数。 プロセス全体の互換モードを有効にするには設定、`flags`パラメーター [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)STARTUP_LEGACY_IMPERSONATION にします。  
  
 詳細については、次を参照してください。、 [ \<alwaysFlowImpersonationPolicy > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)します。  
  
## <a name="configuration-file"></a>構成ファイル  
 .NET Framework アプリケーションでは、この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
 見つかった aspnet.config ファイルで、ASP.NET アプリケーションの権限借用のフローを構成できます、 \<Windows フォルダー > \Microsoft.NET\Framework\vx.x.xxxx ディレクトリ。  
  
 既定では ASP.NET では、次の構成設定を使用して、aspnet.config ファイルで権限借用のフローを無効にします。  
  
``` xml
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
 次の例では、非同期ポイント間、Windows id をフローしない従来の動作を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<alwaysFlowImpersonationPolicy > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
