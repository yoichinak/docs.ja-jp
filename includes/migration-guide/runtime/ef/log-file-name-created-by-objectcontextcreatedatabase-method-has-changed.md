---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235766"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>ObjectContext.CreateDatabase メソッドによって作成されたログ ファイル名が、SQL Server の仕様に一致するように変更された

|   |   |
|---|---|
|説明|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> メソッドが、直接、または SqlClient プロバイダーと共に Code First と接続文字列の AttachDBFilename 値を使用して呼び出されると、filename.ldf (filename は AttachDBFilename 値によって指定されたファイルの名前) ではなく、filename_log.ldf という名前のログ ファイルを作成します。 この変更により、SQL Server の仕様に従ってログ ファイル名が提供されるため、デバッグ機能が向上します。|
|提案される解決策|ログ ファイル名がアプリケーションにとって重要な場合、標準の _log.ldf ファイル名形式を予期するように、アプリケーションを更新する必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
