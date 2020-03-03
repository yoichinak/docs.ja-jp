---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237617"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>グリッド スター行領域の割り当てアルゴリズムの改善

|   |   |
|---|---|
|説明|.NET Framework 4.7 で導入された <xref:System.Windows.Controls.Grid> で[サイズを割り当てるためのアルゴリズム](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) のバグを修正しました。  空の行を含む <code>Height=&quot;Auto&quot;</code> のグリッドなど、場合によっては、行が正しくない位置に配置され、すべてグリッドの外側に示されることがありました。|
|提案される解決策|アプリケーションでこれらの変更を利用するには、.NET Framework 4.8 以降で実行する必要があります。|
|スコープ|Major|
|Version|4.8|
|型|ランタイム|
