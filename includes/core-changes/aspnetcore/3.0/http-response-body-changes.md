---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394210"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP:応答本文のインフラストラクチャの変更

HTTP 応答本文を支えるインフラストラクチャが変更されました。 `HttpResponse` を直接使用する場合は、コードを変更する必要はありません。 `HttpResponse.Body` をラップまたは置換する場合や `HttpContext.Features` にアクセスする場合は、以下をお読みください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

HTTP 応答本文に関連付けられた次の 3 つの API がありました。

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>新しい動作

`HttpResponse.Body` を置き換えると、`IHttpResponseBodyFeature` 全体が、`StreamResponseBodyFeature` を使用して予想されるすべての API の既定の実装を提供する特定のストリームのラッパーに置き換えられます。 元のストリームに戻すと、この変更が元に戻されます。

#### <a name="reason-for-change"></a>変更理由

目的は、応答本文の API を単一の新しい機能インターフェイスに結合することです。

#### <a name="recommended-action"></a>推奨される操作

`IHttpResponseFeature.Body`、`IHttpSendFileFeature`、または `IHttpBufferingFeature` を以前に使用していた場所で `IHttpResponseBodyFeature` を使用します。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>
 
<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
