---
title: <configSections> の <remove> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f57dc9279c107ce751f71c2998670ab992db162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118435"
---
# <a name="remove-element-for-configsections"></a>\<configSections の > 要素を削除 \<

定義済みセクションまたはセクショングループを削除します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<削除**>

## <a name="syntax"></a>構文

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>削除するセクションまたはセクショングループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<configSections >** Element](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれています。 |

## <a name="child-elements"></a>子要素

None

## <a name="remarks"></a>Remarks

**\<remove >** 要素を使用して、構成ファイル階層の上位レベルで定義されたセクションとセクショングループをアプリケーションから削除できます。

## <a name="example"></a>例

次の例では、アプリケーション構成ファイルで **\<remove >** 要素を使用して、マシン構成ファイルで以前に定義したセクションを削除する方法を示します。

次のマシン構成ファイルのコードでは、セクション **\<sampleSection >** が宣言されています。

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

次のアプリケーション構成ファイルのコードでは、 **\<sampleSection >** セクションが削除されます。 削除後、アプリケーションは **\<sampleSection >** の設定を取得できません。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル *、コンピューター構成*ファイル (machine.config)、およびアプリケーションディレクトリレベルでは*ない web.config ファイル*で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
