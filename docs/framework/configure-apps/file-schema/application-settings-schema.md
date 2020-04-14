---
title: アプリケーション設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242830"
---
# <a name="application-settings-schema"></a>アプリケーション設定スキーマ

アプリケーション設定を使用すると、Windows フォームまたはASP.NET アプリケーションは、アプリケーション スコープおよびユーザー スコープの設定を格納および取得できます。 このコンテキストでは、*設定*は、アプリケーションに固有の情報、または現在のユーザーに固有の情報の一部です。

既定では、Windows フォーム アプリケーションのアプリケーション設定では<xref:System.Configuration.LocalFileSettingsProvider>、.NET 構成システムを使用して設定を XML 構成ファイルに格納するクラスが使用されます。 アプリケーション設定で使用されるファイルの詳細については、「[アプリケーション設定のアーキテクチャ](../../winforms/advanced/application-settings-architecture.md)」を参照してください。

アプリケーション設定では、使用する構成ファイルの一部として、次の要素を定義します。

| 要素                    | 説明                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<アプリケーション設定>** | アプリケーションに固有のすべての**\<設定>** タグが含まれます。                         |
| **\<ユーザー設定>**        | 現在のユーザーに固有のすべての**\<設定>** タグが含まれます。                        |
| **\<>の設定**             | 設定を定義します。 アプリケーションの子設定>または**\<ユーザー設定>。 ** ** \<** |
| **\<値>**               | 設定の値を定義します。 **\<設定>** の子。                                   |

## <a name="applicationsettings-element"></a>\<アプリケーション設定>要素

この要素には、クライアント コンピューター**\<上のアプリケーションの**インスタンスに固有のすべての設定>タグが含まれます。 属性は定義されません。

## <a name="usersettings-element"></a>\<ユーザー設定>要素

この要素には、現在アプリケーションを使用しているユーザーに固有のすべての**\<設定>** タグが含まれます。 属性は定義されません。

## <a name="setting-element"></a>\<>要素の設定

この要素は、設定を定義します。 この属性には、次の属性があります。

| 属性        | 説明 |
| ---------------- | ----------- |
| **name**         | 必須。 設定の一意の ID。 Visual Studio で作成された設定は、`ProjectName.Properties.Settings`という名前で保存されます。 |
| **シリアライズア** | 必須。 値をテキストにシリアル化するために使用する形式。 有効な値は次のとおりです。<br><br>- `string`. 値は、<xref:System.ComponentModel.TypeConverter>を使用して文字列としてシリアル化されます。<br>- `xml`. 値は、XML シリアル化を使用してシリアル化されます。<br>- `binary`. 値は、バイナリ シリアル化を使用してテキスト エンコードされたバイナリとしてシリアル化されます。<br />- `custom`. 設定プロバイダーには、この設定に関する固有の知識があり、シリアル化と逆シリアル化を行います。 |

## <a name="value-element"></a>\<要素>値

この要素には、設定の値が含まれます。

## <a name="example"></a>例

次の例は、2 つのアプリケーション スコープ設定と 2 つのユーザー スコープの設定を定義するアプリケーション設定ファイルを示しています。

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
