---
title: アプリケーション設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927761"
---
# <a name="application-settings-schema"></a>アプリケーション設定スキーマ

アプリケーション設定を使用すると、Windows フォームまたは ASP.NET アプリケーションで、アプリケーションスコープの設定とユーザースコープの設定を格納および取得できます。 このコンテキストでは、*設定*は、アプリケーションに固有の情報、または現在のユーザーに固有の情報です。データベース接続文字列からユーザーの優先される既定のウィンドウサイズに至るまでのあらゆるものです。

既定では、Windows フォームアプリケーションのアプリケーション設定は<xref:System.Configuration.LocalFileSettingsProvider>クラスを使用します。このクラスは、.net 構成システムを使用して XML 構成ファイルに設定を格納します。 アプリケーション設定で使用されるファイルの詳細については、「[アプリケーション設定アーキテクチャ](../../winforms/advanced/application-settings-architecture.md)」を参照してください。

アプリケーション設定は、使用する構成ファイルの一部として、次の要素を定義します。

| 要素                    | 説明                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | **\<applicationSettings>\< すべてを含む** \<setting> アプリケーションに固有のタグ                         |
| **\<userSettings >**        | **\<userSettings>\<  すべてが含まれます** \<setting> タグは、現在のユーザーを特定します                        |
| **\<setting>**             | 設定を定義します。 いずれかの子 **\<applicationSettings >** または **\<userSettings>** します。 |
| **\<value>**               | 設定の値を定義します。 設定の値を定義します。 子 **\<setting>** します。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> 要素

この要素には、すべてが含まれています **\<setting>** クライアント コンピューターにアプリケーションのインスタンスに固有のタグ 属性は定義されません。

## <a name="usersettings-element"></a>\<userSettings> 要素

この要素には、すべてが含まれています **\<設定>** アプリケーションが現在使用してユーザーに固有のタグ。 属性は定義されません。

## <a name="setting-element"></a>\<setting> 要素

この要素は、設定を定義します。 これには次の属性があります。

| 属性        | 説明 |
| ---------------- | ----------- |
| **name**         | 必須。 設定の一意の ID。 Visual Studio で作成された設定は、 `ProjectName.Properties.Settings`という名前で保存されます。 |
| **serializedAs** | 必須。 値をテキストにシリアル化するために使用する形式。 次の値を指定できます。<br><br>- `string`。 値は、を<xref:System.ComponentModel.TypeConverter>使用して文字列としてシリアル化されます。<br>- `xml`。 値は、XML シリアル化を使用してシリアル化されます。<br>- `binary`。 この値は、バイナリシリアル化を使用して、テキストエンコードバイナリとしてシリアル化されます。<br />- `custom`。 設定プロバイダーは、この設定に固有の情報を持ち、シリアル化および逆シリアル化を行います。 |

## <a name="value-element"></a>\<value> 要素

この要素には、設定の値が含まれます。

## <a name="example"></a>例

次の例は、2つのアプリケーションスコープ設定と2つのユーザースコープ設定を定義するアプリケーション設定ファイルを示しています。

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

- [アプリケーション設定の概要](../../winforms/advanced/application-settings-overview.md)
- [アプリケーション設定アーキテクチャ](../../winforms/advanced/application-settings-architecture.md)
