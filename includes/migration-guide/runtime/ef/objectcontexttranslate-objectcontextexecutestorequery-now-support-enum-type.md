---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235502"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate と ObjectContext.ExecuteStoreQuery で列挙型がサポートされるようになった

|   |   |
|---|---|
|説明|.NET Framework 4.0 では、<code>ObjectContext.Translate</code> および <code>ObjectContext.ExecuteStoreQuery</code> メソッドのジェネリック パラメーター <code>T</code> を列挙型にすることはできませんでした。 このシナリオがサポートされるようになりました。|
|提案される解決策|.NET Framework 4.0 では、列挙型に対して Translate または ExecuteStoreQuery が呼び出された場合、"0" が返されました。 この動作が望ましい場合は、呼び出しを定数 0 (または同等の列挙型) に置き換えてください。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
