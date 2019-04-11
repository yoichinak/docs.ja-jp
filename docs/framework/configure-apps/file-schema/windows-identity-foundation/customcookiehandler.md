---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224050"
---
# <a name="customcookiehandler"></a>\<customCookieHandler>
カスタム クッキー ハンドラーの型を設定します。 この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素が"Custom"。 カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
\<customCookieHandler>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|種類|派生したカスタム型を指定します、<xref:System.IdentityModel.Services.CookieHandler>クラス。 詳細を指定する方法については、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>読み取りと書き込みの cookie を使用します。|  
  
## <a name="remarks"></a>Remarks  
 設定して、カスタム クッキー ハンドラーを指定する場合、`mode`の属性、`<cookieHandler>`要素"Custom"を含めることによって、カスタム クッキー ハンドラーの種類を指定する必要があります、`<customCookieHandler>`クッキー ハンドラーの型を参照する子要素。 この要素にすることはできないときに指定された、`mode`属性が"Chunked"または"Default"に設定します。 カスタム クッキー ハンドラーはから派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
 `<customCookieHandler>`要素が表される、<xref:System.IdentityModel.Configuration.CustomTypeElement>クラス。  
  
## <a name="example"></a>例  
 次の例では型のカスタム cookie ハンドラーを使用して SAM`MyNamespace.MyCustomCookieHandler`します。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.CookieHandler>
