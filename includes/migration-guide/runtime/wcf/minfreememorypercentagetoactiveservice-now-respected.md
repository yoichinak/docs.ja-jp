---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235636"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService が順守されるようになった

|   |   |
|---|---|
|説明|この設定は、WCF サービスをアクティブにするためにサーバー上で使用できなければならない最小メモリを設定します。 <xref:System.OutOfMemoryException?displayProperty=name> 例外が発生しないようにデザインされています。 .NET Framework 4.5 では、この設定には効果はありません。 .NET Framework 4.5.1 では、この設定が守られます。|
|提案される解決策|Web サーバーで使用できる空きメモリが構成設定によって定義されたパーセンテージよりも小さい場合、例外が発生します。 制約されたメモリ環境で正常に開始し、実行された WCF サービスが今度は失敗することがあります。|
|スコープ|マイナー|
|Version|4.5.1|
|型|ランタイム|
