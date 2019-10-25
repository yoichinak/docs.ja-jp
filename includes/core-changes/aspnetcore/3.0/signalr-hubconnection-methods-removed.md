---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394231"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: HubConnection の ResetSendPing メソッドと ResetTimeout メソッドが削除された

`ResetSendPing` メソッドと `ResetTimeout` メソッドが、SignalR の `HubConnection` API から削除されました。 これらのメソッドはもともと内部使用のみを目的としていましたが、ASP.NET Core 2.2 で公開されました。 これらのメソッドは、ASP.NET Core 3.0 Preview 4 リリース以降では使用できません。 ディスカッションについては、[aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

API を使用できました。

#### <a name="new-behavior"></a>新しい動作

API は削除されています。

#### <a name="reason-for-change"></a>変更理由

これらのメソッドはもともと内部使用のみを目的としていましたが、ASP.NET Core 2.2 で公開されました。

#### <a name="recommended-action"></a>推奨される操作

これらのメソッドは使用しないでください。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
