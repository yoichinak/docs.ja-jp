---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 57a1513f6de7f7bd9ea441b6cbc3db6a06d76fc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940262"
---
# <a name="wsfederation"></a>\<wsFederation >
<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfam) の構成を提供します。  
  
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
|authenticationType|認証の種類を指定する URI。 WS-FEDERATION サインイン要求 wauth パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wauth パラメーターが要求に含まれないことを指定します。|  
|鮮度|認証要求の最大有効期間 (分単位)。 WS-FEDERATION サインイン要求の wfresh パラメーターを設定します。 任意。 既定値は 0 です。 任意。 **警告:** .NET Framework 4.5 `freshness`の次のリリースでは、属性は型`xs:string`になり、 `null`その既定値はになります。|  
|homeRealm|認証に使用する id プロバイダー (IdP) のホーム領域。 WS-FEDERATION サインイン要求 whr パラメーターを設定します。 任意。 既定値は空の文字列です。これは、whr パラメーターが要求に含まれないことを指定します。|  
|issuer|目的のトークン発行者の URI。 WS-FEDERATION サインイン要求とサインアウト要求のベース URL を設定します。|  
|persistentCookiesOnPassiveRedirects|認証時に永続的な cookie を発行するかどうかを指定します。 任意。 既定値は "false" です。 cookie は発行されません。|  
|無効化 Veredirectenabled|承認されていない要求を STS に自動的にリダイレクトするために WSFAM が有効かどうかを指定します。 任意。 既定値は "true" で、承認されていない要求は自動的にリダイレクトされます。|  
|ポリシー|サインイン要求で使用する関連ポリシーの場所を指定する URL。 既定値は空の文字列です。 WS-FEDERATION サインイン要求 wp パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wp パラメーターが要求に含まれないことを指定します。|  
|realm|要求している領域の URI。 (STS (Security Token Service) に証明書利用者 (RP) を識別する URI。要求 wtrealm WS-FEDERATION サインイン要求パラメーターを設定します。 必須。|  
|reply|証明書利用者 (RP) アプリケーションがセキュリティトークンサービス (STS) からの応答を受信するアドレスを識別する URL。 WS-FEDERATION サインイン要求の wreply パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wreply パラメーターが要求に含まれないことを指定します。|  
|要求|トークン発行要求。 WS-FEDERATION サインイン要求 wreq パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wreq パラメーターが要求に含まれないことを指定します。 要求に wreq または wreqptr パラメーターを含めないことは、発行するトークンの種類を STS が認識していることを意味します。|  
|requestPtr|トークン発行要求の場所を指定する URL。 要求の wreqptr パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wreqptr パラメーターが要求に含まれないことを指定します。 要求に wreq または wreqptr パラメーターを含めないことは、発行するトークンの種類を STS が認識していることを意味します。|  
|requireHttps|Security Token Service (STS) との通信で HTTPS プロトコルを使用する必要があるかどうかを指定します。 任意。 既定値は "true"、HTTPS を使用する必要があります。|  
|resource|アクセスされているリソース (証明書利用者 (RP)) を Security Token Service (STS) に識別する URI。 任意。 WS-FEDERATION サインイン要求 wres パラメーターを設定します。 任意。 既定値は空の文字列です。これは、wres パラメーターが要求に含まれないことを指定します。 **注:** wres は従来のパラメーターです。 代わりに、 `realm` wtrealm パラメーターを使用する属性を指定してください。|  
|signInQueryString|WS-FEDERATION サインイン要求 URL でアプリケーション定義のクエリパラメーターを指定する機能拡張ポイントを提供します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。 パラメーターは、次の形式`"param1=value1&param2=value2&param3=value3"`を使用してクエリ文字列フラグメントとして指定されます。 **注:** 構成ファイルでは、クエリ文字列の ' & ' 文字をエンティティ参照を`&`使用して指定する必要があります。|  
|signOutQueryString|WS-FEDERATION サインイン要求 URL でアプリケーション定義のクエリパラメーターを指定する機能拡張ポイントを提供します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。 パラメーターは、次の形式`"param1=value1&param2=value2&param3=value3"`を使用してクエリ文字列フラグメントとして指定されます。 **注:** 構成ファイルでは、クエリ文字列の ' & ' 文字をエンティティ参照を`&`使用して指定する必要があります。|  
|signOutReply|WS-FEDERATION プロトコルを使用したパッシブサインアウト中に、クライアントが Security Token Service (STS) によってリダイレクトされる URL を指定します。 WS-FEDERATION サインアウト要求で wreply パラメーターを設定します。 任意。 既定値は空の文字列です。これは、要求に追加のパラメーターを含める必要がないことを指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfam) <xref:System.IdentityModel.Services.SessionAuthenticationModule>と (SAM) を構成する設定が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 `<wsFederation>`要素を使用して、wsfam の既定の ws-federation パラメーター設定と既定の動作を構成できます。 要素の`<wsFederation>`下で定義された ws-federation パラメーター設定。 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラスによって公開される同等のプロパティを設定します。 これらのプロパティは、WSFAM によって発行されたすべての要求で同じままです。 WSFAM によって公開されるイベントのイベントハンドラーを追加することで、要求の処理中に WS-FEDERATION パラメーターを動的に変更できます。たとえば<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> 、イベントです。 詳細については、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>クラスのドキュメントを参照してください。  
  
 要素は、 <xref:System.IdentityModel.Services.Configuration.WSFederationElement>クラスによって表されます。 `<wsFederation>` 構成オブジェクト自体は、 <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>クラスによって表されます。 プロパティを<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>通じてアクセスさ<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>れるオブジェクトに対して1つのインスタンスが設定され、wsfam の構成が提供されます。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>例  
 次の XML は、 `<wsFederation>` wsfam の設定を指定する要素を示しています。  
  
> [!WARNING]
>  この例では、WSFAM は HTTPS を使用する必要はありません。 これは、 `<wsFederation>`要素`requireHttps`の属性が設定`false`されているためです。 ほとんどの運用環境では、セキュリティ上のリスクが生じる可能性があるため、この設定は推奨されません。  
  
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
