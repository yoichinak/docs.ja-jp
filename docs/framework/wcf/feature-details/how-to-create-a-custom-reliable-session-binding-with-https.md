---
title: '方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039534"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する

ここでは、信頼できるセッションを使用した SSL (Secure Sockets Layer) トランスポート セキュリティの使用方法について説明します。 HTTPS 上で信頼できるセッションを使用するには、信頼できるセッションと HTTPS トランスポートを使用するカスタム バインドを作成する必要があります。 コードを使用して強制的に行う、または構成ファイルで宣言によって、信頼できるセッションが有効にします。 この手順では、クライアントとサービス構成ファイルを使用して、信頼できるセッションを有効にして、 [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)要素。

この手順の重要な部分は、 **\<エンドポイント >** 構成要素を含む、`bindingConfiguration`という名前のカスタム バインド構成を参照する属性`reliableSessionOverHttps`。 [ **\<バインド >** ](../../../../docs/framework/misc/binding.md)構成要素を含めることによって、信頼できるセッションと HTTPS トランスポートを使用することを指定するには、この名前を参照する **\<reliableSession >** と **\<httpsTransport >** 要素。

この例のソースのコピーを次を参照してください。[カスタム バインドの信頼できるセッションが HTTPS 経由で](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)します。

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS で信頼できるセッションを使用するを CustomBinding でサービスを構成します。

1. サービスの種類にサービス コントラクトを定義します。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. サービス クラスにサービス コントラクトを実装します。 サービスの実装の内部アドレスやバインディングの情報が指定されていないことに注意してください。 構成ファイルからのアドレスやバインディングの情報を取得するコードを記述するために必要ないです。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. 作成、 *Web.config*のエンドポイントを構成するファイル、`CalculatorService`という名前のカスタム バインドで`reliableSessionOverHttps`信頼できるセッションと HTTPS トランスポートを使用します。

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. 作成、 *Service.svc*行を含むファイル。

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. 場所、 *Service.svc*インターネット インフォメーション サービス (IIS) 仮想ディレクトリのファイル。

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS で信頼できるセッションを使用するを CustomBinding でクライアントを構成します。

1. 使用して、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからコードを生成するためのコマンドラインから。

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 生成されるクライアントが含まれています、`ICalculator`クライアント実装が満たす必要があるサービス コントラクトを定義するインターフェイス。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. 生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 サービスの実装の内部アドレスとバインディング情報が指定されていないことに注意してください。 構成ファイルからアドレスとバインディング情報を取得するコードを記述するために必要ないです。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. という名前のカスタム バインドを構成する`reliableSessionOverHttps`HTTPS トランスポートと信頼できるセッションを使用します。

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. クライアントをコンパイルして実行します。  

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

このサンプルで使用される証明書はテスト証明書で作成されたため、 *Makecert.exe*などの HTTPS アドレスにアクセスしようとするときに、セキュリティの警告が表示されます`https://localhost/servicemodelsamples/service.svc`、お使いのブラウザーから。

## <a name="see-also"></a>関連項目

- [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
