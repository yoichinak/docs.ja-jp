---
title: <relativeBindForResources> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15156eaf883fc9ec162e0a85525564d49522b01d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592669"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> 要素
サテライト アセンブリのプローブを最適化します。  
  
 \<configuration> 要素  
\<runtime> 要素  
\<relativeBindForResources> 要素  
  
## <a name="syntax"></a>構文  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 共通言語ランタイムがサテライト アセンブリのプローブを最適化するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムでは、サテライト アセンブリのプローブは最適化されません。 これが既定値です。|  
|`true`|ランタイムは、サテライト アセンブリのプローブを最適化します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>Remarks  
 記載されているのリソースについては、Resource Manager が一般に、プローブ、 [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)トピック。 つまり、リソース マネージャーは、リソースの特定のローカライズされたバージョンのプローブ、ときに、可能性があります、グローバル アセンブリ キャッシュ ファイルの場所、カルチャ固有のフォルダー、アプリケーションのコード ベース、クエリ Windows インストーラーでサテライト アセンブリでは、検索対象を発生させる、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。 `<relativeBindForResources>`要素は、Resource Manager がサテライト アセンブリをプローブする方法を最適化します。 次の条件下でリソースのプローブは、パフォーマンスを向上させることできます。  
  
- ときに、サテライト アセンブリは、コード アセンブリと同じ場所にデプロイされます。 つまり、コード アセンブリがグローバル アセンブリ キャッシュにインストールする場合、サテライト アセンブリもインストールしなければなりませんがあります。 コード アセンブリは、アプリケーションのコード ベースでインストールする場合、コード ベースのカルチャ固有のフォルダーにもこのサテライト アセンブリをインストールする必要があります。  
  
- Windows インストーラーが実行されていないまたはほとんど使用されないサテライト アセンブリのオンデマンドでインストールします。  
  
- アプリケーション コードが処理しない場合、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。  
  
 設定、`enabled`の属性、`<relativeBindForResources>`要素を`true`サテライト アセンブリの次のように Resource Manager のプローブを最適化します。  
  
- 親コード アセンブリの場所を使って、サテライト アセンブリをプローブします。  
  
- Windows インストーラーをサテライト アセンブリに照会しません。  
  
- 発生させない、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。  
  
## <a name="see-also"></a>関連項目

- [リソースのパッケージ化と配置](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
