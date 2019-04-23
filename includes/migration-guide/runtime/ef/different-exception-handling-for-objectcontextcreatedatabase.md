---
ms.openlocfilehash: 33ad1c044001e0a8d09708cc7a1f06e05cb307de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804412"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>ObjectContext.CreateDatabase メソッドと DbProviderServices.CreateDatabase メソッドで異なる例外処理

|   |   |
|---|---|
|説明|.NET Framework 4.5 から、データベースの作成が失敗した場合、<code>CreateDatabase</code> メソッドは、空のデータベースの削除を試みます。 その操作が成功した場合、元の <xref:System.Data.SqlClient.SqlException?displayProperty=name> は伝播されます (.NET Framework 4.0 で常にスローされていた <xref:System.InvalidOperationException?displayProperty=name> の代わりに)|
|提案される解決策|<xref:System.Data.Objects.ObjectContext.CreateDatabase> または <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> の実行中に <xref:System.InvalidOperationException?displayProperty=name> をキャッチするときには、SQLExceptions もキャッチする必要があります。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
