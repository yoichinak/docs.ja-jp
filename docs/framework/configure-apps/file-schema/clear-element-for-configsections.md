---
title: <configSections> の <clear> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155428"
---
# <a name="clear-element-for-configsections"></a>\<configSections> の \<clear> 要素

以前に定義したセクションとセクショングループをすべて消去します。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>構文

```xml
<clear/>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>削除するセクションまたはセクショングループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configSections>** Element](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれています。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

要素は、 **\<clear>** アプリケーションから、現在の構成ファイルまたは構成ファイル階層の上位レベルに定義されたすべてのセクションとセクショングループを削除します。

## <a name="example"></a>例

この例では、コンピューター構成ファイルとアプリケーション構成ファイルを定義し、 **\<clear>** アプリケーション構成ファイルで要素を使用して、マシン構成ファイルで以前に定義したセクションをクリアする方法を示します。

次のマシン構成ファイルのコードでは、とという2つのセクションを宣言 **\<sampleSection>** して **\<anotherSampleSection>** います。これらは、アプリケーション構成ファイルの前に読み込まれています。

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

次のアプリケーション構成ファイルのコードは、以前に宣言されたすべてのセクションを消去します。 アプリケーションでは、コンピューターの構成ファイルで宣言されているセクションのいずれかで設定を使用または取得することはできません。 ただし、要素の後に来るため、の設定を使用でき **\<anotherSection>** **\<clear>** ます。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル *、コンピューター構成*ファイル (machine.config)、およびアプリケーションディレクトリレベルでは*ない web.config ファイル*で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
