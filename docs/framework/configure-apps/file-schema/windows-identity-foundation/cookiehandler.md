---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 5238ea7b96c09fb976a25bc00b952539ddd44b49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115155"
---
# <a name="cookiehandler"></a>\<cookieHandler>
構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) を使用して cookie を読み書きします。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<cookieHandler>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|書き込むクッキーの基本名を指定します。 既定では"FedAuth です"。|  
|path|書き込むクッキーのパスの値を指定します。 既定では"HttpRuntime.AppDomainAppVirtualPath です"。|  
|モード|1 つ、 <xref:System.IdentityModel.Services.CookieHandlerMode> SAM で使用されるクッキー ハンドラーの種類を指定する値。 次の値を使用できます。<br /><br /> -"Default"、"Chunked"と同じです。<br />-「チャンク」などのインスタンスを使用して、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス。 このクッキー ハンドラーにより、個々 の cookie は、セットの最大サイズを超えていないこと。 これを行う、変数を複数の cookie でネットワークに 1 つの論理 cookie を可能性のある「チャンク」。<br />-「カスタム」— から派生したカスタム クラスのインスタンスを使用して<xref:System.IdentityModel.Services.CookieHandler>します。 派生クラスは、によって参照される、`<customCookieHandler>`子要素。<br /><br /> 既定値は、"Default"です。|  
|persistentSessionLifetime|永続的なセッションの有効期間を指定します。 0 の場合、一時的なセッションは常に使用します。 既定値は、「0:0:0」は、一時的なセッションを指定します。 最大値は、「365:0:0」は、365 日間のセッションを指定します。 次の制限に従って、値を指定する必要があります:`<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`左端の値が日数を指定します、中央値 (ある場合) が、時間を指定します、右端の値 (存在する) 場合は、分を指定します。|  
|RequireSsl|書き込むクッキーの「セキュリティで保護された」フラグが出力されるかどうかを指定します。 この値が設定されている場合、サインイン セッション cookie はできるだけ HTTPS 経由でです。 既定値は "true" です。|  
|hideFromScript|書き込まれた cookie に対して「httponly が設定された」フラグが出力されるかどうかを制御します。 一部の web ブラウザーでは、cookie の値へのアクセスをクライアント側スクリプトを保持することでこのフラグを優先します。 既定値は "true" です。|  
|ドメイン|書き込むクッキーのドメインの値。 既定値は "" です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|構成、<xref:System.IdentityModel.Services.ChunkedCookieHandler>します。 この要素は存在のみ可能な場合、`mode`の属性、`<cookieHandler>`要素が"Default"または「チャンク」。|  
|[\<customCookieHandler>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|カスタム クッキー ハンドラーの型を設定します。 この要素が存在する必要がある場合、`mode`の属性、`<cookieHandler>`要素が"Custom"。 その他の値のために存在することはできません、`mode`属性。 カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラス。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>Remarks  
 <xref:System.IdentityModel.Services.CookieHandler>はプロトコル レベルの読み取りと書き込みの生の cookie、http に対して責任をします。 いずれかを構成することができます、<xref:System.IdentityModel.Services.ChunkedCookieHandler>またはから派生したカスタム cookie ハンドラーを<xref:System.IdentityModel.Services.CookieHandler>クラス。  
  
 チャンクされたクッキー ハンドラーを構成するには、"Chunked"または"Default"にモード属性を設定します。 既定のチャンク サイズは 2000 (バイト単位) ですが、必要に応じてを含めることによって、さまざまなチャンク サイズを指定することがあります、`<chunkedCookieHandler>`子要素。  
  
 カスタム クッキー ハンドラーを構成するには、"Custom"にモード属性を設定します。 指定する必要があります、`<customCookieHandler>`カスタム ハンドラーの型を参照する子要素。  
  
 `<cookieHandler>`要素が表される、<xref:System.IdentityModel.Services.CookieHandlerElement>クラス。 構成で指定されたクッキー ハンドラーは、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>のプロパティ、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトのセット、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティ。  
  
## <a name="example"></a>例  
 次の XML に示す、`<cookieHandler>`要素。 この例では、ため、`mode`属性が指定されていない、既定のクッキー ハンドラーは、SAM で使用されます。 これは、インスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス。 `<chunkedCookieHandler>`子要素が指定されていない、既定のチャンク サイズが使用されます。 HTTPS は必要ありませんので、`requireSsl`属性が設定されて`false`します。  
  
> [!WARNING]
>  HTTPS は、この例で、セッション クッキーを記述する必要はありません。 これは、ため、`requireSsl`属性を`<cookieHandler>`要素に設定されて`false`します。 ほとんどの運用環境には、セキュリティ リスクがあると、この設定はお勧めできません。  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
