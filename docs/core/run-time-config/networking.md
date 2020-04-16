---
title: ネットワークの構成設定
description: .NET Core アプリのネットワークを構成するランタイム設定について説明します。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989104"
---
# <a name="run-time-configuration-options-for-networking"></a>ネットワークのランタイム構成オプション

## <a name="http2-protocol"></a>HTTP/2 プロトコル

- HTTP/2 プロトコルのサポートを有効にするかどうかを構成します。

- 既定:無効 (`false`)。

- .NET Core 3.0 で導入されました。

| | 設定の名前 | 値 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` - 無効<br/>`true` - 有効 |
| **環境変数** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` - 無効<br/>`1` - 有効 |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> が <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 以前の HTTP プロトコル スタック (Windows と `CurlHandler` では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の上位に実装された内部クラス) を使用するかどうかを構成します。

  > [!NOTE]
  > <xref:System.Net.Http.HttpClientHandler> クラスを直接インスタンス化するのではなく、高レベルのネットワーク API を使用している可能性があります。 この設定は、<xref:System.Net.Http.HttpClient> や [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)) などの高レベル ネットワーク API で使用される HTTP プロトコル スタックにも影響します。

- 既定:<xref:System.Net.Http.SocketsHttpHandler> を使用します (`true`)。

- この設定は、<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> メソッドを呼び出すことによりプログラムで構成できます。

| | 設定の名前 | 値 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする<br/>`false` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする |
| **環境変数** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする<br/>`0` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする |

> [!NOTE]
> .NET 5 以降では、`System.Net.Http.UseSocketsHttpHandler` 設定は使用できなくなりました。
