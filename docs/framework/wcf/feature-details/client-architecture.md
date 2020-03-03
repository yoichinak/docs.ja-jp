---
title: クライアント アーキテクチャ
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 6ed00054de45abc23fdd9ad69f61c758f567b973
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656057"
---
# <a name="client-architecture"></a>クライアント アーキテクチャ
アプリケーションでは、Windows Communication Foundation (WCF) クライアント オブジェクトを使用して、サービス操作を呼び出します。 このトピックでは、WCF クライアント オブジェクト、WCF クライアント チャネル、およびそれらの関係を基になるチャネル アーキテクチャについて説明します。 WCF クライアント オブジェクトの基本的な概要については、次を参照してください。 [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)します。 チャネル レイヤーの詳細については、次を参照してください。[チャネル レイヤーの拡張](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)します。  
  
## <a name="overview"></a>概要  
 サービス モデル ランタイムは、次の構成される WCF クライアントを作成します。  
  
- 自動的に生成される、サービス コントラクトのクライアント実装。これは、アプリケーション コードからの呼び出しを送信メッセージに変換すると共に、応答メッセージを出力パラメーターに変換して、アプリケーションが取得できる値を返します。  
  
- コントロール インターフェイス (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>) の実装。これは、さまざまなインターフェイスをグループ化し、コントロールの機能 (特に、クライアント セッションの終了機能とチャネルの破棄機能) へのアクセスを提供します。  
  
- クライアント チャネル。これは、使用するバインディングによって指定される構成設定に基づいて構築されます。  
  
 アプリケーションはオンデマンドで使用するかこのようなクライアントを作成することができます、<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>またはのインスタンスを作成して、<xref:System.ServiceModel.ClientBase%601>によって生成されるクラスを派生、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 これらの作成済みのクライアント クラスは、<xref:System.ServiceModel.ChannelFactory> によって動的に構築されるクライアント チャネル実装にカプセル化され、処理が代行されます。 したがって、クライアント チャネルと、クライアント チャネルを生成するチャネル ファクトリが、このトピックの説明の中心となります。  
  
## <a name="client-objects-and-client-channels"></a>クライアント オブジェクトとクライアント チャネル  
 WCF クライアントの基本インターフェイスは、<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>インターフェイス、クライアントのコア機能と同様の基本的な通信オブジェクト機能を公開する<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>のコンテキスト機能<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>との拡張可能な動作<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 ただし、<xref:System.ServiceModel.IClientChannel> インターフェイスではサービス コントラクトそのものは定義しません。 サービス コントラクト インターフェイスによって宣言されます (通常のようなツールを使用してサービス メタデータから生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md))。 WCF クライアントの種類は、両方を拡張<xref:System.ServiceModel.IClientChannel>とクライアント側のランタイム機能にも、直接操作を呼び出すアプリケーションを有効にするには、ターゲット サービス コントラクト インターフェイスにアクセスします。 WCF は、WCF クライアントの作成<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>接続を構成済みのサービス エンドポイントと対話できる実行時に作成するために必要な情報を持つオブジェクト。  
  
 前述のように、使用する前に、2 つの WCF クライアントの種類を構成する必要があります。 最も簡単な WCF クライアントの種類はから派生したオブジェクト<xref:System.ServiceModel.ClientBase%601>(または<xref:System.ServiceModel.DuplexClientBase%601>サービス コントラクトが双方向コントラクトの場合)。 これらのクライアント型はコンストラクターを使用して作成し、プログラムで構成するか、または構成ファイルを使用して構成します。また、サービス操作を呼び出すために直接呼び出されます。 基本的な概要の<xref:System.ServiceModel.ClientBase%601>、オブジェクトを参照してください[WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)します。  
  
 2 番目のクライアント型は、実行時に <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> メソッドへの呼び出しから生成されます。 通常、通信の詳細厳格に制御を必要があるアプリケーションと呼ばれるこのクライアントの種類を使用して、*クライアント チャネル オブジェクト*基になるクライアント ランタイムとチャネルより直接的な対話を有効になるので、システム。  
  
## <a name="channel-factories"></a>チャネル ファクトリ  
 クライアント呼び出しをサポートする、基になるランタイムを作成するクラスは、<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> クラスです。 WCF クライアント オブジェクトと WCF クライアント チャネル オブジェクトの使用、 <xref:System.ServiceModel.ChannelFactory%601> ; のインスタンスを作成するオブジェクト、<xref:System.ServiceModel.ClientBase%601>派生クライアント オブジェクトには、チャネル ファクトリの処理がカプセル化しますが、多くのシナリオは、使用することをお勧めしますチャネル ファクトリで直接使用します。 よくあるシナリオとしては、既存のファクトリから新しいクライアント チャネルを繰り返し作成する必要がある場合です。 クライアント オブジェクトを使用している場合、WCF クライアント オブジェクトからの基になるチャネル ファクトリする取得呼び出すことによって、<xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType>プロパティ。  
  
 チャネル ファクトリに関して覚えておく必要のある重要なことは、これらのファクトリが、<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> を呼び出す前に、指定されている構成のクライアント チャネルの新しいインスタンスを作成するという点です。 呼び出す<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>(または<xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>、 <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>、または WCF クライアント オブジェクトのすべての操作)、チャネル ファクトリを変更し、さまざまなサービスのインスタンスへのチャネルを取得する場合でも、ターゲットのエンドポイント アドレスを変更するだけでに予想されることはできません。 異なる構成でクライアント オブジェクトやクライアント チャネルを作成するには、まず新しいチャネル ファクトリを作成する必要があります。  
  
 WCF クライアント オブジェクトと WCF クライアント チャネルを使用してさまざまな問題の詳細については、次を参照してください。[にアクセスするサービスの WCF クライアントを使用して](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)します。  
  
 次の 2 つのセクションでは、作成と WCF クライアント チャネル オブジェクトの使用について説明します。  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>新しい WCF クライアント チャネル オブジェクトの作成  
 次のサービス コントラクトが生成されていることを前提に、クライアント チャネルの使用方法を説明します。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 `ISampleService` サービスに接続するには、チャネル ファクトリ (<xref:System.ServiceModel.ChannelFactory%601>) を直接使用して生成したコントラクト インターフェイスを使用します。 特定のコントラクトのチャネル ファクトリを作成して構成した後は、<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> メソッドを呼び出して、`ISampleService` サービスとの通信に使用できるクライアント チャネル オブジェクトを返すことができます。  
  
 サービス コントラクト インターフェイスで <xref:System.ServiceModel.ChannelFactory%601> クラスを使用する場合、明示的にチャネルを開いたり、閉じたり、中止したりするには、<xref:System.ServiceModel.IClientChannel> インターフェイスにキャストする必要があります。 処理を容易にするために、Svcutil.exe ツールでは、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel> の両方を実装するヘルパー インターフェイスも生成されます。これにより、キャストを行わずにクライアント チャネル インフラストラクチャとのやりとりを実現できます。 上記のサービス コントラクトを実装するヘルパー クライアント チャネルの定義を、次のコード例に示します。  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>新しい WCF クライアント チャネル オブジェクトの作成  
 クライアント チャネルを使用して `ISampleService` サービスに接続するには、チャネル ファクトリを直接使用して生成したコントラクト インターフェイス (またはヘルパー バージョン) を使用して、コントラクト インターフェイスの型を型パラメーターとして渡します。 特定のコントラクトのチャネル ファクトリを作成して構成したら、<xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> メソッドを呼び出して、`ISampleService` サービスとの通信に使用できるクライアント チャネル オブジェクトを返すことができます。  
  
 作成したクライアント チャネル オブジェクトで <xref:System.ServiceModel.IClientChannel> とコントラクト インターフェイスを実装します。 その結果、これらを使用して、このコントラクトをサポートするサービスと対話する操作を直接呼び出すことができます。  
  
 クライアント オブジェクトを使用するかクライアント チャネル オブジェクトを使用するかは、開発者がきめ細かな制御を優先するか容易さを優先するかの違いだけです。 WCF クライアント チャネルではなく、WCF クライアント オブジェクトを使用するクラスとオブジェクトの使用を使い慣れている多くの開発者が優先されます。  
  
 例については、「[方法: ChannelFactory を使用して、](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)します。
