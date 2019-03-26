---
title: アプリケーション設定のスキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: a74716bcdf3c85c08d0ff3bf66407dce30ee91cc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083471"
---
# <a name="application-settings-schema"></a>アプリケーション設定のスキーマ

アプリケーションの設定は、格納およびアプリケーション スコープし、ユーザー スコープの設定を取得する Windows フォームや ASP.NET アプリケーションを許可します。 このコンテキストで、*設定*任意のアプリケーションに固有または現在のユーザーに特定できる情報は、-、ユーザーにデータベース接続文字列から何かの既定のウィンドウ サイズを優先します。

既定では、Windows フォーム アプリケーションでアプリケーションの設定を使用して、<xref:System.Configuration.LocalFileSettingsProvider>クラスは、XML 構成ファイルで設定を格納する、.NET 構成システムを使用します。 アプリケーションの設定で使用されるファイルの詳細については、[アプリケーション設定アーキテクチャ](~/docs/framework/winforms/advanced/application-settings-architecture.md)を参照してください。

アプリケーションの設定は、使用して、構成ファイルの一部として、次の要素を定義します。

| 要素                    | 説明                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | **\<applicationSettings>\< すべてを含む** \<setting> アプリケーションに固有のタグ                         |
| **\<userSettings>**        | **\<userSettings>\<  すべてが含まれます** \<setting> タグは、現在のユーザーを特定します                        |
| **\<setting>**             | 設定を定義します。 いずれかの子 **\<applicationSettings >** または **\<userSettings>** します。 |
| **\<value>**               | 設定の値を定義します。 設定の値を定義します。 子 **\<setting>** します。                                    |

## <a name="applicationsettings-element"></a>\<applicationSettings> 要素

この要素には、すべてが含まれています **\<setting>** クライアント コンピューターにアプリケーションのインスタンスに固有のタグ 属性は定義されません。

## <a name="usersettings-element"></a>\<userSettings> 要素

この要素には、すべてが含まれています **\<設定>** アプリケーションが現在使用してユーザーに固有のタグ。 属性は定義されません。

## <a name="setting-element"></a>\<setting> 要素

この要素は、設定を定義します。 次の属性があります。

| 属性        | 説明 |
| ---------------- | ----------- |
| **name**         | 必須。 設定の一意の ID。 Visual Studio で作成した設定は、名前で保存は`ProjectName.Properties.Settings`します。 |
| **serializedAs** | 必須。 テキスト値をシリアル化するために使用する形式。 次の値を指定できます。<br><br>- `string`。 使用して文字列として値をシリアル化、<xref:System.ComponentModel.TypeConverter>します。<br>- `xml`。 値は、XML シリアル化を使用してシリアル化されます。<br>- `binary`。 値は、バイナリ シリアル化を使用して、テキスト エンコードされたバイナリとしてシリアル化されます。<br />- `custom`。 設定プロバイダーは、この設定の固有の情報しシリアル化し、逆シリアル化します。 |

## <a name="value-element"></a>\<value> 要素

この要素には、設定の値が含まれています。

## <a name="example"></a>例

次の例では、2 つのアプリケーション スコープ設定と 2 つのユーザー スコープ設定を定義するアプリケーション設定ファイルを示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>関連項目

- [アプリケーション設定の概要](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [アプリケーション設定アーキテクチャ](~/docs/framework/winforms/advanced/application-settings-architecture.md)
