---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: eafaf253e27db632f17acfce4445a07d18b109aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778457"
---
# <a name="claimtyperequired"></a>\<claimTypeRequired>
必要な受信セキュリティ トークンのクレームのセットを指定します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimTypeRequired>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<claimType>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|受け取ったセキュリティ トークンの 1 つの省略可能または必須のクレームを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id の設定を指定します。|
