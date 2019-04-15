---
title: '方法: 信頼されたセッション内のメッセージを変換する'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: aad4eae870e3ba603c56a28a620fe8bc0e31ceb6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342988"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>方法: 信頼されたセッション内のメッセージを変換する

このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを (既定ではなく) オプションでサポートするシステム指定のバインディングを使用します。 命令型コードを使用して、信頼できるセッションを有効にするか、構成ファイルで宣言します。 この手順は、信頼できるセッションを有効にして、メッセージが送信された順序で到着したかを規定するために、クライアントとサービス構成ファイルを使用します。

この手順の重要な部分は、エンドポイント構成要素を含む、`bindingConfiguration`という名前のバインド構成を参照する属性`Binding1`します。 [ **\<バインド >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前の参照、`enabled`の属性、 [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100))要素`true`します。 信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。

この例のソースのコピーを次を参照してください。 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)します。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding 使用サービスを構成します。

1. サービスの種類にサービス コントラクトを定義します。

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. サービス クラスにサービス コントラクトを実装します。 サービスの実装の内部アドレスやバインディングの情報が指定されていないことに注意してください。 構成ファイルからのアドレスやバインディングの情報を取得するコードを記述するために必要ないです。

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. 作成、 *Web.config*のエンドポイントを構成するファイル、`CalculatorService`を使用して、<xref:System.ServiceModel.WSHttpBinding>信頼できるセッションが有効になっており、必要なメッセージの配信の順序で。

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. 作成、 *Service.svc*行を含むファイル。

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. 場所、 *Service.svc*インターネット インフォメーション サービス (IIS) 仮想ディレクトリのファイル。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用して、WSHttpBinding でクライアントを構成します。

1. 使用して、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからコードを生成するためのコマンドラインから。

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 生成されたクライアントが含まれています、`ICalculator`クライアント実装が満たす必要があるサービス コントラクトを定義するインターフェイス。

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. 生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 サービスの実装内部アドレスとバインディング情報をどこでも指定されていないことに注意してください。 構成ファイルからのアドレスやバインディングの情報を取得するコードを記述するために必要ないです。

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe*も使用するクライアントの構成を生成、<xref:System.ServiceModel.WSHttpBinding>クラス。 構成ファイルの名前を付けます*App.config* Visual Studio を使用する場合。

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. インスタンスを作成、`ClientCalculator`アプリケーションでサービス操作を呼び出します。

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. クライアントをコンパイルして実行します。

## <a name="example"></a>例

システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。 不足している機能には次が含まれます。

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

信頼できるセッションをサポートするカスタム バインドを作成する方法の例は、次を参照してください。[方法。HTTPS で信頼できるセッションをカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)します。

## <a name="see-also"></a>関連項目

- [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
