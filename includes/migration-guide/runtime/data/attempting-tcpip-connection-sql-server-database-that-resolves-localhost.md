---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237842"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>`localhost` に解決される SQL Server データベースへの TCP/IP 接続の試みが失敗します

|   |   |
|---|---|
|説明|.NET Framework 4.6 および 4.6.1 で、<code>localhost</code> に解決される SQL Server データベースへの TCP/IP 接続の試みが次のエラーで失敗していました: &quot;SQL Server への接続を確立しているときにネットワーク関連またはインスタンス固有のエラーが発生しました。 サーバーが見つからないかアクセスできません。 インスタンス名が正しいこと、および SQL Server がリモート接続を許可するように構成されていることを確認してください。 (プロバイダー:SQL ネットワーク インターフェイス、エラー:26 - 指定されたサーバーまたはインスタンスの位置を特定しているときにエラーが発生しました)&quot;|
|提案される解決策|この問題は修正済みであり、.NET Framework 4.6.2 では以前の動作に戻っています。 <code>localhost</code> に解決される SQL Server データベースに接続するには、.NET Framework 4.6.2 にアップグレードします。|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|
