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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154105"
---
# <a name="legacyimpersonationpolicy-element"></a>\<要素>偽装ポリシー
Windows ID が、現在のスレッドの実行コンテキストのフロー設定に関係なく、非同期ポイント間でフローしないことを指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<レガシズマシポリシー>**  
  
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
|`enabled`|必須の属性です。<br /><br /> 現在のスレッド<xref:System.Security.Principal.WindowsIdentity>のフロー設定に関係なく、非同期ポイント間<xref:System.Threading.ExecutionContext>でのフローを行わないことを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|Value|説明|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>現在のスレッドのフロー設定に<xref:System.Threading.ExecutionContext>応じて、非同期ポイント間でフローします。 これは既定値です。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>は、現在のスレッドのフロー設定に<xref:System.Threading.ExecutionContext>関係なく、非同期ポイント間でフローしません。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 NET Framework バージョン 1.0 および 1.1<xref:System.Security.Principal.WindowsIdentity>では、 はユーザー定義の非同期ポイントを経由しません。 .NET Framework Version 2.0 以降では、<xref:System.Threading.ExecutionContext>現在実行中のスレッドに関する情報を格納するオブジェクトがあり、アプリケーション ドメイン内の非同期ポイント間でフローします。 <xref:System.Security.Principal.WindowsIdentity>この実行コンテキストに含まれるので、非同期ポイントをまた流れ、偽装コンテキストが存在する場合にもフローします。  
  
 NET Framework 2.0 以降では、要素を`<legacyImpersonationPolicy>`使用して、非同期ポイント<xref:System.Security.Principal.WindowsIdentity>を渡って流れないことを指定できます。  
  
> [!NOTE]
> 共通言語ランタイム (CLR) は、マネージ コードの外部で実行される偽装操作 (プラットフォーム呼び出しからアンマネージ コードへの呼び出し、Win32 関数への直接呼び出しなど) ではなく、マネージ コードのみを使用して実行される偽装操作を認識します。 要素が<xref:System.Security.Principal.WindowsIdentity>true ( )`<alwaysFlowImpersonationPolicy enabled="true"/>`に設定`alwaysFlowImpersonationPolicy`されていない限り、非同期ポイントをまたいで流すことができるのはマネージ オブジェクトだけです。 要素を`alwaysFlowImpersonationPolicy`true に設定すると、偽装の実行方法に関係なく、Windows ID が常に非同期ポイントをまたいでフローするように指定されます。 非同期ポイント間でアンマネージ偽装をフローする方法の詳細については[\<、「alwaysFlowImpersonationPolicy>要素](alwaysflowimpersonationpolicy-element.md)」を参照してください。  
  
 このデフォルトの動作は、他の 2 つの方法で変更できます。  
  
1. スレッド単位でのマネージ コード。  
  
     または<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>メソッドを使用して<xref:System.Threading.ExecutionContext>および の設定を変更することで、<xref:System.Security.SecurityContext>スレッド単位でフローを<xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType><xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>抑制できます。  
  
2. 共通言語ランタイム (CLR) を読み込むためのアンマネージ ホスト インターフェイスの呼び出しで。  
  
     CLR の読み込みに、単純なマネージ実行可能ファイルではなく、アンマネージ ホスト インターフェイスを使用する場合は[、CorBindToRuntimeEx 関数関数関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)の呼び出しで特別なフラグを指定できます。 プロセス全体の互換モードを有効にするには`flags`[、CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)のパラメーターをSTARTUP_LEGACY_IMPERSONATIONに設定します。  
  
 詳細については、「[\<常にフロー偽装ポリシー>要素](alwaysflowimpersonationpolicy-element.md)」を参照してください。  
  
## <a name="configuration-file"></a>構成ファイル  
 .NET Framework アプリケーションでは、この要素はアプリケーション構成ファイルでのみ使用できます。  
  
 ASP.NET アプリケーションの場合、偽装フローは\<、Windows フォルダ>\Microsoft.NET\Framework\vx.x.xxxx ディレクトリにある aspnet.config ファイルで構成できます。  
  
 既定では、ASP.NET、次の構成設定を使用して aspnet.config ファイルの偽装フローを無効にします。  
  
``` xml
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
 次の例は、非同期ポイント間で Windows ID をフローしない従来の動作を指定する方法を示しています。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [\<常にフロー偽装ポリシー>要素](alwaysflowimpersonationpolicy-element.md)
