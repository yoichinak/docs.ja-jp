---
title: セキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 0f061e1e12321dbe8034d7619830f71717ca9d1f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664972"
---
# <a name="security-validation-and-authentication-failures"></a>セキュリティ検証と認証エラー
カウンター名:セキュリティ検証と認証エラー  
  
## <a name="description"></a>説明  
 このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。 この問題には、次のようなものがあります。  
  
- メッセージからクライアント トークンを読み取ることができない。  
  
- クライアント トークンが認証に失敗した (例 : 無効なパスワード)。  
  
- 署名の検証に失敗した (例 : メッセージが改ざんされた)。  
  
- メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。  
  
- 復号化に失敗した。  
  
- 一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。  
  
- TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。
