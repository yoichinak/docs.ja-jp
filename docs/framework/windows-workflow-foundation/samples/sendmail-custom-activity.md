---
title: SendMail カスタム アクティビティ
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 3bbb16fd99d5d7de4183b26030c0afe65ebc90cd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617310"
---
# <a name="sendmail-custom-activity"></a>SendMail カスタム アクティビティ
このサンプルでは、<xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。 カスタム アクティビティの機能を使用して<xref:System.Net.Mail.SmtpClient>非同期的に電子メールを送信して、認証を使用したメールを送信します。 また、テスト モード、トークン置換、ファイル テンプレート、テスト ドロップ パスなどのエンドユーザーの機能も提供しています。  
  
 次の表で、`SendMail` アクティビティの引数の詳細を説明します。  
  
|名前|種類|説明|  
|-|-|-|  
|ホスト|String|SMTP サーバー ホストのアドレス。|  
|ポート|String|ホストの SMTP サービスのポート。|  
|EnableSsl|bool|<xref:System.Net.Mail.SmtpClient> が、接続を暗号化するために SSL (Secure Sockets Layer) を使用するかどうかを指定します。|  
|UserName|String|差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するユーザー名。|  
|[Password]|String|差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するパスワード。|  
|Subject|<xref:System.Activities.InArgument%601>\<string>|メッセージの件名。|  
|本文|<xref:System.Activities.InArgument%601>\<string>|メッセージの本文。|  
|添付ファイル|<xref:System.Activities.InArgument%601>\<string>|この電子メール メッセージに添付されるデータの格納に使用される添付データのコレクション。|  
|From|<xref:System.Net.Mail.MailAddress>|この電子メール メッセージのアドレス。|  
|目的|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|この電子メール メッセージの受信者を格納するアドレスのコレクション。|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|この電子メール メッセージのカーボン コピー (CC) 受信者を格納するコレクションをアドレスします。|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|この電子メール メッセージのブラインド カーボン コピー (BCC) 受信者を格納するアドレスのコレクション。|  
|トークン|<xref:System.Activities.InArgument%601>< IDictionary\<, string >>|本文で置換するトークン。 この機能を使用すると、本文にいくつかの値を指定した後、このプロパティを使用して提供されるトークンで置換できます。|  
|BodyTemplateFilePath|String|本文のテンプレートのパス。 `SendMail` アクティビティは、このファイルの内容をその body プロパティにコピーします。<br /><br /> テンプレートは、tokens プロパティの内容によって置き換えられるトークンを含めることができます。|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|このプロパティが設定されている場合は、すべての電子メールが指定されているアドレスに送信されます。<br /><br /> このプロパティは、ワークフローをテストするときに使用するためのものです。 たとえば、ことを確認する場合に、すべての電子メールが実際の受信者に送信せず送信されます。|  
|TestDropPath|String|このプロパティが設定されている場合、すべての電子メールは、指定したファイルにも保存されます。<br /><br /> このプロパティは、送信メールの内容と形式が適切であるかどうかを確認する、ワークフローのデバッグまたはテストするときに使用されるものです。|  
  
## <a name="solution-contents"></a>ソリューションのコンテンツ  
 ソリューションには、次の 2 つのプロジェクトが含まれています。  
  
|プロジェクト|説明|重要なファイル|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail アクティビティ|1.SendMail.cs: main アクティビティの実装<br />2.SendMailDesigner.xaml および SendMailDesigner.xaml.cs: SendMail アクティビティのデザイナー<br />3.MailTemplateBody.htm: 送信される電子メールのテンプレート|  
|SendMailTestClient|SendMail アクティビティをテストするクライアント。  このプロジェクトでは、SendMail アクティビティを宣言的に起動する方法とプログラムで起動する方法を示します。|1.Sequence1.xaml: SendMail アクティビティを起動するワークフロー<br />2.Program.cs: Sequence1 を呼び出し、SendMail を使用するワークフローもプログラムで作成します。|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>SendMail アクティビティの追加構成  
 サンプルには表示されませんが、SendMail アクティビティの追加構成を実行できます。 次の 3 つのセクションは、その方法を示しています。  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>本文で指定されたトークンを使用した電子メールの送信  
 次のコード スニペットでは、本文のトークンを使用して電子メールを送信する方法を示します。 トークンが body プロパティに指定されていることに注目してください。 それらのトークンの値は、tokens プロパティに指定されています。  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>テンプレートを使用した電子メールの送信  
 次のスニペットでは、本文のテンプレート トークンを使用して電子メールを送信する方法を示します。 `BodyTemplateFilePath` プロパティを設定するときに、Body プロパティの値を指定する必要がないことに注目してください (テンプレート ファイルのコンテンツは本文にコピーされます)。  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>テスト モードでの電子メールの送信  
 このコード スニペットは、2 つのテストのプロパティを設定する方法を示します。 設定して`TestMailTo`すべてのメッセージには、に送信されます`john.doe@contoso.con`(To、Cc、Bcc の値を考慮) なし。 TestDropPath を設定すると、送信するすべての電子メールは、指定したパスにも記録されます。 これらのプロパティは、個別に設定できます (関連していません)。  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>セットアップ手順  
 このサンプルでは SMTP サーバーにアクセスする必要があります。  
  
 SMTP サーバーの設定に関する詳細については、次のリンクを参照してください。  
  
- [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [SMTP サービス (IIS 6.0) を構成します。](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [IIS 7.0:SMTP 電子メールを構成します。](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [SMTP サービスをインストールする方法](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 ダウンロードには、サードパーティで提供されている SMTP エミュレーターを使用できます。  
  
##### <a name="to-run-this-sample"></a>このサンプルを実行するには  
  
1. Visual Studio 2010 を使用して、SendMail.sln ソリューション ファイルを開きます。  
  
2. 有効な SMTP サーバーへのアクセス権があることを確認してください。 セットアップ手順を参照してください。  
  
3. サーバー アドレスとの電子メール アドレスには、プログラムを構成します。  
  
     このサンプルを正しく実行するには、Program.cs および Sequence.xaml の値からその電子メール アドレス、SMTP サーバーのアドレスを構成する必要があります。 プログラムでは電子メールが 2 つの方法で送信されるため、両方の場所でアドレスを変更する必要があります。  
  
4. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
5. ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`