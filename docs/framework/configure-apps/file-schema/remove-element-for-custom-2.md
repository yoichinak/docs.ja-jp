---
title: <remove>NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920945"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<NameValueSectionHandler および DictionarySectionHandler の > 要素を削除します。

以前に定義した設定を削除します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<> の削除**

## <a name="syntax"></a>構文

```xml
<add remove="key" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>削除する設定の名前を指定します。 |

## <a name="parent-element"></a>親要素

| 要素 | 説明 |
| ------- | ------------|
| [sectionname > 要素 **\<** ](custom-element-2.md) | クラス<xref:System.Configuration.NameValueSectionHandler> および<xref:System.Configuration.DictionarySectionHandler>クラスを使用するカスタム構成セクションの設定を定義します。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

[  **\<> の削除**] 要素を使用して、構成ファイル階層の上位レベルで定義されているアプリケーションから設定を削除できます。

## <a name="example"></a>例

次の例は、アプリケーション構成ファイルで **\<remove >** 要素を使用して、マシン構成ファイルで以前に定義した設定を削除する方法を示しています。

次のマシン構成ファイルのコードでは、セクション **\<mysection >** を宣言し`key1` 、 `key2`2 つの設定 (と) を追加します。

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

次のアプリケーション構成ファイルのコードは`key2` 、  **\<mysection >** から設定を削除します。

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、コンピューター構成ファイル (machine.config)、およびアプリケーションディレクトリレベルではない web.config ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
