---
title: <relativeBindForResources> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153907"
---
# <a name="relativebindforresources-element"></a>\<相対バインドフォーリソース>要素
サテライト アセンブリのプローブを最適化します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<リソース>を相対的に設定します。**  
  
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
  
|Value|説明|  
|-----------|-----------------|  
|`false`|ランタイムは、サテライト アセンブリのプローブを最適化しません。 これが既定値です。|  
|`true`|ランタイムは、サテライト アセンブリのプローブを最適化します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>解説  
 一般に、リソース マネージャーは、「リソースの[パッケージ化とデプロイ](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)」トピックで説明されているように、リソースを調査します。 つまり、リソース マネージャーは、リソースの特定のローカライズされたバージョンを調査するときに、グローバル アセンブリ キャッシュを検索し、アプリケーションのコード ベースでカルチャ固有のフォルダーを検索し、サテライト アセンブリの Windows インストーラーを<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>照会し、イベントを発生させる可能性があります。 この`<relativeBindForResources>`要素は、リソース マネージャーがサテライト アセンブリを調査する方法を最適化します。 次の条件下でリソースを調査する場合、パフォーマンスが向上します。  
  
- サテライト アセンブリがコード アセンブリと同じ場所に配置される場合。 つまり、コード アセンブリがグローバル アセンブリ キャッシュにインストールされている場合は、サテライト アセンブリもそこにインストールする必要があります。 コード アセンブリがアプリケーションのコード ベースにインストールされている場合、サテライト アセンブリはコード ベースのカルチャ固有のフォルダーにもインストールする必要があります。  
  
- Windows インストーラが使用されていない場合、またはサテライト アセンブリのオンデマンド インストールに使用されることはほとんどありません。  
  
- アプリケーション コードがイベントを<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>処理しない場合。  
  
 次のように`enabled`、サテライト`true`アセンブリのリソース マネージャーのプローブを最適化する要素の属性を設定します。 `<relativeBindForResources>`  
  
- このサービスは、親コード アセンブリの場所を使用して、サテライト アセンブリをプローブします。  
  
- Windows インストーラによるサテライト アセンブリのクエリは行われません。  
  
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベントは発生しません。  
  
## <a name="see-also"></a>関連項目

- [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
