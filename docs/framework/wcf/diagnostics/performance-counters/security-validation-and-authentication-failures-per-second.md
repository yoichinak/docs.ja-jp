---
title: 1 秒あたりのセキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: 5db8b656b626ea16f89ce432bf4cf1030b87a0b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664993"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>1 秒あたりのセキュリティ検証と認証エラー
カウンター名:セキュリティ検証と 1 秒あたりの認証エラー。  
  
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
