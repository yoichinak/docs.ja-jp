---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944075"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache>
トークン再生キャッシュをサービスまたはセキュリティトークンハンドラーコレクションに登録します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<キャッシュ >  
\<tokenReplayCache>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|<xref:System.IdentityModel.Tokens.TokenReplayCache>クラスから派生する型。 カスタム`type`を指定する方法の詳細については、「[カスタム型参照]」を参照してください。
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<キャッシュ >](caches.md)|サービスまたはセキュリティトークンハンドラーコレクションによって使用されるキャッシュを登録します。|  
  
## <a name="remarks"></a>Remarks  
 トークン再生キャッシュは、再生されたトークンを検出するために使用されます。 トークンリプレイ検出は、トークンの最大有効期間を指定する[ \<tokenreplaydetection >](tokenreplaydetection.md)要素によって有効にされます。  
  
## <a name="example"></a>例  
 次の XML は、再生されたトークンを検出するためのカスタムキャッシュの構成を示しています。  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
