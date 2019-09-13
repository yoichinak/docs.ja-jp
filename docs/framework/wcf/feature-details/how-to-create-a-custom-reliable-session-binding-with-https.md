---
title: '方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 7f22eeaae39b4d9a83c77c7f3e9db1d7d3f04e8e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895202"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>方法: カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する

ここでは、信頼できるセッションを使用した SSL (Secure Sockets Layer) トランスポート セキュリティの使用方法について説明します。 HTTPS 上で信頼できるセッションを使用するには、信頼できるセッションと HTTPS トランスポートを使用するカスタム バインドを作成する必要があります。 信頼できるセッションは、コードを使用するか、構成ファイルで宣言によって、強制的に有効にします。 この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションと[ **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)要素を有効にします。

この手順の重要な部分は、  **\<エンドポイント >** `bindingConfiguration`構成要素に、という名前`reliableSessionOverHttps`のカスタムバインディング構成を参照する属性が含まれていることです。 [ **\<Binding >** ](../../../../docs/framework/misc/binding.md) configuration 要素は、この名前を参照して、  **\<reliableSession >** と **\<httpsTransport を含めることで、信頼できるセッションと HTTPS トランスポートを使用することを指定し >** 要素。

この例のソースコピーについては、「HTTPS を使用した[カスタムバインディングの信頼できるセッション](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)」を参照してください。

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS で信頼できるセッションを使用するための CustomBinding でサービスを構成する

1. サービスの種類にサービス コントラクトを定義します。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. サービス クラスにサービス コントラクトを実装します。 サービスの実装内では、アドレスまたはバインド情報が指定されていないことに注意してください。 構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. *Web.config ファイルを*作成して、 `CalculatorService`信頼できるセッションと HTTPS トランスポートを使用すると`reliableSessionOverHttps`いう名前のカスタムバインドを持つのエンドポイントを構成します。

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. 次の行を含む .svc ファイルを作成*し*ます。

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. サービスの *.svc*ファイルをインターネットインフォメーションサービス (IIS) 仮想ディレクトリに配置します。

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>HTTPS で信頼できるセッションを使用するようにクライアントを構成する (CustomBinding)

1. コマンドラインから[ServiceModel メタデータユーティリティツール (*svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービスメタデータからコードを生成します。

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 生成されるクライアントには、 `ICalculator`クライアント実装が満たす必要のあるサービスコントラクトを定義するインターフェイスが含まれています。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. 生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 サービスの実装内でアドレスとバインディング情報が指定されていないことに注意してください。 構成ファイルからアドレスおよびバインド情報を取得するコードを記述する必要はありません。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. HTTPS トランスポートと信頼できる`reliableSessionOverHttps`セッションを使用するように、という名前のカスタムバインディングを構成します。

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. クライアントをコンパイルして実行します。  

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

このサンプルで使用される証明書は、 *Makecert*で作成されたテスト証明書であるため、ブラウザーからなどの HTTPS アドレス`https://localhost/servicemodelsamples/service.svc`にアクセスしようとすると、セキュリティの警告が表示されます。

## <a name="see-also"></a>関連項目

- [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
