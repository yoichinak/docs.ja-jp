---
title: '方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 74f15c3ac6e5192ce3565579d515198d3b7e39f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769594"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする
## <a name="applies-to"></a>対象  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web フォーム  
  
## <a name="summary"></a>まとめ  
 この操作方法では、簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。 また、フェデレーション認証を正常に実装するために簡単なクレーム対応 ASP.NET Web フォーム アプリケーションをテストする方法も示します。 この操作方法には、セキュリティ トークン サービス (STS) の詳細な作成手順は含まれていません。既に STS が構成済みであると想定します。  
  
## <a name="contents"></a>目次  
  
-   目的  
  
-   手順の要約  
  
-   手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
  
-   手順 2 – クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する  
  
-   手順 3 – ソリューションをテストする  
  
## <a name="objectives"></a>目的  
  
-   クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する  
  
-   クレーム対応 ASP.NET Web フォーム アプリケーションが正常であることをテストする  
  
## <a name="summary-of-steps"></a>手順の要約  
  
-   手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
  
-   手順 2 – フェデレーション認証用の ASP.NET Web フォーム アプリケーションを構成する  
  
-   手順 3 – ソリューションをテストする  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには  
  
1. Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。  
  
2. **[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。  
  
3. **[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>手順 2 – クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する  
 この手順では、構成エントリを ASP.NET Web フォーム アプリケーションの *Web.config* 構成ファイルに追加して、クレーム対応にします。  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>クレーム ベースの認証用の ASP.NET アプリケーションを構成するには  
  
1. **\<configuration>** 開始要素のすぐ後の *Web.config* 構成ファイルに、次の構成セクション エントリを追加します。  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. 次のように、アプリケーションのフェデレーション メタデータへのアクセスを有効にする **\<location>** 要素を追加します。  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. **\<system.web>** 要素内で以下の構成エントリを追加して、ユーザーを拒否し、ネイティブ認証を無効にし、認証を管理するために WIF を有効にします。  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. フェデレーション認証用のモジュールを定義する **\<system.webServer>** 要素を追加します。 *PublicKeyToken* 属性は、前の手順で追加した **\<configSections>** エントリの *PublicKeyToken* 属性と同じである必要があることに注意してください。  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. 以下の Windows Identity Foundation 関連の構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が、**\<audienceUris>** エントリ、**\<wsFederation>** 要素の **realm** 属性、および **\<wsFederation>** 要素の **reply** 属性の値と一致することを確認します。 また、**issuer** の値がセキュリティ トークン サービス (STS) URL に適したものであることを確認します。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <xref:System.IdentityModel> アセンブリに参照を追加します。  
  
7. ソリューションをコンパイルして、エラーがないかどうかを確認します。  
  
## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする  
 この手順では、クレーム ベースの認証用に構成された ASP.NET Web フォーム アプリケーションをテストします。 基本テストを実行するには、セキュリティ トークン サービス (STS) で発行されたトークンでクレームを表示するコードを追加します。  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションをテストするには  
  
1. **TestApp** プロジェクトの下にある **Default.aspx** ファイルを開き、既存のマークアップを次のマークアップに置き換えます。  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. **Default.aspx** を保存し、**Default.aspx.cs** という名前の分離コード ファイルを開きます。  
  
    > [!NOTE]
    >  **Default.aspx.cs** は、ソリューション エクスプローラーで **Default.aspx** の下に隠れていることがあります。 **Default.aspx.cs** が表示されない場合は、**Default.aspx** の横の三角形をクリックして展開します。  
  
3. **Default.aspx.cs** の **Page_Load** メソッド内の既存のコードを次のコードに置き換えます。  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. **Default.aspx.cs** を保存して、ソリューションをビルドします。  
  
5. **F5** キーを押して、ソリューションを実行します。  
  
6. セキュリティ トークン サービスで発行されたトークンでクレームを表示するページが表示されます。
