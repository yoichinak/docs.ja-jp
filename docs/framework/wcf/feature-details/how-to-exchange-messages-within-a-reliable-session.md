---
title: '方法: 信頼されたセッション内のメッセージを変換する'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 5b01ddfd95db2f7e88f9481265c348f4f16fbbee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579477"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>方法: 信頼されたセッション内のメッセージを変換する

このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを (既定ではなく) オプションでサポートするシステム指定のバインディングを使用します。 信頼できるセッションは、コードまたは構成ファイルで宣言によって強制的に有効にすることができます。 この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションを有効にし、メッセージが送信された順序と同じ順序で到着することを指定します。

この手順の重要な部分は、エンドポイント構成要素に、 `bindingConfiguration` という名前のバインディング構成を参照する属性が含まれていることです `Binding1` 。 [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)構成要素は、要素の属性をに設定することによって、信頼できるセッションを有効にするために、この名前を参照し `enabled` [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` ます。 信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。

この例のソースコピーについては、「 [WS Reliable Session](../samples/ws-reliable-session.md)」を参照してください。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用するようにサービスを WSHttpBinding で構成する

1. サービスの種類にサービス コントラクトを定義します。

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. サービス クラスにサービス コントラクトを実装します。 サービスの実装内では、アドレスまたはバインド情報が指定されていないことに注意してください。 構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. *Web.config*ファイルを作成して、 `CalculatorService` <xref:System.ServiceModel.WSHttpBinding> 信頼できるセッションを有効にし、必要なメッセージの順次配送を使用するのエンドポイントを構成します。

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. 次の行を含む .svc ファイルを作成*し*ます。

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. サービスの *.svc*ファイルをインターネットインフォメーションサービス (IIS) 仮想ディレクトリに配置します。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用するようにクライアントを WSHttpBinding で構成する

1. コマンドラインから[ServiceModel メタデータユーティリティツール (*svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービスメタデータからコードを生成します。

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 生成されたクライアントには、 `ICalculator` クライアント実装が満たす必要のあるサービスコントラクトを定義するインターフェイスが含まれています。

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. 生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 サービスの実装内でアドレスおよびバインド情報が指定されていないことに注意してください。 構成ファイルからアドレスやバインド情報を取得するためのコードを記述する必要はありません。

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe*は、クラスを使用するクライアントの構成も生成します <xref:System.ServiceModel.WSHttpBinding> 。 Visual Studio を使用*する場合は*、構成ファイルに app.config という名前を指定します。

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. アプリケーションでのインスタンスを作成 `ClientCalculator` し、サービス操作を呼び出します。

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. クライアントをコンパイルして実行します。

## <a name="example"></a>例

システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。 これには以下が含まれます。

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

信頼できるセッションをサポートするカスタムバインディングを作成する方法の例については、「[方法: HTTPS を使用してカスタムの信頼できるセッションのバインディングを作成](how-to-create-a-custom-reliable-session-binding-with-https.md)する」を参照してください。

## <a name="see-also"></a>関連項目

- [信頼できるセッション](reliable-sessions.md)
