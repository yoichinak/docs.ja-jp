---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252105"
---
# <a name="chunkedcookiehandler"></a>\<chunkedCookieHandler>
を<xref:System.IdentityModel.Services.ChunkedCookieHandler>構成します。 この要素は、 `mode` `<cookieHandler>`要素の属性が "Default" または "Chunked" の場合にのみ存在する可能性があります。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> のシステム**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|chunkSize|1つの HTTP クッキーの HTTP クッキーデータの最大サイズ (文字数)。 チャンクサイズを調整する場合は注意が必要です。 Web ブラウザーでは、cookie のサイズとドメインごとに許可される数の制限が異なります。 たとえば、Netscape の元の仕様では、次の制限が規定されています。300クッキーの合計、cookie ヘッダーあたりの4096バイト (cookie 値だけでなく、メタデータを含む)、ドメインごとに20の cookie。 既定値は2000です。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](cookiehandler.md)|(SAM) が<xref:System.IdentityModel.Services.SessionAuthenticationModule> cookie の読み取りと書き込みに使用するを構成します。<xref:System.IdentityModel.Services.CookieHandler>|  
  
## <a name="remarks"></a>Remarks  
 要素の<xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode`属性を "Default" または "Chunked" に設定してを指定した場合、 `<chunkedCookieHandler>`子要素を含めることによって cookie ハンドラーが cookie の読み取りと書き込みに使用するチャンクサイズを指定できます。 `<cookieHandler>``chunkSize`属性を設定しています。 `<chunkedCookieHandler>`要素が存在しない場合は、既定のチャンクサイズである2000バイトが使用されます。 属性が "Custom" に設定`mode`されている場合、この要素を指定することはできません。  
  
 要素は、 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>クラスによって表されます。 `<chunkedCookieHandler>`  
  
## <a name="example"></a>例  
 次の例では、3000バイトのチャンク単位でクッキーを書き込むチャンク cookie ハンドラーを構成します。  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
