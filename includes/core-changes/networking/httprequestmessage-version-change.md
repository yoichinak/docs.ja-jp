---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237394"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage.Version の既定値が 1.1 に変更された 

<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティの既定値が 2.0 から 1.1 に変更されました。

#### <a name="version-introduced"></a>導入されたバージョン

.NET Core 3.0

#### <a name="change-description"></a>変更の説明

.NET Core 1.0 から 2.0 では、<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティの既定値は 1.1 です。 .NET Core 2.1 以降では、2.1 に変更されました。 

.NET Core 3.0 以降では、<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティによって返される既定のバージョン番号は再び 1.1 になりました。
 
#### <a name="recommended-action"></a>推奨される操作

既定値 2.0 を返す <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> プロパティに依存している場合は、コードを更新します。

#### <a name="category"></a>カテゴリ

ネットワーキング

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

