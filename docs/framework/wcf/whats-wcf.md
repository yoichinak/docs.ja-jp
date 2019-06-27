---
title: Windows Communication Foundation とは
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 37e12c499b19d196dd695e1e2970d750f4dc9b0e
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402425"
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation とは
Windows Communication Foundation (WCF) は、サービス指向アプリケーションを構築するためのフレームワークです。 WCF を使用して、できるデータを送信する非同期メッセージとして 1 つのサービス エンドポイントから別です。 サービス エンドポイントには、IIS でホストされている、継続的に使用可能なサービスの一部を使用したり、アプリケーションでホストされているサービスを使用できます。 エンドポイントには、サービス エンドポイントからデータを要求するサービスのクライアントを使用できます。 メッセージは XML として送信された 1 文字または 1 語の簡単なものでも、バイナリ データのストリームのような複雑なものでも構いません。 サンプル シナリオをいくつか挙げます。

- ビジネス トランザクションを処理するセキュリティ保護サービス。

- トラフィック レポートやその他のモニタリング サービスなど、現在のデータを他のサービスに提供するサービス。

- 2 人のユーザーがリアル タイムで通信したりデータを交換したりできるチャット サービス。

- データの 1 つ以上のサービスをポーリングし、論理プレゼンテーションで表示するダッシュボード アプリケーション。

- Windows Workflow Foundation を WCF サービスに使用した、実装されたワークフローの公開。

- 最新のデータ フィードのサービスをポーリングする Silverlight アプリケーション。

このようなアプリケーションを作成すると、WCF の存在の前に考えられるが、WCF、エンドポイントの開発より簡単になります。 要約すると、Web サービスと Web サービス クライアントを作成して管理しやすいアプローチを提供する WCF が設計されています。

## <a name="features-of-wcf"></a>WCF の機能

WCF には、次の機能セットが含まれています。 詳細については、次を参照してください。 [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)します。

- **サービス指向**

     WS 標準を使用して 1 つの結果では、WCF には作成することができるように*サービス指向*アプリケーション。 サービス指向アーキテクチャ (SOA) は、データの送受信に Web サービスを使用します。 このサービスを使用する一般的な長所は、1 つのアプリケーションから別のアプリケーションへハードコーディングせずに、疎結合にできるということです。 疎結合リレーションシップでは、必須のコントラクトが一致していれば、任意のプラットフォームで作成した任意のクライアントを任意のサービスに接続できます。

- **相互運用性**

     WCF では、Web サービス相互運用性の最新の業界標準を実装します。 サポートされている標準の詳細については、次を参照してください。[相互運用性と統合](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)します。

- **複数のメッセージ パターン**

     メッセージは複数のパターンの 1 つを使用して交換されます。 最も一般的なパターンは要求/応答パターンです。このパターンでは 1 つのエンドポイントが 2 番目のエンドポイントからデータを要求し、 2 番目のエンドポイントが応答します。 その他にも一方向のメッセージなどのパターンがあります。一方向のメッセージでは、1 つのエンドポイントが応答を期待せずにメッセージを送信します。 より複雑なパターンとして、2 つのエンドポイントが接続を確立し、インスタント メッセージング プログラムのようにデータをやり取りする双方向交換パターンがあります。 WCF を使用してパターンを異なるメッセージ交換を実装する方法の詳細について参照してください[コントラクト](../../../docs/framework/wcf/feature-details/contracts.md)します。

- **サービス メタデータ**

     WCF では、WSDL、XML スキーマ、Ws-policy などの業界標準で指定された形式を使用してサービス メタデータの公開をサポートします。 このメタデータは、自動的に生成し、WCF サービスにアクセスするためのクライアントの構成に使用できます。 メタデータは HTTP や HTTPS 上で、または Web サービス メタデータ交換標準を使用して公開できます。 詳細については、次を参照してください。[メタデータ](../../../docs/framework/wcf/feature-details/metadata.md)します。

- **データ コントラクト**

     WCF を .NET Framework を使用してビルドするため、適用するコントラクトを指定するコードに対応したメソッドもあります。 汎用的な型のコントラクトの 1 つにデータ コントラクトがあります。 本質的に、Visual C# または Visual Basic を使用してサービスをコード化した場合、データを処理する最も簡単な方法は、データ エンティティを表すクラスにデータ エンティティに属するプロパティを作成する方法です。 WCF には、この簡単な方法でデータを操作するための包括的なシステムが含まれています。 データを表すクラスを作成すると、設計したデータ型にクライアントが準拠できるメタデータがサービスによって自動生成されます。 詳細については、「[データ コントラクトの使用](../../../docs/framework/wcf/feature-details/using-data-contracts.md)」を参照してください。

- **セキュリティ**

     メッセージを暗号化してプライバシーを保護し、メッセージを受信する前にユーザーが自身を認証することを必須化することができます。 SSL や WS-SecureConversation などよく知られた標準を使用してセキュリティを実装できます。 詳細については、[セキュリティ](../../../docs/framework/wcf/feature-details/security.md)に関するページをご覧ください。

- **複数のトランスポートとエンコーディング**

     メッセージは複数の組み込みトランスポート プロトコルおよびエンコーディングのいずれかを使用して送信できます。 最も一般的なプロトコルとエンコーディングではエンコードされた World Wide Web 上で使用するためのハイパー テキスト転送プロトコル (HTTP) を使用して SOAP メッセージのテキストを送信します。 また、WCF に名前付きパイプ、または MSMQ を使用 TCP 経由でメッセージを送信することができます。 これらのメッセージはテキストとしてエンコードするか、最適化されたバイナリ形式を使用することができます。  バイナリ データは MTOM 標準を使用することで効率的に送信できます。 提供されているトランスポートまたはエンコーディングのいずれもニーズを満たさない場合は、独自のカスタム トランスポートまたはエンコーディングを作成できます。 トランスポートと WCF でサポートされているエンコーディングの詳細については、次を参照してください。[トランスポート](../../../docs/framework/wcf/feature-details/transports.md)します。

- **キューに置かれた信頼性のあるメッセージ**

     WCF では、Ws-reliable Messaging 経由で実装され、MSMQ を使用して、信頼できるセッションを使用した信頼性の高いメッセージ交換をサポートします。 WCF で信頼性が高く、キューに置かれたメッセージングのサポートの詳細については、次を参照してください。 [Queues and Reliable Sessions](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)します。

- **非揮発性メッセージ**

     非揮発性メッセージは、通信の中断によって失われることがないメッセージです。 非揮発性メッセージ パターンのメッセージは常にデータベースに保存されます。 中断が発生した場合、接続復旧時にデータベースでメッセージの交換を再開できます。 Windows Workflow Foundation (WF) を使用して永続的なメッセージを作成することもできます。 詳細については、次を参照してください。[ワークフロー サービス](../../../docs/framework/wcf/feature-details/workflow-services.md)します。

- **トランザクション**

     WCF には、次の 3 つのトランザクション モデルのいずれかを使用したトランザクションもサポートしています。Ws-atomicttransactions、Api、<xref:System.Transactions>名前空間、および Microsoft 分散トランザクション コーディネーターです。 詳細については、トランザクションは WCF でのサポートを参照してください[トランザクション](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)です。

- **AJAX および REST サポート**

     REST は、進化し続ける Web 2.0 テクノロジの一例です。 WCF は、SOAP エンベロープにラップされていない「書式なし」の XML データ処理を構成できます。 ATOM (一般的な RSS 標準)、および JavaScript Object Notation (JSON) など、非 XML 形式でもなどの特定の XML 形式をサポートするために WCF を拡張することもできます。

- **機能拡張**

     WCF アーキテクチャには、さまざまな機能拡張ポイントがあります。 追加の機能が必要になった場合、サービスの動作をカスタマイズできる多数のエントリ ポイントがあります。 使用可能な機能拡張の詳細についてはについては、「 [WCF の拡張](../../../docs/framework/wcf/extending/index.md)します。

## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF と他のマイクロソフト テクノロジと統合

WCF は、柔軟なプラットフォームです。 この柔軟性を活かして WCF も他のいくつかのマイクロソフト製品で使用されます。 WCF の基本を理解することでもこれらの製品を使用する場合、直接的なメリットがあります。

WCF とペアにする最初のテクノロジは、Windows Workflow Foundation (WF) でした。 ワークフロー「アクティビティ」として、ワークフローの手順をカプセル化するアプリケーションの開発を簡略化します。 最初のバージョンの Windows Workflow Foundation では、開発者は、ワークフローのホストを作成する必要があります。 Windows Workflow Foundation の次のバージョンは、WCF と統合されました。 任意のワークフローを簡単に WCF サービスでホストを許可されているとします。 Visual Studio 2012 またはそれ以降は、WF と WCF プロジェクトの種類を自動的に選択して、これを行うことができます。

また、Microsoft BizTalk Server R2 は、通信テクノロジとして WCF を利用します。 BizTalk は、1 つの標準化形式のデータを受け取り、別の形式に変換するように設計されています。 メッセージは、厳密なマッピングか、またはワークフロー エンジンなどの BizTalk 機能の 1 つを使用してメッセージを変換できる、中央管理のメッセージ ボックスに配信する必要があります。 BizTalk では、メッセージ ボックスにメッセージを配信するのに WCF 基幹業務 (LOB) アダプターを使用できます。

Microsoft Silverlight は開発者がストリーミング ビデオなどメディアを多用する Web サイトを作成できる、相互運用が可能で充実した Web アプリケーションを作成するためのプラットフォームです。 以降のバージョン 2 では、Silverlight は silverlight の WCF エンドポイントを接続する通信技術として WCF を組み込まいます。

アプリケーション サーバーの Windows Server AppFabric のホスティング機能は具体的には、展開、および WCF の通信を使用してアプリケーションを管理するために設計されています。 ホストの機能には、WCF 対応アプリケーション向けに設計の豊富なツールと構成オプションが含まれます。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel>
- [Windows Communication Foundation の基本概念](../../../docs/framework/wcf/fundamental-concepts.md)
- [Windows Communication Foundation のアーキテクチャ](../../../docs/framework/wcf/architecture.md)
- [ガイドラインとベスト プラクティス](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)
- [ドキュメントのガイド](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Communication Foundation サンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)
