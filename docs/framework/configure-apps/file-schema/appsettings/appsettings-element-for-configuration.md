---
title: <configuration> の <appSettings> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155532"
---
# <a name="appsettings-element-for-configuration"></a>\<構成>の\<>要素

カスタム アプリケーション設定が含まれます。 これは、.NET Framework によって提供される定義済みの構成セクションです。

&nbsp;[**\<構成>**](../configuration-element.md)&nbsp;**アプリ設定>\<**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **ファイル**  | 省略可能な属性です。<br><br>カスタム アプリケーション構成設定を含む外部ファイルへの相対パスを指定します。 指定したファイルには、[**\<追加>、****\<削除**、>、および**\<>** 要素をクリアする] で指定した同じ種類の設定が含まれ、それらの要素と同じキー/値ペア形式が使用されます。<br><br>指定されたパスは、メイン構成ファイルを基準にしています。 Windows フォーム アプリケーションの場合、これはバイナリ フォルダ *(/bin/debug*など) であり、アプリケーション構成ファイルの場所ではありません。 Web フォーム アプリケーションの場合、パスは *、web.config*ファイルが配置されているアプリケーション ルートを基準にしています。<br><br>指定されたファイルが見つからない場合、ランタイムはこの属性を無視します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成>** 要素](../configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<>を追加する**](add-element-for-appsettings.md) | カスタム アプリケーション設定を追加します。 |
| [**\<クリア>**](clear-element-for-appsettings.md) | 以前に定義したアプリケーション設定をすべてクリアします。 |
| [**\<>を削除する**](remove-element-for-appsettings.md) | 以前に定義したアプリケーション設定を削除します。 |

## <a name="remarks"></a>解説

** \<appSettings>** 要素には、データベース接続文字列、ファイル パス、XML Web サービス URL、アプリケーションのその他のカスタム構成情報などのカスタム アプリケーション構成情報が格納されます。 ** \<appSettings>** 要素で指定されたキーと値のペアは、クラスを使用<xref:System.Configuration.ConfigurationSettings>してコードでアクセスされます。

*web.config*およびアプリケーション構成ファイルの**\<>** 要素の appSettings で**ファイル**属性を使用できます。 この属性は、追加の設定を提供する構成ファイルを指定するか**\<、appSettings>** 要素で指定された設定をオーバーライドします。 **file**属性は、ソース管理チームの開発シナリオで使用できます (ユーザーがアプリケーション構成ファイルで指定されたプロジェクト設定を上書きする場合など)。

**file**属性で指定される構成ファイルには、**\<構成>** ではなく**\<、appSettings>** のルート ノードが必要です。

## <a name="example"></a>例

次の例は、カスタム アプリケーション設定を定義する外部アプリケーション設定ファイル (*custom.config*) を示しています。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

次の例は、外部設定ファイルで設定を使用して、独自のアプリケーション設定を設定するアプリケーション構成ファイルを示しています。

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーションディレクトリレベルではないアプリケーション構成ファイル、マシン構成ファイル (*Machine.config*) および*Web.config*ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](../index.md)
