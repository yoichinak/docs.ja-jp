---
ms.openlocfilehash: b23f06ec5b27fbd7976a4b62ba6105c607eaee39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236698"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>一部の .NET API がファースト チャンス (処理済み) EntryPointNotFoundExceptions の原因になります

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、少数の .NET メソッドが、ファースト チャンス <xref:System.EntryPointNotFoundException?displayProperty=name> をスローするようになりました。 これらの例外は .NET Framework 内で処理されますが、ファースト チャンス例外を予期していないテスト自動化を中断することがありました。 これらと同じ API は、HighVersionLie が有効なとき、一部の ApiVerifier シナリオを中断させます。|
|提案される解決策|このバグは、.NET Framework 4.5.1 にアップグレードすることによって回避できます。 または、ファースト チャンス <xref:System.EntryPointNotFoundException?displayProperty=name> で中断しないように、テスト自動化を更新できます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|
