---
title: <routing> の <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: b7a9be18395ef8878900d754b5aa5afdeee0cff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202509"
---
# <a name="routing-of-servicebehavior"></a>\<ルーティング > の\<serviceBehavior >
ルーティング構成の動的な変更を可能にするルーティング サービスへの実行時アクセスを提供します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<ルーティング >  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|filterTable|ルーティング サービスによって評価されるフィルターを含むルーティング テーブルの名前を指定する文字列。 この値に一致する必要があります、`name`の属性を[ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md)内の要素、 [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md)セクション。|  
|routeOnHeaderOnly|フィルターがメッセージの本文とヘッダーの両方を調べるか、ヘッダーのみを調べるかを指定するブール値。 既定値は `true` です。|  
|soapProcessingEnabled|SOAP 処理を実行するかどうかを指定するブール値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 サービスの動作構成に追加すると、この構成要素により、サービスのルーティングが有効になります。 この要素には、サービスで使用される実際のルーティング テーブルを指定できます。  
  
 この構成セクションを使用すると、配置パターンの変更時にルーティング設定を変更できます。 実行時には、新しいルーティング設定を使用した独自のルーティング拡張を登録できます。ルーティング サービスは (開始時に適用されていた規則に関係なく) 更新済みの構成情報を使用して新たなメッセージとセッションにサービスを提供します。ただし、インフライトのメッセージやセッションには以前の規則が適用されます。  このようにして、実行時において、セッション セーフでリサイクルの程度を抑えた状態でのルーティング サービスの再構成が可能となります。  
