---
ms.openlocfilehash: 1f06a185939c40274adad1ceac6990719069167a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804391"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>データ定義言語 (DDL: Data Definition Language) API の動作の変更

|   |   |
|---|---|
|説明|AttachDBFilename が指定されたときの DDL API の動作が、次のように変更されました。<ul><li>接続文字列で初期カタログ値を指定する必要がなくなりました。 以前は、AttachDBFilename と初期カタログの両方が必要でした。</li><li>AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> メソッドは <code>true</code> を返します。 以前は、<code>false</code>が返されていました。</li><li>AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、<xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> メソッドを呼び出すと、ファイルが削除されます。</li><li>接続文字列で存在しない MDF の AttachDBFilename 値および存在しない初期カタログが指定されたときに <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> が呼び出されると、メソッドでは <xref:System.InvalidOperationException> 例外がスローされます。 以前は、<xref:System.Data.SqlClient.SqlException> の例外がスローされていました。</li></ul>|
|提案される解決策|これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。 これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。<ul><li><code>DROP DATABASE</code> で <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> が返されたときに、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> を呼び出す代わりに直接 <code>true</code> コマンドを実行するコードをユーザーが作成した場合。 データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。</li><li>初期カタログと MDF ファイルが存在しない場合に、<xref:System.InvalidOperationException> ではなく <xref:System.Data.SqlClient.SqlException> をスローするように、<xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> メソッドを要求するコードをユーザーが作成した場合。</li></ul>|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
