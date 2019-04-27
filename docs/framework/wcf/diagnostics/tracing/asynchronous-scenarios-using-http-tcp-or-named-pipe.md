---
title: HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: d08f70186a59b8717c4441167ee720ba1c20b9dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998291"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ここでは、マルチスレッド要求で HTTP、TCP、または名前付きパイプを使用したときの、さまざまな非同期要求/応答シナリオでのアクティビティおよび転送について説明します。  
  
## <a name="asynchronous-requestreply-without-errors"></a>エラーを伴わない非同期要求/応答  
 ここでは、マルチスレッド クライアントを使用したときの、非同期要求/応答シナリオでのアクティビティおよび転送について説明します。  
  
 呼び出し元アクティビティは、`beginCall` が返され、`endCall` が返されると終了します。 コールバックが呼び出されたときは、そのコールバックが返されます。  
  
 呼び出されたアクティビティは、`beginCall` が返され、`endCall` が返されると終了します。または、そのアクティビティからコールバックが呼び出された場合は、コールバックが返されると終了します。  
  
### <a name="asynchronous-client-without-callback"></a>コールバックを伴わない非同期クライアント  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>HTTP を使用して、両方の側で伝達が有効になっている場合  
 ![非同期シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 図 1. 非同期クライアント、コールバックなし、 `propagateActivity` = `true`両方の側では、HTTP で  
  
 場合`propagateActivity` = `true`ProcessMessage は ProcessAction アクティビティへの転送を示します。  
  
 HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>HTTP を使用して、両方の側で伝達が無効になっている場合  
 場合`propagateActivity` = `false`いずれかの側では、ProcessMessage は示しませんアクティビティへの転送を示しません。 したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。 非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。 その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。  
  
 ![HTTP を使用した非同期シナリオ&#47;TCP&#47;名前付きパイプ](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 図 2. 非同期クライアント、コールバックなし、 `propagateActivity` = `false`右辺でも左辺でも、HTTP  
  
 HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。  
  
 プロセスのアクション アクティビティが、非同期クライアントで作成されたときに`propagateActivity` = `false`呼び出し元または呼び出し先、および応答メッセージに Action ヘッダーが含まれていない場合。  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>TCP または名前付きパイプを使用して、両方の側で伝達が有効になっている場合  
 ![HTTP を使用した非同期シナリオ&#47;TCP&#47;名前付きパイプ](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 図 3. 非同期クライアント、コールバックなし、 `propagateActivity` = `true`で両方の側では、名前付きパイプ/TCP  
  
 名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。  
  
 場合 1 を図のような`propagateActivity` = `true`ProcessMessage は ProcessAction アクティビティへの転送を示します。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>TCP または名前付きパイプを使用して、両方の側で伝達が無効になっている場合  
 名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。  
  
 図 2 では、ような場合`propagateActivity` = `false`いずれかの側では、ProcessMessage は示しません ProcessAction アクティビティに転送します。 したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。 非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。 その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。  
  
 ![HTTP を使用した非同期シナリオ&#47;TCP&#47;名前付きパイプ](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 図 4。 非同期クライアント、コールバックなし、 `propagateActivity` = `false`右辺でも左辺でも、名前付きパイプ/TCP  
  
### <a name="asynchronous-client-with-callback"></a>コールバックを伴う非同期クライアント  
 このシナリオでは、コールバックと `endCall` に対するアクティビティ G と A’、およびその転送 (送受信) が追加されています。  
  
 このセクションでは HTTP との使用方法を示しますのみ`propragateActivity` =`true`します。 ただし、それ以外の場合にも適用の他のアクティビティおよび転送 (つまり、 `propagateActivity` = `false`、TCP または名前付きパイプを使用して)。  
  
 クライアントがユーザー コードを呼び出して結果の準備が完了したことを通知すると、コールバックは新しいアクティビティ (G) を作成します。 ユーザー コードは、次に、コールバック内 (図 5 を参照) またはコールバック外 (図 6 を参照) で `endCall` を呼び出します。 どのユーザー アクティビティが不明なので`endCall`が呼び出されるから、このアクティビティがというラベルが付いた`A’`します。 A’ と A が同じである場合もありますし、異なる場合もあります。  
  
 ![非同期シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 図 5。 非同期クライアント、コールバックあり、コールバック内での `endCall`  
  
 ![非同期シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 図 6。 非同期クライアント、コールバックあり、コールバック外での `endCall`  
  
### <a name="asynchronous-server-with-callback"></a>コールバックを伴う非同期サーバー  
 ![HTTP を使用した非同期シナリオ&#47;TCP&#47;名前付き&#45;パイプ](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 図 7。 非同期サーバー、コールバックあり  
  
 チャネル スタックは、"メッセージを受信" でクライアントをコールバックします。この処理のトレースは、"要求を処理" アクティビティ自体で出力されます。  
  
## <a name="asynchronous-requestreply-with-errors"></a>エラーを伴う非同期要求/応答  
 エラー メッセージは、`endCall` 中に受信されます。 この点を除き、アクティビティおよび転送は前のシナリオと同様です。  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>エラーを伴う/伴わない非同期一方向要求/応答  
 クライアントに返される応答やエラーはありません。
