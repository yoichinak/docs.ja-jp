---
title: '方法: Windows 認証を使用してクレーム対応 ASP.NET アプリケーションをビルドする'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 039fccde55dd48571e38f064f68b16480b65cb44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650404"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a>方法: Windows 認証を使用してクレーム対応 ASP.NET アプリケーションをビルドする
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® Web フォーム  
  
## <a name="summary"></a>まとめ  
 この操作方法では、Windows 認証を使用する簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。 また、Windows 認証を使用してユーザーがサインインするときにクレームが表示されることを確認するために、アプリケーションをテストする方法についても説明します。  
  
## <a name="contents"></a>目次  
  
- 目的  
  
- 概要  
  
- 手順の要約  
  
- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
  
- 手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する  
  
- 手順 3 – ソリューションをテストする  
  
## <a name="objectives"></a>目的  
  
- Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する  
  
- ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する  
  
## <a name="overview"></a>概要  
 .NET 4.5 には、WIF とそのクレーム ベースの認証が、Framework の不可欠な部分として組み込まれています。 以前は、ASP.NET ユーザーからのクレームが必要な場合に、WIF をインストールしてから、`Thread.CurrentPrincipal` または `HttpContext.Current.User` などのプリンシパル オブジェクトにインターフェイスをキャストする必要がありました。 現在は、これらのプリンシパル オブジェクトで自動的にクレームが処理されます。  
  
 Windows 認証では、.NET 4.5 に組み込まれている WIF による利点が得られます。Windows 資格情報で認証されたすべてのユーザーには自動的にクレームが関連付けられるためです。 この操作方法で示すように、Windows 認証を使用する ASP.NET アプリケーションでは、これらのクレームの使用をすぐに開始することができます。  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
  
- 手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する  
  
- 手順 3 – ソリューションをテストする  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには  
  
1. Visual Studio を起動してから、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。  
  
2. **[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。  
  
3. **[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。  
  
4. **TestApp** プロジェクトが作成されたら、**ソリューション エクスプローラー**でそれをクリックします。 プロジェクトのプロパティが、**ソリューション エクスプローラー**の下の **[プロパティ]** ウィンドウに表示されます。 **[Windows 認証]** プロパティを **[有効]** に設定します。  
  
    > [!WARNING]
    >  新しい ASP.NET アプリケーションでは Windows 認証が既定で無効になるため、手動で有効にする必要があります。  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する  
 この手順では、構成エントリを *Web.config* 構成ファイルに追加し、アカウントのクレーム情報を表示するように *Default.aspx* ファイルを変更します。  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a>Windows 認証を使用してクレーム用の ASP.NET アプリケーションを構成するには  
  
1. **TestApp** プロジェクトの *Default.aspx* ファイルで、既存のマークアップを次のものに置き換えます。  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     この手順では GridView コントロールを *Default.aspx* ページに追加します。このページには、Windows 認証から取得されたクレームが取り込まれます。  
  
2. *Default.aspx* ファイルを保存し、*Default.aspx.cs* という名前の分離コード ファイルを開きます。 既存のコードを次のコードに置き換えます。  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     上記のコードでは、認証ユーザーに関するクレームが表示されます。  
  
3. アプリケーションの認証の種類を変更するには、プロジェクトのルート *Web.config* ファイルの **\<system.web>** セクション内の **\<authentication>** ブロックを変更して、以下の構成エントリのみが含まれるようにします。  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4. 最後に、同じ *Web.config* ファイルの **\<system.web>** セクション内の **\<authorization>** ブロックを変更して、認証を強制します。  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする  
 この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーが Windows 認証を使用してサインインするときに、クレームが表示されることを確認します。  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a>Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには  
  
1. **F5** キーを押してアプリケーションをビルドし、実行します。 *Default.aspx* が表示されます。Windows アカウント名 (ドメイン名を含む) は、ページの右上に認証ユーザーとして既に表示されています。 ページの内容には、Windows アカウントから取得されたクレームが入力されたテーブルが含まれています。
