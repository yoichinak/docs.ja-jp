---
title: カスタム エンコーダー
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 586207af0bfbe106512dfb61ee7439d4f5ce64c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797221"
---
# <a name="custom-encoders"></a>カスタム エンコーダー
このトピックでは、カスタム エンコーダーを作成する方法について説明します。  
  
 Windows Communication Foundation (WCF) では、*バインディング*を使用して、エンドポイント間でネットワーク経由でデータを転送する方法を指定します。 バインディングは、*バインド要素*のシーケンスで構成されます。 バインディングには、セキュリティ、必須の*メッセージエンコーダー*のバインド要素、必須のトランスポートバインド要素など、オプションのプロトコルバインド要素が含まれます。 メッセージ エンコーダーは、メッセージ エンコーディング バインド要素で表されます。 WCF には、次の3つのメッセージエンコーダーが含まれています。バイナリ、メッセージ伝送最適化メカニズム (MTOM)、テキスト。  
  
 メッセージ エンコーディング バインド要素は、送信する <xref:System.ServiceModel.Channels.Message> をシリアル化してそれをトランスポートに渡すか、シリアル化された形式のメッセージをトランスポートから受信して、それをプロトコル層 (ある場合) またはアプリケーション (プロトコル層がない場合) に渡します。  
  
 メッセージ エンコーダーは、<xref:System.ServiceModel.Channels.Message> インスタンスと物理メッセージ形式を相互に変換します。 エンコーダーは、チャネル スタックのトランスポート層の上に位置すると説明されていますが、トランスポート層の内部に存在します。 トランスポート (HTTP など) は、トランスポート標準の要件に従ってメッセージの書式設定を行います。 エンコーダー (テキスト XML など) は、単にメッセージのエンコードを行います。  
  
 既存のクライアントまたはサーバーに接続する場合、特定のメッセージ エンコーディングを使用する選択ができない場合があります。 ただし、WCF サービスは、それぞれが異なるメッセージエンコーダーを持つ複数のエンドポイントを介してアクセスできるようにすることができます。 1 つのエンコーダーでサービスの対象ユーザー全体を網羅しない場合、複数のエンドポイントにサービスを公開することを検討します。 これによりクライアント アプリケーションはそのアプリケーションに最も適したエンドポイントを選択できます。 複数のエンドポイントを使用することにより、さまざまなメッセージ エンコーダーの利点を他のバインド要素と組み合わせることが可能になります。  
  
## <a name="system-provided-encoders"></a>システム指定のエンコーダー  
 WCF には、最も一般的なアプリケーションシナリオに対応するように設計された、システム指定のバインディングがいくつか用意されています。 これらのバインディングは、それぞれトランスポート、メッセージ エンコーダー、その他のオプション (セキュリティなど) を組み合わせます。 このトピック`Text`では、WCF に含ま`Binary`れる、 `MTOM` 、およびメッセージエンコーダーを拡張する方法、または独自のカスタムエンコーダーを作成する方法について説明します。 テキスト メッセージ エンコーダーは、通常の XML のエンコーディングに加えて、SOAP のエンコーディングもサポートします。 テキスト メッセージ エンコーダーの通常の XML エンコーディング モードは、テキスト ベースの SOAP エンコーディングと区別するために、POX ("Plain Old XML") エンコーダーと呼ばれます。  
  
 システム指定のバインディングによって提供されるバインド要素の組み合わせの詳細については、「[トランスポートの選択](../feature-details/choosing-a-transport.md)」の対応するセクションを参照してください。  
  
## <a name="how-to-work-with-system-provided-encoders"></a>システム標準のエンコーダーの操作方法  
 エンコーディングは、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> からの派生クラスを使用してバインディングに追加します。  
  
 WCF には、テキスト、バイナリ、およびメッセージ伝送<xref:System.ServiceModel.Channels.MessageEncodingBindingElement>最適化機構 (MTOM) のエンコーディングに使用できるクラスから派生した次の種類のバインド要素が用意されています。  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>:最も相互運用が可能ですが、XML メッセージのエンコーダーは最も効率的ではありません。 Web サービスまたは Web サービス クライアントは、一般に、テキスト形式の XML を認識できます。 ただし、大きいブロックのバイナリ データをテキストとして転送するのは効率的ではありません。  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>:バイナリベースの XML メッセージに使用される文字エンコーディングおよびメッセージのバージョン管理を指定するバインド要素を表します。 これは、最も効率的なエンコードオプションですが、WCF エンドポイントでのみサポートされているため、相互運用性は最も少なくなります。  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>:メッセージ転送最適化機構 (MTOM) エンコーディングを使用して、メッセージに使用される文字エンコーディングおよびメッセージのバージョン管理を指定するバインド要素を表します。 MTOM は、WCF メッセージでバイナリ データを転送するための効率的なテクノロジです。 MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。 MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックはテキストに変換せずにそのまま転送することによって最適化します。  
  
 バインド要素は、バイナリ、MTOM、またはテキストの <xref:System.ServiceModel.Channels.MessageEncoderFactory> を作成します。 ファクトリは、バイナリ、MTOM、またはテキストの <xref:System.ServiceModel.Channels.MessageEncoderFactory> を作成します。 通常、インスタンスは 1 つだけあります。 ただし、セッションを使用すると、異なるエンコーダーを各セッションに提供できます。 バイナリ エンコーダーでは、これを利用して動的ディクショナリ (XML インフラストラクチャを参照) を調整します。  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> メソッドと <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> メソッドは、エンコーダーのコアです。 このメソッドは、ストリームまたは <xref:System.Byte> 配列からのメッセージの読み取りに対応します。 バイト配列は、トランスポートをバッファー モードで操作している場合に使用されます。 メッセージはストリームに常に書き込まれます。 トランスポートでメッセージをバッファーする必要がある場合は、バッファリングを行うストリームが提供されます。  
  
 残りのメンバーは、サポート コンテンツ、メディア タイプ、および <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A> を処理します。 トランスポートは、このエンコーダー メソッドを呼び出して、受信メッセージがデコード可能かどうかをテストするか、または送信メッセージがこのエンコーダーに対して有効かどうかを決定します。  
  
 3 つのそれぞれのエンコーダー実装は、特定のエンコーディングに関連するプロパティを追加し、完全に構成可能です。 また、エンコーダーは、安全な既定値を持つリーダーのクォータも公開しています。 クォータの詳細については、XML インフラストラクチャを参照してください。  
  
## <a name="features-of-system-provided-encoders"></a>システム標準のエンコーダーの機能  
 システム標準のエンコーダーは多くの機能を提供します。  
  
### <a name="pooling"></a>Pooling  
 各エンコーダー実装は、可能な限りプールを試みます。 マネージド コードのパフォーマンスを向上するには、割り当てを減らすことが重要です。 このプールを実現するには、実装で `SynchronizedPool` クラスを使用します。 C# ファイルには、このクラスで使用する追加の最適化に関する記述を含めます。  
  
 メッセージごとに新しい <xref:System.Xml.XmlDictionaryReader> および <xref:System.Xml.XmlDictionaryWriter> インスタンスを割り当てるのを避けるため、これらのインスタンスをプールして再初期化します。 リーダーについては、`OnClose` の呼び出し時に `Close()` コールバックでリーダーが再利用されます。 また、エンコーダーでは、メッセージを作成するときに使用するいくつかのメッセージ状態オブジェクトが再利用されます。 このプールのサイズは、`MaxReadPoolSize` から派生した 3 つの各クラスの `MaxWritePoolSize` プロパティと <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> プロパティによって構成可能です。  
  
### <a name="binary-encoding"></a>バイナリ エンコーディング  
 バイナリ エンコーディングでセッションを使用する場合、動的ディクショナリの文字列をメッセージの受信者と通信する必要があります。 これを行うには、メッセージのプレフィックスに動的ディクショナリの文字列を指定します。 受信側では、その文字列を取り除いて、セッションに追加し、メッセージ処理を行います。 ディクショナリの文字列を正しく渡すには、トランスポートをバッファーする必要があります。  
  
 文字列は、内部 `AddSessionInformationToMessage` メソッドによってメッセージに追加されます。 文字列は、メッセージの先頭に UTF-8 として追加され、その長さがプレフィックスに指定されます。 次にディクショナリ ヘッダー全体のプレフィックスにそのデータ長が指定されます。 内部 `ExtractSessionInformationFromMessage` メソッドにより逆操作が実行されます。  
  
 動的ディクショナリ キーの処理に加え、バッファーされセッションの多いメッセージが独自の方法で受信されます。 ドキュメントでリーダーを作成して処理する代わりに、バイナリ エンコーダーは、内部 `MessagePatterns` クラスを使用してバイナリ ストリームを分解します。 概念として、ほとんどのメッセージには、WCF によって生成されたときに特定の順序で表示される特定のヘッダーのセットがあります。 想定を基にしたパターン システムによりメッセージは分割されます。 成功した場合は、XML の解析を行わずに <xref:System.ServiceModel.Channels.MessageHeaders> オブジェクトを初期化します。 成功しなかった場合は、標準の方法に戻ります。  
  
### <a name="mtom-encoding"></a>MTOM エンコーディング  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> クラスには、<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A> という追加の構成プロパティがあります。 これには、メッセージ読み取り中にバッファーできるデータ量の上限が設けられています。 すべての MIME パートを 1 つのメッセージに再アセンブルするために、XML 情報セット (Infoset) または他の MIME パートをバッファーすることが必要な場合もあります。  
  
 HTTP を正しく操作するために、内部 MTOM メッセージ エンコーダーのクラスでは、`GetContentType` (内部) や `WriteMessage` (パブリックで、オーバーライド可能) の内部 API がいくつか用意されています。 HTTP ヘッダーの値を MIME ヘッダーの値と一致させるには、多くの通信を行う必要があります。  
  
 内部的には、MTOM メッセージエンコーダーは、WCF のテキストリーダーを使用します。これは、テキストエンコーダーに似ています。 主な違いは、Base-64 エンコーディングに変換せずにメッセージ バイトに埋め込むことで、大きいサイズのバイナリ (バイナリ ラージ オブジェクト (BLOB) と呼びます) を最適化する点です。 代わりに、この BLOB は抽出され、MIME 添付として参照されます。  
  
## <a name="writing-your-own-encoder"></a>独自のエンコーダーの作成  
 独自のカスタム メッセージ エンコーダーを実装するには、次の抽象基本クラスのカスタム実装を提供する必要があります。  
  
- <xref:System.ServiceModel.Channels.MessageEncoder>  
  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 メッセージのメモリ内表現からストリームに書き込むことのできる表現への変換は、 <xref:System.ServiceModel.Channels.MessageEncoder> クラスにカプセル化されており、このクラスは、特定の種類の XML エンコーディングをサポートする XML リーダーおよび XML ライターに対するファクトリとして機能します。  
  
- オーバーライドを必要とする、このクラスの主要なメソッドを次に示します。  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>。<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> オブジェクトを受け取り、それを <xref:System.IO.Stream> オブジェクトに書き込みます。  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>。<xref:System.IO.Stream> オブジェクトと最大ヘッダー サイズを受け取り、<xref:System.ServiceModel.Channels.Message> オブジェクトを返します。  
  
 これらのメソッドに記述するコードは、標準トランスポート プロトコルとカスタマイズしたエンコーディングの間の変換処理です。  
  
 次に、カスタム エンコーダーを作成するファクトリ クラスをコーディングする必要があります。 <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> をオーバーライドして、独自のカスタム <xref:System.ServiceModel.Channels.MessageEncoder> のインスタンスを返します。  
  
 次に、<xref:System.ServiceModel.Channels.MessageEncoderFactory> メソッドをオーバーライドしてこのファクトリのインスタンスを返すようにすることで、サービスまたはクライアントの構成に使用されるバインド要素スタックにカスタム <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> を接続します。  
  
 WCF には、このプロセスをサンプルコードと共に示す2つのサンプルが用意されています。[カスタムメッセージエンコーダー:カスタムテキストエンコーダー](../samples/custom-message-encoder-custom-text-encoder.md)と[カスタムメッセージエンコーダー:圧縮エンコーダー](../samples/custom-message-encoder-compression-encoder.md)。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [データ転送のアーキテクチャの概要](../feature-details/data-transfer-architectural-overview.md)
- [メッセージ エンコーダーを選択する](../feature-details/choosing-a-message-encoder.md)
- [トランスポートの選択](../feature-details/choosing-a-transport.md)
