---
title: アクティビティ ID の伝達
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: 642d4da49f90d3fc6f2b0dfc9896d724acb075b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651815"
---
# <a name="activity-id-propagation"></a>アクティビティ ID の伝達
伝達は、ServiceModel アクティビティ トレースが有効な場合 (ServiceModel 伝達) または無効な場合 (ユーザーからユーザーへのアクティビティ伝達) に実行されます。  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>ServiceModel アクティビティ トレースが有効な場合  
 ServiceModel アクティビティ トレースが有効な場合、伝達は ProcessAction アクティビティ間で実行されます。  
  
### <a name="server"></a>サーバー  
 ときに、`propagateActivity`属性に設定されて`true`クライアントとサーバーの ID の両方で、 `ProcessAction` 、サーバーのアクティビティには、伝達された ID と同じですが`ActivityId`メッセージ ヘッダー。  
  
 ない場合`ActivityId`ヘッダーがメッセージに存在する (つまり、 `propagateActivity` = `false`クライアントで)、または`propagateActivity` = `false`サーバーをサーバーで、新しいアクティビティ ID を生成します  
  
### <a name="client"></a>クライアント  
 クライアントが同期的にシングル スレッドで動作する場合、クライアントは、クライアントまたはサーバー側で `propagateActivity` の設定を無視します。 代わりに、応答は要求アクティビティで処理されます。 クライアントが非同期または同期の場合、マルチ スレッド`propagateActivity` = `true`クライアントで、サーバーによって送信されたメッセージでアクティビティ ID ヘッダーがあると、クライアントが、メッセージからアクティビティ ID を取得し転送、Process Action アクティビティ伝達されたアクティビティ ID を含む それ以外の場合、クライアントは、"プロセス メッセージ" アクティビティから新しい "プロセス アクション" アクティビティに転送します。 この新しい "プロセス アクション" アクティビティへの転送は、整合性を維持するために行われます。 このアクティビティの内部で、クライアントは、スレッドが応答メッセージ処理用に割り当てられている場合、ローカル スレッド コンテキストから BeginCall アクティビティのアクティビティ ID を取得します。 その後、最初の "プロセス アクション" アクティビティに転送します。  
  
 クライアントが双方向の場合、クライアントは、メッセージを受信するときにサーバーとして機能します。  
  
### <a name="propagation-in-fault-messages"></a>エラー メッセージの伝達  
 有効なメッセージの処理とエラー メッセージの処理に違いはありません。 場合`propagateActivity` = `true`、SOAP エラー メッセージのヘッダーに追加されたアクティビティ ID は、アンビエント アクティビティと同じです。  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>ServiceModel アクティビティ トレースが無効な場合  
 ServiceModel アクティビティ トレースが無効な場合、伝達は、ServiceModel アクティビティを通過せずに直接ユーザー コード アクティビティ間で実行されます。 ユーザー定義のアクティビティ ID もメッセージ アクティビティ ID ヘッダーによって伝達されます。  
  
 場合`propagateActivity` = `true`と`ActivityTracing` = `off` (ServiceModel のトレースを有効かどうか) に関係なく、ServiceModel トレース リスナーの次にクライアントまたはサーバーのいずれかで発生します。  
  
- 要求の処理時または応答の送信時に、TLS のアクティビティ ID は、メッセージが作成されるまでユーザー コードの外部で伝達されます。 また、アクティビティ ID ヘッダーは、メッセージが送信される前にメッセージに挿入されます。  
  
- 要求の受信時または応答の受信時に、アクティビティ ID は、受信したメッセージのオブジェクトが作成されしだい、メッセージ ヘッダーから取得されます。 TLS のアクティビティ ID は、メッセージがスコープから消えるとすぐに、ユーザー コードに到達するまで伝達されます。  
  
 このアクションによって、伝達が有効な場合にユーザー トレースが同じアクティビティに表示されることが保証されます。 ただし、ServiceModel トレースに対する保証はありません。 ServiceModel トレースは、このトレースの処理がユーザー コード アクティビティが設定されたのと同じスレッドで実行される場合のみ、ユーザー コード アクティビティで実行されます。  
  
 通常、ServiceModel トレースは、次の場所で確認できます。  
  
- ServiceModel トレースが無効な場合、出力されたすべてのトレースは、ユーザー アクティビティに表示されます。 サーバーとクライアントの両方で伝達が有効な場合、このトレースは同じアクティビティに表示されます。  
  
- ServiceModel トレースが有効で、ActivityTracing が無効の場合、ユーザー トレースは、サーバーとクライアントの両方で伝達が有効な場合は同じアクティビティに表示されます。 ServiceModel トレースは、既定の 0000 アクティビティに表示されます。ただし、このトレースが、アクティビティが最初に設定されたユーザー コード処理と同じスレッドで実行される場合を除きます。  
  
- ServiceModel トレースと ActivityTracing が両方とも有効な場合、ユーザー トレースは、ユーザー定義のアクティビティに表示され、ServiceModel トレースは、ServiceModel 定義のアクティビティに表示されます。 伝達は、ServiceModel レベルで実行されます。
