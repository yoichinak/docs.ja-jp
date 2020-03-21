---
title: <appDomainResourceMonitoring> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154377"
---
# <a name="appdomainresourcemonitoring-element"></a>\<要素>リソースの監視
プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>の監視**  
  
## <a name="syntax"></a>構文  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがアプリケーション ドメインリソース監視の統計を収集するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|Value|説明|  
|-----------|-----------------|  
|`true`|アプリケーション ドメインリソース監視の統計が収集されます。|  
|`false`|アプリケーション ドメインリソースの監視の統計は収集されません。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  
 アプリケーション ドメイン リソースの監視は、マネージ アプリケーション ドメイン クラス、ホストする[ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)インターフェイス、および Windows のイベント トレース (ETW) を通じて使用できます。 監視が有効な場合、プロセスの有効期間中に、プロセス内のすべてのアプリケーション ドメインに関する統計が収集されます。  
  
 マネージ コードからの監視を有効にするには、<xref:System.AppDomain.MonitoringIsEnabled%2A>プロパティを使用します。  
  
 この構成要素は、.NET Framework 4 以降でのみ使用できます。  
  
## <a name="example"></a>例  
 アプリケーション ドメインのリソース監視を有効にする方法を次の例に示します。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
