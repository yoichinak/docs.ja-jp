---
ms.openlocfilehash: c9efbefc2bce9e21f328680795e72b62bfcd5cbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379647"
---
### <a name="enumerableemptytresult-always-returns-cached-instance"></a>Enumerable.Empty\<TResult> は、常にキャッシュされたインスタンスを返します

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Linq.Enumerable.Empty%60%601> は、常にキャッシュされた内部インスタンス <xref:System.Collections.Generic.IEnumerable%601> を返します。以前は、<xref:System.Linq.Enumerable.Empty%60%601> は、API が呼び出された時点で空の <xref:System.Collections.Generic.IEnumerable%601> をキャッシュしました。つまり、<xref:System.Linq.Enumerable.Empty%60%601> が迅速かつ同時に呼び出されるような条件では、API の別の呼び出しに対して、型の別のインスタンスが返される可能性がありました。|
|提案される解決策|以前の動作は非確定的なため、コードがそれに依存している可能性は低いです。 ただし、ありそうにないことですが、空の列挙が比較され、ときには等しくないことが予期されている場合には、<xref:System.Linq.Enumerable.Empty%60%601> を使用する代わりに、明示的に空の配列を作成する (<code>new T[0]</code>) 必要があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
