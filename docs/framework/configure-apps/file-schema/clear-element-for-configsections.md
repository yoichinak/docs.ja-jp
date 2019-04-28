---
title: <clear>appSettings&gt;の<configSections>add&gt;要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d824ae828dd025f3292990facaa5e423add9c282
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705351"
---
# <a name="clear-element-for-configsections"></a>\<クリア > 要素の\<configSections >

以前に定義されたセクションおよびセクション グループのすべてをクリアします。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>構文

```xml
<clear/>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>セクションまたは削除するセクション グループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configSections >** 要素](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 構成セクションと名前空間宣言が含まれています。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

**\<オフ >** 要素、または構成ファイル階層内の上位レベルにある現在の構成ファイルで既に定義されているアプリケーションからすべてのセクションおよびセクション グループを削除します。

## <a name="example"></a>例

この例は、マシン構成ファイルと、アプリケーション構成ファイルを定義しを使用する方法を示しています、 **\<オフ >** セクションで以前に定義を解除する、アプリケーション構成ファイル内の要素、マシン構成ファイル。

マシン構成ファイルのコードは、次は、2 つのセクションを宣言します **\<sampleSection >** と **\<anotherSampleSection >**、アプリケーションを読んでいる。構成ファイル:

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

次のアプリケーション構成ファイルのコードでは、以前に宣言されたすべてのセクションをクリアします。 アプリケーションがコンピューターの構成ファイルで宣言されたセクションのいずれかの設定を取得または使用できません。 ただしから設定を使用して、  **\<anotherSection >** 後を備えているため、 **\<をオフに >** 要素。

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

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
