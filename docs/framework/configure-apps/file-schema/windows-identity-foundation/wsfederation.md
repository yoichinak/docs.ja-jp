---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 801970ec05fc88587a5b45b5bb3a855d1a81afb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356092"
---
# <a name="wsfederation"></a>\<wsFederation >
構成を提供、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM)。  
  
\<system.identityModel.services>  
\<federationConfiguration>  
\<wsFederation >  
  
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
|authenticationType|認証の種類を指定する URI。 Ws-federation サインイン要求の wauth パラメーターを設定します。 任意。 既定では、要求の wauth パラメーターが含まれていないことを指定します。 空の文字列です。|  
|鮮度|必要な最大有効期間、認証要求の分単位で。 Ws-federation サインイン要求 wfresh パラメーターを設定します。 任意。 既定値は 0 です。 任意。 **警告:**.NET Framework 4.5 では、次のリリースで、`freshness`属性の型がで`xs:string`その既定値になります`null`します。|  
|homeRealm|認証に使用する id プロバイダー (IP) のホーム領域。 Ws-federation サインイン要求 whr パラメーターを設定します。 任意。 既定では空の文字列、whr パラメーターが要求に含まれていないことを指定します。|  
|issuer|目的のトークン発行者の URI。 ベース URL の Ws-federation サインイン要求とサインアウト要求のために必要な設定します。|  
|persistentCookiesOnPassiveRedirects|認証で永続的な cookie が発行されるかどうかを指定します。 任意。 既定値は"false"は、クッキーは発行されません。|  
|passiveRedirectEnabled|自動的に承認されていない要求を STS にリダイレクトするため、WSFAM が有効になっているかどうかを指定します。 任意。 既定値は"true"、未承認の要求が自動的にリダイレクトされます。|  
|ポリシー|サインイン要求で使用する関連ポリシーの場所を指定する URL。 既定値は空の文字列です。 Ws-federation サインイン要求 wp パラメーターを設定します。 任意。 既定では空の文字列、wp パラメーターが要求に含まれていないことを指定します。|  
|realm|要求レルムの URI。 (を識別する URI、証明書利用者 (RP) セキュリティ トークン サービス (STS)。)要求 wtrealm Ws-federation サインイン要求のパラメーターを設定します。 必須。|  
|応答|これで、証明書利用者 (RP) アプリケーションのセキュリティ トークン サービス (STS) からの応答を受信するようはアドレスを識別する URL。 Ws-federation サインイン要求で wreply パラメーターを設定します。 任意。 既定では、要求で wreply パラメーターが含まれていないことを指定します。 空の文字列です。|  
|要求|トークン発行要求。 Ws-federation サインイン要求 wreq パラメーターを設定します。 任意。 既定では空の文字列、wreq パラメーターが要求に含まれていないことを指定します。 要求に含めない、wreq パラメーターまたは wreqptr パラメーターは、STS が発行するトークンの種類を知っていることを意味します。|  
|requestPtr|トークン発行要求の場所を指定する URL。 要求 wreqptr パラメーターを設定します。 任意。 既定では空の文字列、wreqptr パラメーターが要求に含まれていないことを指定します。 要求に含めない、wreq パラメーターまたは wreqptr パラメーターは、STS が発行するトークンの種類を知っていることを意味します。|  
|requireHttps|セキュリティ トークン サービス (STS) との通信が HTTPS プロトコルを使用する必要があるかどうかを指定します。 任意。 既定値が"true"には、HTTPS を使用する必要があります。|  
|リソース|アクセスされるリソース (RP) 証明書利用者を識別する URI、セキュリティ トークン サービス (STS)。 任意。 Ws-federation サインイン要求 wres パラメーターを設定します。 任意。 既定では空の文字列、wres パラメーターが要求に含まれていないことを指定します。 **注:** wres はレガシ パラメーターです。 指定、 `realm` wtrealm パラメーターを代わりに使用する属性。|  
|signInQueryString|Ws-federation サインイン要求 URL で定義されているアプリケーションのクエリ パラメーターを指定する機能拡張ポイントを提供します。 任意。 既定では、要求に追加のパラメーターを含めるないかを指定します。 空の文字列です。 パラメーターは、次の形式を使用してクエリ文字列のフラグメントとして指定されます。 `"param1=value1&param2=value2&param3=value3"` 、という具合です。 **注:** 構成ファイルで、' (& a)"のエンティティ参照を使用してクエリ文字列内の文字を指定する必要があります`&`します。|  
|signOutQueryString|Ws-federation サインイン要求 URL で定義されているアプリケーションのクエリ パラメーターを指定する機能拡張ポイントを提供します。 任意。 既定では、要求に追加のパラメーターを含めるないかを指定します。 空の文字列です。 パラメーターは、次の形式を使用してクエリ文字列のフラグメントとして指定されます。 `"param1=value1&param2=value2&param3=value3"` 、という具合です。 **注:** 構成ファイルで、' (& a)"のエンティティ参照を使用してクエリ文字列内の文字を指定する必要があります`&`します。|  
|signOutReply|Ws-federation プロトコルによるパッシブ サインアウト時にセキュリティ トークン サービス (STS) によって、クライアントをリダイレクトする URL を指定します。 Ws-federation サインアウト要求で wreply パラメーターを設定します。 任意。 既定では、要求に追加のパラメーターを含めるないかを指定します。 空の文字列です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) と<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>Remarks  
 使用することができます、 `<wsFederation>` WSFAM の Ws-federation パラメーターの既定の設定と既定の動作を構成する要素。 下で定義された Ws-federation パラメーターの設定、`<wsFederation>`要素によって公開されている同等のプロパティの設定、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラス。 これらのプロパティでは、WSFAM によって発行されたすべての要求に対して同じままです。 要求; WSFAM によって公開されるイベントのイベント ハンドラーを追加することで処理中に、Ws-federation パラメーターを動的に変更することができます。たとえば、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>イベント。 詳細については、ドキュメントを参照して、<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラス。  
  
 `<wsFederation>`要素が表される、<xref:System.IdentityModel.Services.Configuration.WSFederationElement>クラス。 構成オブジェクト自体がによって表される、<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>クラス。 1 つ<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>インスタンスが設定されて、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>経由でアクセスするオブジェクト、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティ WSFAM の構成を提供するとします。  
  
## <a name="example"></a>例  
 次の XML に示す、`<wsFederation>`要素 WSFAM の設定を指定します。  
  
> [!WARNING]
>  この例で、WSFAM は HTTPS を使用する必要はありません。 これは、ため、`requireHttps`属性を`<wsFederation>`要素が設定されて`false`します。 ほとんどの運用環境には、セキュリティ リスクがあると、この設定はお勧めできません。  
  
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
