---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394045"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: トランスポートの抽象化を削除して公開

"pubternal" API からの移行の一環として、Kestrel トランスポート層の API がパブリック インターフェイスとして `Microsoft.AspNetCore.Connections.Abstractions` ライブラリに公開されています。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

- トランスポート関連の抽象化は、`Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` ライブラリで提供されていました。
- `ListenOptions.NoDelay` プロパティが使用可能でした。

#### <a name="new-behavior"></a>新しい動作

- `...Transport.Abstractions` ライブラリの最も使用されている機能を公開するために、`Microsoft.AspNetCore.Connections.Abstractions` ライブラリに `IConnectionListener` インターフェイスが導入されました。
- トランスポート オプション (`LibuvTransportOptions` および `SocketTransportOptions`) で、`NoDelay` が使用できるようになりました。
- `SchedulingMode` は使用できなくなりました。

#### <a name="reason-for-change"></a>変更理由

ASP.NET Core 3.0 は、"pubternal" API から移行しました。

#### <a name="recommended-action"></a>推奨される操作

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

### Affected APIs

Not detectable via API analysis

-->
