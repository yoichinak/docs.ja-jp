---
title: <remove>appSettings&gt;の<configSections>add&gt;要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9ceffd3194c7df41f12ac6cd6b589602965b4920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674312"
---
# <a name="remove-element-for-configsections"></a>\<削除 > 要素の\<configSections >

定義済みのセクション、またはセクション グループを削除します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>構文

```xml
<remove name="section name or section group name" />
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

使用することができます、 **\<削除 >** セクションおよびセクション グループを構成ファイル階層内の上位レベルで定義されているアプリケーションから削除する要素。

## <a name="example"></a>例

次の例は、使用する方法を示します、 **\<削除 >** マシン構成ファイルで定義したセクションを削除するアプリケーション構成ファイル内の要素。

マシン構成ファイルのコードは、次のセクションを宣言します **\<sampleSection >**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

アプリケーション構成ファイルのコードは、次の削除、  **\<sampleSection >** セクション。 削除した後、アプリケーションが設定を取得できません **\<sampleSection >** します。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
