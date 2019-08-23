---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942792"
---
# <a name="customcookiehandler"></a>\<customCookieHandler >
カスタムクッキーハンドラーの種類を設定します。 この要素は、 `mode` `<cookieHandler>`要素の属性が "Custom" の場合にのみ存在する可能性があります。 カスタム型は、 <xref:System.IdentityModel.Services.CookieHandler>クラスから派生する必要があります。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler >  
\<customCookieHandler >  
  
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
|型|<xref:System.IdentityModel.Services.CookieHandler>クラスから派生するカスタム型を指定します。 `type`属性を指定する方法の詳細については、「[カスタム型参照](../windows-workflow-foundation/index.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> が<xref:System.IdentityModel.Services.SessionAuthenticationModule> cookie の読み取りと書き込みに使用するを構成します。|  
  
## <a name="remarks"></a>Remarks  
 要素の属性を "custom" に設定`<customCookieHandler>`してカスタム cookie ハンドラーを指定する場合は、クッキーハンドラーの型を参照する子要素を含めることによって、カスタム cookie ハンドラーの型を指定する必要があります。 `mode` `<cookieHandler>` 属性が "Chunked" または`mode` "Default" に設定されている場合、この要素を指定することはできません。 カスタムクッキーハンドラーは、 <xref:System.IdentityModel.Services.CookieHandler>クラスから派生する必要があります。  
  
 要素は、 <xref:System.IdentityModel.Configuration.CustomTypeElement>クラスによって表されます。 `<customCookieHandler>`  
  
## <a name="example"></a>例  
 次の例では、型`MyNamespace.MyCustomCookieHandler`のカスタム cookie ハンドラーを使用するように SAM を構成します。  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.CookieHandler>
