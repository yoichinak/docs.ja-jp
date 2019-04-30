---
title: '方法: トークン再生検出を有効にする'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
ms.openlocfilehash: a357f153d61b6a8e1e105639bd68647dabdc26f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940479"
---
# <a name="how-to-enable-token-replay-detection"></a>方法: トークン再生検出を有効にする
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® Web フォーム  
  
## <a name="summary"></a>まとめ  
 ここでは、WIF を使用する ASP.NET アプリケーションでトークン再生検出を有効にするための詳細な操作手順を示します。 トークン再生検出が有効になっていることを確認するためにアプリケーションをテストする方法についても説明します。 ここでは、セキュリティ トークン サービス (STS) を作成するための詳細な手順については説明しません。代わりに、Identity and Access Tool に付属している開発用 STS を使用します。 開発用 STS はテスト用に用意されたもので、実際の認証は行いません。 このページの内容を完了するには、Identity and Access Tool をインストールする必要があります。 これは、次の場所からダウンロードできます。[Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>目次  
  
- 目的  
  
- 概要  
  
- 手順の要約  
  
- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化  
  
- 手順 2 – ソリューションのテスト  
  
## <a name="objectives"></a>目的  
  
- Identity and Access Tool の WIF および開発用 STS を使用する簡単な ASP.NET アプリケーションの作成  
  
- トークン再生検出の有効化と動作確認  
  
## <a name="overview"></a>概要  
 再生攻撃は、クライアントが既に使用している STS トークンで証明書利用者に対する認証を試みた場合に発生します。 この攻撃を防ぐために、WIF には、以前に使用された STS トークンの再生検出キャッシュが含まれます。 有効にすると、再生検出で受信要求のトークンがチェックされ、トークンが以前に使用されているかどうかが確認されます。 トークンが既に使用されている場合、要求は拒否され、<xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 例外がスローされます。  
  
 次の手順では、再生検出を有効にするために必要な構成の変更を示します。  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化  
  
- 手順 2 – ソリューションのテスト  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>手順 1 – 簡単な ASP.NET Web フォーム アプリケーションの作成と再生検出の有効化  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成し、再生検出を有効にするために *Web.config* ファイルを変更します。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには  
  
1. Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。  
  
2. **[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。  
  
3. **[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。  
  
4. **ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。  
  
5. **[Identity and Access]** ウィンドウが表示されます。 **[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。  
  
6. *Web.config* ファイルに、以下のように **\<system.identityModel>** および **\<identityConfiguration>** 要素のすぐ後に次の **\<tokenReplayDetection>** 要素を追加します。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>手順 2 – ソリューションのテスト  
 この手順では、WIF 対応 ASP.NET アプリケーションをテストし、再生検出が有効になっていることを確認します。  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>再生検出のために WIF 対応 ASP.NET アプリケーションをテストするには  
  
1. **F5** キーを押して、ソリューションを実行します。 既定の ASP.NET ホーム ページが開き、ユーザー名 *Terry* (開発用 STS によって返される既定のユーザー) で自動的に認証されます。  
  
2. ブラウザーの **[戻る]** ボタンを押します。 表示される、 **'/' アプリケーションでサーバー エラー**と次の説明ページ。*ID1062:再生が検出されました。トークン。'System.identitymodel.tokens.samlsecuritytoken'*、その後に、 *AssertionId*と*発行者*します。  
  
     このエラー ページが表示されるのは、トークン再生が検出されたときに <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 型の例外がスローされたためです。 このエラーが発生するのは、トークンが最初に表示されたときに初期 POST 要求を再送信しようとしたためです。 **[戻る]** ボタンを押しても、サーバーへの後続の要求でこのような動作にはなりません。
