---
ms.openlocfilehash: e8c48c4b1031813ce62f576e5bf1f94c082dfe4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234700"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute は、WinMD のシナリオで、ObsoleteAttribute と DeprecatedAttribute の両方としてエクスポートする

|   |   |
|---|---|
|説明|Windows メタデータ ライブラリ (.winmd ファイル) を作成するとき、<xref:System.ObsoleteAttribute?displayProperty=name> 属性は <xref:System.ObsoleteAttribute?displayProperty=name> および [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) の両方としてエクスポートされます。|
|提案される解決策|<xref:System.ObsoleteAttribute?displayProperty=name> 属性を使用する既存のソース コードを再コンパイルするとき、C++/CX または JavaScript からそのコードを使用するとき、警告が生成されることがあります。マネージド アセンブリのコードを記述するとき、<xref:System.ObsoleteAttribute?displayProperty=name> と [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) の両方を適用することはお勧めしません。ビルドで警告が生成されることがあります。|
|スコープ|エッジ|
|Version|4.5.1|
|型|再ターゲット中|
