---
title: <configuration> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705416"
---
# <a name="configuration-element"></a>\<configuration > 要素

共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。

**\<configuration>**

## <a name="syntax"></a>構文

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

なし

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [ **\<assemblyBinding >** ](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 構成レベルでのアセンブリ バインディング ポリシーを指定します。|
| [ **\<スタートアップ >** 設定スキーマ](~/docs/framework/configure-apps/file-schema/startup/index.md) | スタートアップ設定スキーマのすべての要素。 |
| [ **\<ランタイム >** 設定スキーマ](~/docs/framework/configure-apps/file-schema/runtime/index.md) | ランタイム設定スキーマのすべての要素。 |
| [ **\<system.runtime.remoting >** 設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | リモート処理設定スキーマのすべての要素。 |
| [ **\<system.Net >** 設定スキーマ](~/docs/framework/configure-apps/file-schema/network/index.md) | ネットワーク設定スキーマのすべての要素。 |
| [ **\<cryptographySettings >** 設定スキーマ](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | 暗号設定スキーマのすべての要素。 |
| [ **\<configuration >** セクション スキーマ](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | 構成セクションの設定のスキーマのすべての要素。 |
| [トレースおよびデバッグ設定のスキーマ](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | トレースとデバッグの設定のスキーマのすべての要素。 |
| [ASP.NET 構成設定のスキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET Web サイトおよびアプリケーションを構成するための要素を含む、ASP.NET 構成スキーマのすべての要素。 使用される*Web.config*ファイル。 |
| [ **\<webServices >** 設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web サービス設定スキーマのすべての要素。 |
| [Web 設定スキーマ](~/docs/framework/configure-apps/file-schema/web/index.md) | IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。 使用される*aspnet.config*ファイル。 |

## <a name="remarks"></a>Remarks

各構成ファイルには、1 つだけ含める必要があります **\<構成 >** 要素。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
