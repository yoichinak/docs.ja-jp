---
title: <appSettings>appSettings&gt;の<configuration>add&gt;要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: e8f85be2efe972fc45230855d18649a89f2fbd61
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300816"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > 要素の\<構成 >

カスタム アプリケーションの設定が含まれています。 これは、.NET Framework で提供される定義済みの構成セクションです。

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp; **\<appSettings>**

## <a name="syntax"></a>構文

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **file**  | 省略可能な属性です。<br><br>カスタム アプリケーションの構成設定を含む外部ファイルへの相対パスを指定します。 同じ種類設定で指定されているにはが、指定したファイルに含まれています、 **\<追加 >** 、 **\<削除 >** 、および **\<オフ >** 要素と同じキー/値ペアは、それらの要素として書式設定を使用します。<br><br>指定されたパスでは、主要な構成ファイルの相対です。 Windows フォーム アプリケーションでは、これは、バイナリ フォルダー (など*bin/デバッグ*)、アプリケーション構成ファイルの場所ではありません。 Web フォーム アプリケーション、パスは、アプリケーションのルートを基準とした場所、 *web.config*ファイルが配置されています。<br><br>指定したファイルが見つからない場合、ランタイムは、属性を無視します。 注意してください。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<configuration >** 要素](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [ **\<add>** ](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | カスタム アプリケーション設定を追加します。 |
| [ **\<clear>** ](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | すべての定義済みのアプリケーション設定をクリアします。 |
| [ **\<remove>** ](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | 定義済みのアプリケーション設定を削除します。 |

## <a name="remarks"></a>Remarks

**\<AppSettings >** 要素は、データベース接続文字列、ファイル パス、XML Web サービスの Url の他のカスタム構成情報などのカスタム アプリケーションの構成情報を格納します。アプリケーション。 指定されたキーと値のペア、  **\<appSettings >** 要素は、コードを使用して、<xref:System.Configuration.ConfigurationSettings>クラス。

使用することができます、**ファイル**属性、  **\<appSettings >** の要素、 *Web.config*とアプリケーション構成ファイル。 この属性は、追加の設定を提供またはで指定された設定をオーバーライドする構成ファイルを指定、  **\<appSettings >** 要素。 **ファイル**属性をソース制御チーム開発などのシナリオで、ユーザーがアプリケーション構成ファイルで指定されたプロジェクトの設定をオーバーライドできます。

指定された構成ファイル、**ファイル**属性のルート ノードが必要です **\<appSettings >** なく **\<構成>** 。

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

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
