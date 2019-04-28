---
title: カスタムのトークン ハンドラー
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792770"
---
# <a name="custom-token-handlers"></a>カスタムのトークン ハンドラー
このトピックでは、WIF のトークン ハンドラーと、それらを使用してトークンをどのように処理するかを説明します。 また、WIF で既定ではサポートされていないトークンの種類用にカスタム トークン ハンドラーを作成するために必要なことについても説明します。  
  
## <a name="introduction-to-token-handlers-in-wif"></a>WIF のトークン ハンドラーの概要  
 WIF は、証明書利用者 (RP) アプリケーションまたはセキュリティ トークン サービス (STS) のトークンの作成、読み取り、書き込み、および検証を行う際に、セキュリティ トークン ハンドラーに依存します。 トークン ハンドラーは WIF パイプラインでカスタム トークン ハンドラーを追加したり、既存のトークン ハンドラーがトークンを管理する方法をカスタマイズするための機能拡張ポイントです。 WIF では 9 つの組み込みセキュリティ トークン ハンドラーが提供されます。必要に応じて、これらを変更または完全にオーバーライドして機能を変更することができます。  
  
## <a name="built-in-security-token-handlers-in-wif"></a>WIF の組み込みセキュリティ トークン ハンドラー  
 WIF 4.5 には、抽象基本クラス <xref:System.IdentityModel.Tokens.SecurityTokenHandler> から派生する次の 9 つのセキュリティ トークン ハンドラー クラスが含まれています。  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>カスタム トークン ハンドラーの追加  
 SWT (Simple Web Token) や JWT (JSON Web Token) など、一部のトークン型には、WIF によって提供される組み込みトークン ハンドラーがありません。 これらのトークン型や、組み込みハンドラーがない他のトークン型の場合は、以下の手順を実行して、カスタム トークン ハンドラーを作成する必要があります。  
  
#### <a name="adding-a-custom-token-handler"></a>カスタム トークン ハンドラーの追加  
  
1. <xref:System.IdentityModel.Tokens.SecurityTokenHandler> から派生する新しいクラスを作成します。  
  
2. 以下のメソッドをオーバーライドし、独自の実装を指定します。  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. WIF に適用される **\<system.identityModel>** セクション内の、*Web.config* または *App.config* ファイルの新しいカスタム トークン ハンドラーへの参照を追加します。 たとえば、次の構成マークアップでは、**CustomToken** 名前空間に存在する **MyCustomTokenHandler** という名前の新しいトークン ハンドラーを指定します。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     既に組み込みトークン ハンドラーがあるトークン型を処理する独自のトークン ハンドラーを指定する場合は、**\<remove>** 要素を追加して、既定のハンドラーを削除し、代わりにカスタム ハンドラーを使用する必要があります。 たとえば、次の構成では、既定の <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> をカスタム トークン ハンドラーに置き換えます。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
