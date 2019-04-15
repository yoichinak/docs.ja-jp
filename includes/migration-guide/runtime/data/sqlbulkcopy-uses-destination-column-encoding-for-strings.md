---
ms.openlocfilehash: fa09831ac47a59535ff73c8c8680c2642c3248c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235523"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy で文字列に挿入先の列エンコードが使用される

|   |   |
|---|---|
|説明|データを列に挿入する場合、<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> は <code>VARCHAR</code> と <code>CHAR</code> の型の既定エンコードではなく、挿入先の列のエンコードを使用します。 この変更により、挿入先の列が既定のエンコードを使用しない場合に、既定のエンコードを使用することによって発生するデータ破損の可能性がなくなります。 まれに、エンコードに変更を加えることによって、挿入先の列に収まりきらない大きいデータが生成された場合に、既存のアプリケーションで SqlException の例外がスローされることがあります。|
|提案される解決策|<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> では、エンコードが異なるため、データは破損しなくなると予想します。 挿入先の列のサイズ制限に近づいている文字列がコピーされている場合、データの事前エンコード (コピーして挿入先の行にデータが収まることを確認するため) や <xref:System.Data.SqlClient.SqlException?displayProperty=name> のキャッチが必要になることがあります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|
