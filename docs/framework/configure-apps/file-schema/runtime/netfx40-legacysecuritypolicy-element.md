---
title: <NetFx40_LegacySecurityPolicy> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a0ca8560fcd5d7f9d171df3e3b4c3f42e78641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674182"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy > 要素
ランタイムがレガシ コード アクセス セキュリティ (CAS) ポリシーを使用するかどうかを指定します。  
  
 \<configuration>  
\<runtime>  
< NetFx40_LegacySecurityPolicy >  
  
## <a name="syntax"></a>構文  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがレガシ CAS ポリシーを使用するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムは、従来の CAS ポリシーを使用しません。 既定値です。|  
|`true`|ランタイムは、従来の CAS ポリシーを使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework version 3.5 以前のバージョンで、CAS ポリシーは常に影響します。 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、CAS ポリシーを有効にする必要があります。  
  
 CAS ポリシーは、バージョン固有です。 .NET Framework の以前のバージョンに存在するカスタムの CAS ポリシーを再度指定する必要があります、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]します。  
  
 適用する、`<NetFx40_LegacySecurityPolicy>`要素を[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]アセンブリには影響しません[セキュリティ透過的なコード](../../../../../docs/framework/misc/security-transparent-code.md); 透過性規則が適用されます。  
  
> [!IMPORTANT]
>  適用、`<NetFx40_LegacySecurityPolicy>`要素により、大幅なパフォーマンスの低下によって作成されたネイティブ イメージ アセンブリ、[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md)でインストールされていない、[グローバル アセンブリ キャッシュ](../../../../../docs/framework/app-domains/gac.md). パフォーマンスの低下は、ランタイム属性が適用されるときに、ネイティブ イメージとして、アセンブリを読み込むことができないによる、として、just-in-time でアセンブリが読み込まれる結果的にします。  
  
> [!NOTE]
>  ターゲット .NET Framework のバージョンよりも前に指定するかどうか、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] Visual Studio プロジェクトのプロジェクト設定、CAS ポリシーが有効にする、そのバージョンの指定した任意のカスタムの CAS ポリシーを含むです。 New を使用できなくが、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]型とメンバー。 使用して、.NET Framework の以前のバージョンを指定することも、 [ \<supportedRuntime > 要素](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)でスタートアップ設定スキーマで、[アプリケーション構成ファイル](../../../../../docs/framework/configure-apps/index.md)します。  
  
> [!NOTE]
>  構成ファイルの構文は、大文字小文字を区別します。 構文と例のセクションで指定された構文を使用する必要があります。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例では、アプリケーションの従来の CAS ポリシーを有効にする方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
