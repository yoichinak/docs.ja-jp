---
title: '方法: WCF Web サービス アプリケーションの WIF を有効にする'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: 4f67ddc7b61c5c127c7fcbe888454e0a4aa36539
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626091"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>方法: WCF Web サービス アプリケーションの WIF を有効にする
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Microsoft® Windows® Communication Foundation (WCF)  
  
## <a name="summary"></a>まとめ  
 ここでは、WCF Web サービスの WIF を有効にするための詳細な操作手順を示します。 また、アプリケーションの実行中に Web サービスが正しくクレームを表示しているかどうかを確認するためにアプリケーションをテストする方法についても説明します。 ここでは、セキュリティ トークン サービス (STS) を作成するための詳細な手順については説明しません。代わりに、Identity and Access Tool に付属している開発用 STS を使用します。 開発用 STS はテスト用に用意されたもので、実際の認証は行いません。 このページの内容を完了するには、Identity and Access Tool をインストールする必要があります。 これは、次の場所からダウンロードできます。[Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>目次  
  
- 目的  
  
- 概要  
  
- 手順の要約  
  
- 手順 1 – 簡単な WCF サービスの作成  
  
- 手順 2 – WCF サービスのクライアント アプリケーションの作成  
  
- 手順 3 – ソリューションをテストする  
  
## <a name="objectives"></a>目的  
  
- 発行済みトークンを必要とする WCF サービスを作成する  
  
- STS のトークンを要求し、それを WCF サービスに渡す WCF クライアントを作成する  
  
## <a name="overview"></a>概要  
 ここでは、WCF サービス開発時に開発者がフェデレーション認証を使用する方法を示します。 WCF サービスでフェデレーションを使用する利点には、次のものが含まれます。  
  
1. WCF サービス コード外の認証ロジックのファクタリング  
  
2. 既存の ID 管理ソリューションの再利用  
  
3. 他の ID ソリューションとの相互運用性  
  
4. 今後の変更に対する柔軟性と回復力  
  
 次の手順に示すように、WIF および関連する Identity and Access Tool を使用すると、フェデレーション認証を使用した WCF サービスの開発およびテストが簡単になります。  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – 簡単な WCF サービスの作成  
  
- 手順 2 – WCF サービスのクライアント アプリケーションの作成  
  
- 手順 3 – ソリューションをテストする  
  
## <a name="step-1--create-a-simple-wcf-service"></a>手順 1 – 簡単な WCF サービスの作成  
 この手順では、Identity and Access Tool に付属している開発用 STS を使用する新しい WCF サービスを作成します。  
  
#### <a name="to-create-a-simple-wcf-service"></a>簡単な WCF サービスを作成するには  
  
1. システム特権のあるモードで管理者として Visual Studio を起動します。  
  
2. Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。  
  
3. **[新しいプロジェクト]** ウィンドウで、**[WCF サービス アプリケーション]** をクリックします。  
  
4. **[名前]** で、「`TestService`」と入力し、**[OK]** を押します。  
  
5. **ソリューション エクスプローラー**で **[TestService]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。  
  
6. **[Identity and Access]** ウィンドウが表示されます。 **[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。 Identity and Access Tool は、サービスが WIF を使用し、*Web.config* ファイルに構成要素を追加することによって認証をローカル開発用の STS (**LocalSTS**) に外部委託するように構成します。  
  
7. *Service1.svc.cs* ファイルで、**System.Security.Claims** 名前空間に `using` ディレクティブを追加し、既存のコードを次のコードに置き換え、ファイルを保存します。  
  
    ```csharp  
    public class Service1 : IService1  
    {  
        public string ComputeResponse(string input)  
        {  
            // Get the caller's identity from ClaimsPrincipal.Current  
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;  
  
            // Start generating the output  
            StringBuilder builder = new StringBuilder();  
            builder.AppendLine("Computed by ClaimsAwareWebService");  
            builder.AppendLine("Input received from client:" + input);  
  
            if (claimsPrincipal != null)  
            {  
                // Display the claims from the caller. Do not use this code in a production application.  
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;  
                builder.AppendLine("Client Name:" + identity.Name);  
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);  
                builder.AppendLine("The service received the following issued claims of the client:");  
  
                // Iterate over the caller’s claims and append to the output  
                foreach (Claim claim in claimsPrincipal.Claims)  
                {  
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);  
                }  
            }  
  
            return builder.ToString();  
        }  
    }  
    ```  
  
     `ComputeResponse` メソッドでは、**LocalSTS** が発行するさまざまなクレームのプロパティが表示されます。  
  
8. *IService1.cs* ファイルでは、既存のコードを次のコードに置き換え、ファイルを保存します。  
  
    ```csharp  
    [ServiceContract]  
    public interface IService1  
    {  
        [OperationContract]  
        string ComputeResponse(string input);  
    }  
    ```  
  
9. プロジェクトをビルドします。  
  
10. デバッガーを起動せずにサービスを実行するには、**Ctrl-F5** キーを押します。 Web ページが開き、サービスが表示されます。通知領域 (システム トレイ) を見ると、**LocalSTS** が実行中であることが確認できます。  
  
    > [!IMPORTANT]
    >  次の手順でクライアント アプリケーションにサービス参照を追加するときに、**TestService** と **LocalSTS** の両方が実行されている必要があります。  
  
## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>手順 2 – WCF サービスのクライアント アプリケーションの作成  
 この手順では、前の手順で作成した WCF サービスとの認証に開発用 STS を使用するコンソール アプリケーションを作成します。  
  
#### <a name="to-create-a-client-application"></a>クライアント アプリケーションを作成するには  
  
1. Visual Studio でソリューションを右クリックし、**[追加]** をクリックしてから **[新しいプロジェクト]** をクリックします。  
  
2. **[新しいプロジェクトの追加]** ウィンドウで、**[Visual C#]** テンプレート一覧から **[コンソール アプリケーション]** を選択し、「`Client`」と入力して **[OK]** を押します。 新しいプロジェクトがソリューション フォルダーに作成されます。  
  
3. **[Client]** プロジェクトの下の **[参照設定]** を右クリックし、**[サービス参照の追加]** をクリックします。  
  
4. **[サービス参照の追加]** ウィンドウで、**[探索]** ボタンのドロップダウン矢印をクリックし、**[ソリューションのサービス]** をクリックします。 **[アドレス]** には、前の手順で作成した WCF サービスが自動的に入力されます。**[名前空間]** は、**[ServiceReference1]** に設定されます。 **[OK]** をクリックします。  
  
    > [!IMPORTANT]
    >  クライアントにサービス参照を追加するときに、**TestService** と **LocalSTS** の両方が実行されている必要があります。  
  
5. Visual Studio は、WCF サービスのプロキシ クラスを生成し、必要なリファレンス情報をすべて追加します。 また、*App.config* ファイルに要素を追加して、サービスでの認証のために STS からトークンを取得するようにクライアントを構成します。 このプロセスが完了したら、**Program.cs** ファイルが開きます。 **System.ServiceModel** と **Client.ServiceReference1** それぞれに `using` ディレクティブを追加し、**Main** メソッドを次のコードに置き換えて、ファイルを保存します。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the client for the service  
        Service1Client client = new Service1Client();  
        Console.WriteLine("-------------WCF Client Application--------------\n");  
  
        while (!ShouldQuitApplication())  
        {  
            try  
            {  
                Console.WriteLine(client.ComputeResponse("Hello World"));  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
                Console.WriteLine(e.StackTrace);  
                Exception ex = e.InnerException;  
                while (ex != null)  
                {  
                    Console.WriteLine("===========================");  
                    Console.WriteLine(ex.Message);  
                    Console.WriteLine(ex.StackTrace);  
                    ex = ex.InnerException;  
                }  
            }  
            catch (TimeoutException)  
            {  
                Console.WriteLine("Timed out...");  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("An unexpected exception occurred.");  
                Console.WriteLine(e.StackTrace);  
            }  
        }  
  
        client.Close();  
  
        if (client != null)  
        {  
            client.Abort();  
        }  
    }  
  
    static bool ShouldQuitApplication()  
    {  
        Console.WriteLine("---------------------------------------------------------------------");  
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");  
        Console.WriteLine("----------------------------------------------------------------------");  
  
        ConsoleKeyInfo keyInfo = Console.ReadKey();  
        if (keyInfo.Key == ConsoleKey.Enter)  
            return false;  
        return true;  
    }  
    ```  
  
6. *App.config* ファイルを開き、`<system.serviceModel>` 要素の下に最初の子要素として次の XML を追加し、ファイルを保存します。  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
         <behavior>  
           <clientCredentials>  
             <serviceCertificate>  
               <authentication certificateValidationMode="None"/>  
             </serviceCertificate>  
           </clientCredentials>  
         </behavior>  
       </endpointBehaviors>  
     </behaviors>  
    ```  
  
     これにより、証明書の検証が無効になります。  
  
7. **[TestService]** ソリューションを右クリックし、**[スタートアップ プロジェクトの設定]** をクリックします。 **[スタートアップ プロジェクト]** プロパティ ページが開きます。 **[スタートアップ プロジェクト]** プロパティ ページで、**[マルチ スタートアップ プロジェクト]** を選択します。次に、各プロジェクトの **[アクション]** フィールドをクリックし、ドロップダウン メニューから **[開始]** を選択します。 **[OK]** をクリックして設定を保存します。  
  
8. ソリューションをビルドします。  
  
## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする  
 この手順では、WIF 対応 WCF アプリケーションをテストし、クレームが表示されることを確認します。  
  
#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>WIF 対応 WCF アプリケーションをテストしてクレームを確認するには  
  
1. **F5** キーを押してアプリケーションをビルドし、実行します。 コンソール ウィンドウで、次のテキストで表示されます。**サービス、アプリケーションを終了するその他の任意のキーを呼び出すには Enter キーを押します。**  
  
2. **Enter** キーを押すと、コンソールに以下のクレーム情報が表示されます。  
  
    ```  
    Computed by Service1  
    Input received from client: Hello World  
    Client Name: Terry  
    IsAuthenticated: True  
    The service received the following issued claims of the client:  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry  
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams  
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer  
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com  
    ```  
  
    > [!IMPORTANT]
    >  **Enter** キーを押す前に **TestService** と **LocalSTS** の両方が実行されている必要があります。 Web ページが開き、サービスが表示されます。通知領域 (システム トレイ) を見ると、**LocalSTS** が実行中であることが確認できます。  
  
3. これらのクレームがコンソールに表示されている場合、WCF サービスのクレームを表示するための STS での認証が正常に完了しています。
