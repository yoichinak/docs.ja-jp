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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155428"
---
# <a name="clear-element-for-configsections"></a>\<構成セクション>の\<>要素をクリアする

以前に定義したすべてのセクションおよびセクション グループをクリアします。

&nbsp;&nbsp;[**\<構成>**](configuration-element.md)&nbsp;&nbsp;**な\<>>** セクション[**\<**](configsections-element-for-configuration.md)&nbsp;&nbsp;

## <a name="syntax"></a>構文

```xml
<clear/>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>削除するセクションまたはセクション グループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成セクション>** 要素](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれます。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

** \<clear>** 要素は、現在の構成ファイルで以前に定義された、または構成ファイル階層の上位レベルで定義されたすべてのセクションとセクション グループをアプリケーションから削除します。

## <a name="example"></a>例

この例では、マシン構成ファイルとアプリケーション構成ファイルを定義し、**\<アプリケーション**構成ファイルで clear>要素を使用して、マシン構成ファイルで以前に定義されたセクションをクリアする方法を示します。

次のマシン構成ファイル コードでは、**\<アプリケーション**構成ファイルの前に読み取られる、sampleSection>と**\<別の SampleSection>** の 2 つのセクションを宣言します。

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

次のアプリケーション構成ファイルコードは、以前に宣言されたすべてのセクションをクリアします。 アプリケーションは、マシン構成ファイルで宣言されたセクションの設定を使用または取得できません。 ただし、クリア**\<>** 要素の後に来るので、**\<別のセクション>** からの設定を使用することができます。

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

この要素は、アプリケーションディレクトリレベルではないアプリケーション構成ファイル、マシン構成ファイル (*Machine.config*) および*Web.config*ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](index.md)
