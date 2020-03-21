---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152464"
---
# <a name="wsfederation"></a>\<ws フェデレーション>
(WSFAM) の構成を<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>提供します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<サービス>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<フェデレーション構成>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws フェデレーション>**  
  
## <a name="syntax"></a>構文  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|authenticationType|認証の種類を指定する URI。 WS フェデレーション サインイン要求 wauth パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wauth パラメーターが要求に含まれていないことを指定します。|  
|鮮度|分単位の、希望する認証要求の最大期間。 WS-Federation サインインの要求 wfresh パラメーターを設定します。 省略可能。 既定値は 0 です。 省略可能。 **警告:** .NET Framework 4.5 の次のリリース`freshness`では、属性は型`xs:string`で、既定値は`null`です。|  
|ホームレルム|認証に使用する ID プロバイダー (IdP) のホーム 領域。 WS-Federation サインインの要求 whr パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、whr パラメータがリクエストに含まれていないことを指定します。|  
|発行者|目的のトークン発行者の URI。 WS フェデレーション サインイン要求とサインイン要求が必要な場合の基本 URL を設定します。|  
|永続的なクッキーオンパッシブリダイレクト|認証時に永続的な Cookie を発行するかどうかを指定します。 省略可能。 デフォルトは"false"で、クッキーは発行されません。|  
|パッシブリダイレクトが有効|承認されていない要求を STS に自動的にリダイレクトするために WSFAM を有効にするかどうかを指定します。 省略可能。 デフォルトは "true" で、不正なリクエストは自動的にリダイレクトされます。|  
|policy|サインイン要求で使用する関連ポリシーの場所を指定する URL。 既定値は空の文字列です。 WS-Federation サインインの要求 wp パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wp パラメーターが要求に含まれていないことを指定します。|  
|realm|要求元の領域の URI。 (セキュリティ トークン サービス (STS) への証明書利用者 (RP) を識別する URI。要求 wtrealm WS フェデレーション サインイン要求パラメーターを設定します。 必須。|  
|返信|証明書利用者 (RP) アプリケーションがセキュリティ トークン サービス (STS) から応答を受信することを希望しているアドレスを識別する URL。 WS フェデレーション サインイン要求 wreply パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wreply パラメーターが要求に含まれていないことを指定します。|  
|request|トークン発行要求。 WS-Federation サインインの要求 wreq パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wreq パラメーターが要求に含まれていないことを指定します。 要求に wreq パラメーターまたは wreqptr パラメーターを含めないことを意味する STS は、発行するトークンの種類を認識します。|  
|要求Ptr|トークン発行要求の場所を指定する URL 要求の wreqptr パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wreqptr パラメーターが要求に含まれていないことを指定します。 要求に wreq パラメーターまたは wreqptr パラメーターを含めないことを意味する STS は、発行するトークンの種類を認識します。|  
|必要なHttps|セキュリティ トークン サービス (STS) との通信で HTTPS プロトコルを使用する必要があるかどうかを指定します。 省略可能。 デフォルトは "true" で、HTTPS を使用する必要があります。|  
|resource|セキュリティ トークン サービスに対してアクセスされるリソース、証明書利用者 (RP) を識別する URI。 省略可能。 WS フェデレーション サインイン要求の wres パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、wres パラメーターが要求に含まれていないことを指定します。 **注:** wre はレガシー・パラメーターです。 代わりに`realm`wtrealm パラメーターを使用する属性を指定します。|  
|文字列にサインインします。|WS フェデレーション サインイン要求 URL でアプリケーション定義のクエリ パラメーターを指定する機能拡張ポイントを提供します。 省略可能。 デフォルトは空の文字列で、追加のパラメーターを要求に含めなさなくすることを指定します。 パラメータは、次の形式を使用してクエリ文字列フラグメントとして指定`"param1=value1&param2=value2&param3=value3"`されます。 **注:** 構成ファイルでは、クエリ文字列の "&" 文字は、`&`そのエンティティ参照を使用して指定する必要があります。|  
|文字列を指定します。|WS フェデレーション サインイン要求 URL でアプリケーション定義のクエリ パラメーターを指定する機能拡張ポイントを提供します。 省略可能。 デフォルトは空の文字列で、追加のパラメーターを要求に含めなさなくすることを指定します。 パラメータは、次の形式を使用してクエリ文字列フラグメントとして指定`"param1=value1&param2=value2&param3=value3"`されます。 **注:** 構成ファイルでは、クエリ文字列の "&" 文字は、`&`そのエンティティ参照を使用して指定する必要があります。|  
|返信のサインアウト|WS フェデレーション プロトコルを使用したパッシブサインアウト時に、クライアントがセキュリティ トークン サービス (STS) によってリダイレクトされる URL を指定します。 WS フェデレーションのサインアウト要求に対して wreply パラメーターを設定します。 省略可能。 デフォルトは空の文字列で、追加のパラメーターを要求に含めなさなくすることを指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<フェデレーション構成>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と (SAM) を<xref:System.IdentityModel.Services.SessionAuthenticationModule>構成する設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 この要素を`<wsFederation>`使用して、WSFAM の既定の WS フェデレーション パラメーター設定と既定の動作を構成できます。 要素セットの下で定義された`<wsFederation>`WS-Federation パラメーター設定は、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラスによって公開される同等のプロパティを設定します。 これらのプロパティは、WSFAM によって発行されるすべての要求で同じままです。 WSFAM によって公開されるイベントのイベント ハンドラーを追加することで、要求処理中に WS フェデレーション パラメーターを動的に変更できます。たとえば、イベント。 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> 詳細については、クラスのドキュメントを<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>参照してください。  
  
 要素`<wsFederation>`は<xref:System.IdentityModel.Services.Configuration.WSFederationElement>クラスによって表されます。 構成オブジェクト自体は<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>、クラスによって表されます。 プロパティを<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>介してアクセスされる<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトに対して単一の<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>インスタンスが設定され、WSFAM の構成が提供されます。  
  
## <a name="example"></a>例  
 次の XML`<wsFederation>`は、WSFAM の設定を指定する要素を示しています。  
  
> [!WARNING]
> この例では、HTTPS を使用するために WSFAM は必要ありません。 これは、要素の`requireHttps`属性が`<wsFederation>`設定`false`されているためです。 この設定は、セキュリティ上のリスクが生じる可能性があるため、ほとんどの運用環境では推奨されません。  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
