---
title: '方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: f2ac263d8869c770594283923a45c7c53c9df4cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626129"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>まとめ  
 この操作方法では、簡単なクレーム対応 ASP.NET MVC Web アプリケーションを作成するための詳細な手順を示します。 また、クレーム ベースの認証を正常に実装するために簡単なクレーム対応 ASP.NET MVC Web アプリケーションをテストする方法も示します。 この操作方法には、セキュリティ トークン サービス (STS) の詳細な作成手順は含まれていません。既に STS が構成済みであると想定します。  
  
## <a name="contents"></a>目次  
  
- 目的  
  
- 手順の要約  
  
- 手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する  
  
- 手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する  
  
- 手順 3 – ソリューションをテストする  
  
- 関連項目  
  
## <a name="objectives"></a>目的  
  
- クレーム ベースの認証用の ASP.NET MVC Web アプリケーションを構成する  
  
- クレーム対応 ASP.NET MVC Web アプリケーションが正常であることをテストする  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する  
  
- 手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する  
  
- 手順 3 – ソリューションをテストする  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する  
 この手順では、新しい ASP.NET MVC アプリケーションを作成します。  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>簡単な ASP.NET MVC アプリケーションを作成するには  
  
1. Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。  
  
2. **[新しいプロジェクト]** ウィンドウで、**[ASP.NET MVC 3 Web アプリケーション]** をクリックします。  
  
3. **[名前]** で、「`TestApp`」と入力して **[OK]** を押します。  
  
4. **[新しい ASP.NET MVC 3 プロジェクト]** ダイアログで、使用可能なテンプレートから **[インターネット アプリケーション]** を選択し、**[ビュー エンジン]** が **[Razor]** に設定されていることを確認して **[OK]** をクリックします。  
  
5. 新しいプロジェクトが開いたら、**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックして **[プロパティ]** オプションを選択します。  
  
6. プロジェクトのプロパティ ページで、左側の **[Web]** タブをクリックし、**[ローカル IIS Web サーバーを使用する]** オプションが選択されていることを確認します。  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する  
 この手順では、構成エントリを ASP.NET MVC Web アプリケーションの *Web.config* 構成ファイルに追加して、クレーム対応にします。  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成するには  
  
1. 次の構成セクションの定義を *Web.config* 構成ファイルに追加します。 これで、Windows Identity Foundation に必要な構成セクションが定義されます。 **\<configuration>** 開始要素のすぐ後に定義を追加します。  
  
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
  
4. 以下の Windows Identity Foundation 関連の構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が、**\<audienceUris>** エントリ、**\<wsFederation>** 要素の **realm** 属性、および **\<wsFederation>** 要素の **reply** 属性の値と一致することを確認します。 また、**issuer** の値がセキュリティ トークン サービス (STS) URL に適したものであることを確認します。  
  
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
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <xref:System.IdentityModel> アセンブリに参照を追加します。  
  
6. ソリューションをコンパイルして、エラーがあるかどうかを確認します。  
  
## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする  
 この手順では、クレーム ベースの認証用に構成された ASP.NET MVC Web アプリケーションをテストします。 基本テストを実行するには、セキュリティ トークン サービス (STS) で発行されたトークンでクレームを表示する簡単なコードを追加します。  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>クレーム ベースの認証用の ASP.NET MVC アプリケーションをテストするには  
  
1. **ソリューション エクスプローラー**で、**Controllers** フォルダーを展開し、エディターで *HomeController.cs* ファイルを開きます。 **Index** メソッドに次のコードを追加します。  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. **ソリューション エクスプローラー**で、**Views** フォルダーを展開してから **Home** フォルダーを展開し、エディターで *Index.cshtml* ファイルを開きます。 その内容を削除し、次のマークアップを追加します。  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. **F5** キーを押して、ソリューションを実行します。  
  
4. セキュリティ トークン サービスで発行されたトークンでクレームを表示するページが表示されます。  
  
## <a name="related-items"></a>関連項目  
  
- [方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションを構築します。](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
