---
title: トランスポート クォータ
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: 12c266a473aa7c20ab35d6047fedafbfa04dac4a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299307"
---
# <a name="transport-quotas"></a>トランスポート クォータ
トランスポート クォータは、接続がリソースを過剰に消費している時期を特定するポリシー機構です。 クォータとは、クォータ値を超えた場合に、それ以上のリソースの使用を禁止する確実な制限です。 トランスポート クォータは、悪質な、または意図的でないサービス拒否攻撃を防ぎます。  
  
 Windows Communication Foundation (WCF) トランスポートでは、控えめなリソース割り当てに基づく既定クォータ値を指定します。 これらの既定値は開発環境、および小規模のインストール シナリオに適しています。 インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は、トランスポート クォータをレビューし、個別のクォータ値を調整する必要があります。  
  
## <a name="types-of-transport-quotas"></a>トランスポート クォータの種類  
 WCF トランスポートでは、次の 3 つの種類のクォータがあります。  
  
-   *タイムアウト*拒否一定の時間のリソースを停滞に依存するサービス拒否攻撃の緩和します。  
  
-   *メモリ割り当て制限*システム メモリの枯渇し、他の接続にサービスを拒否する 1 つの接続を防止します。  
  
-   *コレクション サイズの制限*間接的にメモリを割り当てまたは供給に制限されているリソースの消費量をバインドします。  
  
## <a name="transport-quota-descriptions"></a>トランスポート クォータの説明  
 このセクションには、標準の WCF トランスポートの使用可能なトランスポート クォータがについて説明します。HTTP (S)、TCP/IP、および名前付きパイプします。 カスタム トランスポートでは、このリストに含まれない独自の構成可能なクォータを公開できます。 カスタム トランスポートのクォータについては、ドキュメントを参照してください。  
  
 各クォータ設定では、種類、最小値、および既定値を設定します。 クォータの最大値は、クォータの種類によって制限されます。 コンピューターの制限により、クォータを最大値に設定できない場合もあります。  
  
|名前|型|最小<br /><br /> 値|既定値<br /><br /> 値|説明|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 目盛り|5 秒|最初の読み取り中に、接続が前文の送信を待機する最大時間。 このデータは、認証が行われる前に受信されます。 この設定は一般に、`ReceiveTimeout` クォータ値よりも大幅に小さな値になります。|  
|`CloseTimeout`|TimeSpan|0|1 分|接続の終了を待機する最大時間。これを超えるとトランスポートで例外が発生します。|  
|`ConnectionBufferSize`|整数型|1|8 KB|基となるトランスポートの送信および受信バッファーのサイズ (バイト単位)。 サイズの大きなメッセージを送信する場合、バッファー サイズを増やすとスループットを向上させることができます。|  
|`IdleTimeout`|TimeSpan|0|2 分|プールされた接続が閉じられるまで、アイドル状態を維持できる最大時間。<br /><br /> この設定はプールされた接続にのみ適用されます。|  
|`LeaseTimeout`|TimeSpan|0|5 分|プールされたアクティブな接続の最長有効期間。 指定した期間が経過すると、現在の要求の処理後、接続は閉じられます。<br /><br /> この設定はプールされた接続にのみ適用されます。|  
|`ListenBacklog`|整数型|1|10|リスナーで未処理にできる接続の最大数。エンドポイントへの接続がこれ以上増加すると拒否されます。|  
|`MaxBufferPoolSize`|Long|0|512 KB|トランスポートで再使用可能なメッセージ バッファーのプール専用にするメモリの最大値 (バイト単位)。 プールがメッセージ バッファーを供給できない場合、新しいバッファーが一時的な使用のために割り当てられます。<br /><br /> 多数のチャネル ファクトリまたはリスナーを作成するインストールでは、バッファー プールに多くのメモリが割り当てられることがあります。 このバッファー サイズを縮小すると、このシナリオにおけるメモリ使用量を大幅に削減できることがあります。|  
|`MaxBufferSize`|整数型|1|64 KB|ストリーミング データ用に使用されるバッファーの最大サイズ (バイト単位)。 このトランスポート クォータが設定されていない、またはトランスポートがストリーミングを使用しない場合、このクォータ値は `MaxReceivedMessageSize` クォータ値と <xref:System.Int32.MaxValue> の小さい方と同じになります。|  
|`MaxOutboundConnectionsPerEndpoint`|整数型|1|10|特定のエンドポイントに関連付けることのできる送信接続の最大数。<br /><br /> この設定はプールされた接続にのみ適用されます。|  
|`MaxOutputDelay`|TimeSpan|0|200 ミリ秒|送信操作後に 1 回の操作で追加メッセージをバッチ処理するために待機する最大時間。 基になるトランスポートのバッファーがいっぱいになると、メッセージはより早い時期に送信されます。 追加のメッセージの送信によって遅延時間がリセットされることはありません。|  
|`MaxPendingAccepts`|整数型|1|1|リスナーで待機状態にできるチャネルの受け入れの最大数。<br /><br /> 受け入れの完了と新しい受け入れの開始との間には、時間的な間隔があります。 このコレクション サイズを大きくすると、この時間間隔内に接続するクライアントが切断されるのを防ぎます。|  
|`MaxPendingConnections`|整数型|1|10|アプリケーションによる受け入れをリスナーで待機できる最大接続数。 このクォータ値を超過すると、新規の受信接続は受け入れられるのを待機せずに切断されます。<br /><br /> メッセージ セキュリティのような接続機能では、クライアントは複数の接続を開くことがあります。 このクォータ値を設定する場合、サービス管理者はこのような追加の接続も考慮する必要があります。|  
|`MaxReceivedMessageSize`|Long|1|64 KB|ヘッダーを含む、受信メッセージの最大サイズ (バイト単位)。これを超えるとトランスポートで例外が発生します。|  
|`OpenTimeout`|TimeSpan|0|1 分|接続の確立を待機する最大時間。これを超えるとトランスポートで例外が発生します。|  
|`ReceiveTimeout`|TimeSpan|0|10 分|読み取り操作の完了を待機する最大時間。これを超えるとトランスポートで例外が発生します。|  
|`SendTimeout`|Timespan|0|1 分|書き込み操作の完了を待機する最大時間。これを超えるとトランスポートで例外が発生します。|  
  
 トランスポート クォータ `MaxPendingConnections` および `MaxOutboundConnectionsPerEndpoint` は、バインディングまたは構成を使用して設定される場合には、`MaxConnections` トランスポート クォータと呼ばれる単一のクォータに結合されます。 これらのクォータ値を個別に設定できるのは、バインド要素に限られます。 `MaxConnections` トランスポート クォータでは、最小値と既定値が同じになります。  
  
## <a name="setting-transport-quotas"></a>トランスポート クォータの設定  
 トランスポート クォータは、トランスポート バインド要素、トランスポート バンディング、アプリケーション構成、またはホスト ポリシーを介して設定されます。 このドキュメントでは、ホスト ポリシーを介したトランスポートの設定については説明しません。 ホスト ポリシー クォータの設定については、基になるトランスポートのドキュメントを参照してください。 [構成の HTTP および HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) Http.sys ドライバーのクォータ設定について説明します。 HTTP、TCP/IP、および名前付きパイプの接続で Windows の制限を構成する詳細については、マイクロソフト サポート技術情報を検索してください。  
  
 他の種類のクォータは、トランスポートへ間接的に適用されます。 トランスポートがメッセージをバイトに変換するために使用するメッセージ エンコーダーには、独自のクォータ設定があります。 ただし、これらのクォータは使用されているトランスポートの種類に依存しません。  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>バインド要素によるトランスポート クォータの制御  
 バインド要素を介してトランスポート クォータを設定した場合、トランスポートの動作を最も柔軟に制御できます。 閉じる、開く、受信、送信の各操作の既定のタイムアウトは、チャネルを構築したときにバインディングから設定されます。  
  
|名前|HTTP|TCP/IP|名前付きパイプ|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||x|x|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||x|x|  
|`IdleTimeout`||x|x|  
|`LeaseTimeout`||x||  
|`ListenBacklog`||x||  
|`MaxBufferPoolSize`|x|x|x|  
|`MaxBufferSize`|x|x|x|  
|`MaxOutboundConnectionsPerEndpoint`||x|x|  
|`MaxOutputDelay`||x|x|  
|`MaxPendingAccepts`||x|x|  
|`MaxPendingConnections`||x|x|  
|`MaxReceivedMessageSize`|x|x|x|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>バインディングによるトランスポート クォータの制御  
 バインディングによるトランスポート クォータの設定では、選択対象のクォータがセットにまとめられます。ただし、最も一般的に使用するクォータ値にはアクセスできます。  
  
|名前|HTTP|TCP/IP|名前付きパイプ|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|x|x|x|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||x||  
|`MaxBufferPoolSize`|x|x|x|  
|`MaxBufferSize`|1|x|x|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|x|x|x|  
|`OpenTimeout`|x|x|x|  
|`ReceiveTimeout`|x|x|x|  
|`SendTimeout`|x|x|x|  
  
1. `MaxBufferSize` トランスポート クォータは、`BasicHttp` バインディングでのみ使用可能です。 `WSHttp` バインディングは、ストリーミング トランスポート モードがサポートされないシナリオに対応します。  
  
2. トランスポート クォータ `MaxPendingConnections` および `MaxOutboundConnectionsPerEndpoint` は、`MaxConnections` トランスポート クォータと呼ばれる単一のクォータに結合されます。  
  
### <a name="controlling-transport-quotas-from-configuration"></a>構成によるトランスポート クォータの制御  
 アプリケーション構成からバインディング上のプロパティに直接アクセスして、同じトランスポート クォータを設定できます。 構成ファイルでは、トランスポート クォータの名前は必ず小文字で始めます。 たとえば、バインディングの `CloseTimeout` プロパティは構成では `closeTimeout` 設定に対応し、バインディングの `MaxConnections` プロパティは構成では `maxConnections` 設定に対応します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
