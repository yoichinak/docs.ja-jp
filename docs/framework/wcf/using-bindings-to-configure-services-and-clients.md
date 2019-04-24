---
title: サービスとクライアントを構成するためのバインディングの使用
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 3b4f00617418d5f84a0da5d0e531e1f671b58bb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323149"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>サービスとクライアントを構成するためのバインディングの使用
バインディングとは、エンドポイントへの接続に必要な通信の詳細設定を指定するオブジェクトです。 具体的には、バインディングには構成情報が含まれており、この情報を使用してそれぞれのエンドポイントまたはクライアント チャネルで使用されるトランスポート仕様、ワイヤ形式 (メッセージ エンコード) 仕様、プロトコル仕様が定義され、クライアントまたはサービスのランタイムが作成されます。 機能している Windows Communication Foundation (WCF) サービスを作成するには、サービス内の各エンドポイントにバインディングが必要です。 ここでは、エンドポイントにおけるバインディングの概要と定義方法、特定のバインディングの指定方法を説明します。  
  
## <a name="what-a-binding-defines"></a>バインディングの定義内容  
 バインディングの情報は、非常に基本的な情報にすることも複雑なものにすることもできます。 最も基本的なバインディングはトランスポート プロトコル (HTTP など) のみを指定したもので、これはエンドポイントへの接続に必ず使用します。 一般的に、バインディングに含まれるエンドポイントへの接続方法を示す情報は、次のカテゴリのいずれかに当てはまります。  
  
 プロトコル  
 使用されているセキュリティ機構 (信頼性の高いメッセージング機能またはトランザクション コンテキストのフロー設定のいずれか) を決定します。  
  
 Transport  
 使用する基本のトランスポート プロトコル (TCP や HTTP など) を決定します。  
  
 エンコード  
 メッセージ エンコード (Text/XML、バイナリ、MTOM (Message Transmission Optimization Mechanism) など) を決定します。これは、メッセージをネットワーク上のバイト ストリームとしてどのように表現するかを決定します。  
  
## <a name="system-provided-bindings"></a>システム標準のバインディング  
 WCF には、ほとんどのアプリケーションの要件とシナリオをカバーするように設計されたシステム指定のバインディングのセットが含まれています。 システム指定のバインディングの例のいくつかを次のクラスで示します。  
  
-   <xref:System.ServiceModel.BasicHttpBinding>:WS に準拠している HTTP プロトコル バインディング Web サービスに接続するのに適した-Basic Profile 1.1 仕様 (たとえば、ASP.NET Web サービス (ASMX)-ベースのサービス)。  
  
-   <xref:System.ServiceModel.WSHttpBinding>:HTTP プロトコル バインディングを Web に準拠するエンドポイントに接続するために適したサービス仕様のプロトコルです。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>:.NET binary エンコードとフレーム技術と組み合わせてを名前付きパイプ トランスポートの Windows でを使用して、同じコンピューター上の他の WCF エンドポイントに接続します。  
  
-   <xref:System.ServiceModel.NetMsmqBinding>:.NET binary エンコードとフレーム メッセージ キュー (MSMQ とも呼ばれます) と組み合わせて技術を使用して、他の WCF エンドポイントとメッセージをキューに置かれた接続を作成します。  
  
 詳細についてで、システム指定のバインディングの完全な一覧を参照してください。 [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)します。  
  
## <a name="custom-bindings"></a>カスタム バインディング  
 システム指定のバインディング コレクションに、サービス アプリケーションに必要な機能の適切な組み合わせが含まれていない場合は、<xref:System.ServiceModel.Channels.CustomBinding> バインディングを作成できます。 要素の詳細については、<xref:System.ServiceModel.Channels.CustomBinding>バインドを参照してください[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)と[カスタム バインド](../../../docs/framework/wcf/extending/custom-bindings.md)します。  
  
## <a name="using-bindings"></a>バインディングの使用  
 バインディングを使用する際には、次の 2 つの基本手順があります。  
  
1. バインディングを選択、または定義します。 最も簡単な方法は、システム指定のバインディングを 1 つ選択し、それを既定の設定で使用することです。 また、システム指定のバインディングを選択し、そのプロパティを要件に適した値に再設定することもできます。 さらに、カスタム バインドを作成し、すべてのプロパティを必要に応じて設定することもできます。  
  
2. このバインディングを使用するエンドポイントを作成します。  
  
## <a name="code-and-configuration"></a>コードおよび構成  
 バインディングは、コードまたは構成を使用して定義または構成できます。 この 2 つの方法は使用するバインディングの種類に依存しません。たとえば、システム指定のバインディングまたは <xref:System.ServiceModel.Channels.CustomBinding> バインディングのどちらを使用していても関係ありません。 一般に、コードを使用すると、コンパイル時に開発者がバインディングの定義を完全に制御できます。 システム管理者または WCF サービスまたはクライアントのバインディングのパラメーターを変更するユーザーは、その一方で、構成を使用しています。 特定のマシンの要件を予測し、ネットワークの状態は、WCF アプリケーションの展開方法がないために、このような柔軟性が望ましい多くの場合。 バインディング (およびアドレス) 情報がコードから分離されているため、管理者はアプリケーションの再コンパイルや再配置を行わずにバインディングの詳細を変更できます。 バインディングをコードに定義した場合、構成ファイルに記述されている構成ベースの定義はすべて上書きされます。 この方法についての例は、以下のトピックを参照してください。  
  
-   [方法: マネージ アプリケーションで WCF サービスをホスト](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)コードでバインディングの作成の例を示します。  
  
-   [チュートリアル: Windows Communication Foundation クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)の構成を使用してクライアントを作成する例を示します。  
  
## <a name="see-also"></a>関連項目

- [エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [方法: 構成でサービス バインディングを指定します。](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [方法: コードでのサービス バインドを指定します。](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [方法: 構成でクライアント バインディングを指定します。](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [方法: コードでクライアント バインディングを指定します。](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
