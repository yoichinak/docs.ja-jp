---
title: エンドポイント:1 秒あたりのセキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: a6d76a0d11c52d20aebd44a85862c802cc0a68f7
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912477"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>エンドポイント:1 秒あたりのセキュリティ検証と認証エラー
カウンター名:1 秒あたりのセキュリティ検証と認証エラー  
  
## <a name="description"></a>説明  
 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
- メッセージからクライアント トークンを読み取ることができない。  
  
- クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
- 署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
- メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
- 復号化に失敗した。  
  
- 一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
- TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用して、その値が計算されます。  
  
 (N1-N0)/((D1-D0)/F)
