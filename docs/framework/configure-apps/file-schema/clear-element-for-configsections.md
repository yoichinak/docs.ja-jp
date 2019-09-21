---
title: <clear>appSettings&gt;の<configSections>add&gt;要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927728"
---
# <a name="clear-element-for-configsections"></a>\<configsections の > \<要素をクリア >

以前に定義されたセクションおよびセクション グループのすべてをクリアします。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<クリア >**

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
| [要素 > configsections  **\<** ](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれています。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

**\<Clear >** 要素は、現在の構成ファイルまたは構成ファイル階層の上位レベルで定義されたすべてのセクションとセクショングループをアプリケーションから削除します。

## <a name="example"></a>例

この例では、コンピューター構成ファイルとアプリケーション構成ファイルを定義し、アプリケーション構成ファイルで **\<clear >** 要素を使用して、コンピューター構成で以前に定義したセクションをクリアする方法を示します。拡張子.

次のマシン構成ファイルのコードでは、アプリケーション構成ファイルの前に読み取られた **\<sampleSection >** と **\<anotherSampleSection >** の2つのセクションが宣言されています。

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

次のアプリケーション構成ファイルのコードは、以前に宣言されたすべてのセクションを消去します。 アプリケーションでは、コンピューターの構成ファイルで宣言されているセクションのいずれかで設定を使用または取得することはできません。 ただし、  **\<clear >** 要素の後にあるため、他の **\<セクション >** の設定を使用できます。

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

この要素は、アプリケーション構成ファイル、コンピューター構成ファイル (machine.config)、およびアプリケーションディレクトリレベルではない web.config ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
