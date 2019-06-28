---
title: HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 218887f7d09e234d0d02dfa1df5c1d4e114ddc11
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422240"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP、TCP、または名前付きパイプを使用した非同期シナリオ
ここでは、マルチスレッド要求で HTTP、TCP、または名前付きパイプを使用したときの、さまざまな非同期要求/応答シナリオでのアクティビティおよび転送について説明します。  
  
## <a name="asynchronous-requestreply-without-errors"></a>エラーを伴わない非同期要求/応答  
 ここでは、マルチスレッド クライアントを使用したときの、非同期要求/応答シナリオでのアクティビティおよび転送について説明します。  
  
 呼び出し元アクティビティは、`beginCall` が返され、`endCall` が返されると終了します。 コールバックが呼び出されたときは、そのコールバックが返されます。  
  
 呼び出されたアクティビティは、`beginCall` が返され、`endCall` が返されると終了します。または、そのアクティビティからコールバックが呼び出された場合は、コールバックが返されると終了します。  
  
### <a name="asynchronous-client-without-callback"></a>コールバックを伴わない非同期クライアント  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>HTTP を使用して、両方の側で伝達が有効になっている場合  
 ![PropagateActivity に設定されていないコールバックを伴う非同期クライアント両方の側では true。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 場合`propagateActivity=true`ProcessMessage は ProcessAction アクティビティへの転送を示します。  
  
 HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>HTTP を使用して、両方の側で伝達が無効になっている場合  
 場合`propagateActivity=false`いずれかの側では、ProcessMessage は示しませんアクティビティへの転送を示しません。 したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。 非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。 その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。  
  
 ![非同期クライアント propagateActivity を右辺でも左辺でも false に設定されているコールバックなし。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 HTTP ベースのシナリオでは、最初に送信するメッセージで "バイトを受信" が呼び出され、要求の有効期間だけ存在します。  
  
 プロセスのアクション アクティビティが、非同期クライアントで作成されたときに`propagateActivity=false`呼び出し元または呼び出し先、および応答メッセージに Action ヘッダーが含まれていない場合。  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>TCP または名前付きパイプを使用して、両方の側で伝達が有効になっている場合  
 ![非同期のクライアントにコールバックが propagateActivity が両方の側で true と名前付きに設定されていない/TCP パイプします。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。  
  
 最初の図のような場合`propagateActivity=true`ProcessMessage は ProcessAction アクティビティへの転送を示します。  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>TCP または名前付きパイプを使用して、両方の側で伝達が無効になっている場合  
 名前付きパイプまたは TCP ベースのシナリオでは、クライアントが開かれるときに "バイトを受信" が呼び出され、接続の有効期間だけ存在します。  
  
 2 番目の図のような場合は`propagateActivity=false`いずれかの側では、ProcessMessage は示しませんアクティビティへの転送を示しません。 したがって、新しい ID を使用して、新しい一時的な "アクションを処理" アクティビティが呼び出されます。 非同期応答と ServiceModel コード内の要求が一致する場合は、アクティビティ ID をローカル コンテキストから取得できます。 その ID を使用して、実際の "アクションを処理" アクティビティに転送できます。  
  
 ![非同期クライアント propagateActivity の右辺でも左辺でも false に設定し、パイプ/TCP という名前の場所、コールバックなし。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a>コールバックを伴う非同期クライアント  
 このシナリオでは、コールバックと `endCall` に対するアクティビティ G と A’、およびその転送 (送受信) が追加されています。  
  
 このセクションでは HTTP との使用方法を示しますのみ`propagateActivity` =`true`します。 ただし、それ以外の場合にも適用の他のアクティビティおよび転送 (つまり、 `propagateActivity` = `false`、TCP または名前付きパイプを使用して)。  
  
 クライアントがユーザー コードを呼び出して結果の準備が完了したことを通知すると、コールバックは新しいアクティビティ (G) を作成します。 ユーザー コードは、次に、コールバック内 (図 5 を参照) またはコールバック外 (図 6 を参照) で `endCall` を呼び出します。 どのユーザー アクティビティが不明なので`endCall`が呼び出されるから、このアクティビティがというラベルが付いた`A’`します。 A’ と A が同じである場合もありますし、異なる場合もあります。  
  
 ![非同期コールバック、コールバックで endcall でクライアントを示しています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![非同期コールバック、endcall コールバック外でクライアントを示しています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a>コールバックを伴う非同期サーバー  
 ![コールバックを伴う非同期サーバーを示しています。](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 チャネル スタックは、"メッセージを受信" でクライアントをコールバックします。この処理のトレースは、"要求を処理" アクティビティ自体で出力されます。  
  
## <a name="asynchronous-requestreply-with-errors"></a>エラーを伴う非同期要求/応答  
 エラー メッセージは、`endCall` 中に受信されます。 この点を除き、アクティビティおよび転送は前のシナリオと同様です。  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>エラーを伴う/伴わない非同期一方向要求/応答  
 クライアントに返される応答やエラーはありません。
