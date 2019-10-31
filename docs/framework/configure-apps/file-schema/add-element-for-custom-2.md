---
title: NameValueSectionHandler および DictionarySectionHandler の <add> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e7d68530ae1f0666fc4940ffe7605c3bf8dfe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119607"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler および DictionarySectionHandler の > 要素を追加 \<には

カスタムアプリケーション設定を追加します。 > タグの**追加\<** には、キーと値のペアが含まれています。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<追加 >**

## <a name="syntax"></a>構文

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>属性

| 属性 | 説明 |
| --------- | ----------- |
| **key**   | 必須の属性です。<br><br>設定の名前を指定します。 |
| **value** | 必須の属性です。<br><br>設定の値を指定します。 |

## <a name="parent-element"></a>親要素

| 要素 | 説明 |
| ------- | ------------|
| [ **\<sectionName >** Element](custom-element-2.md) | <xref:System.Configuration.NameValueSectionHandler> クラスと <xref:System.Configuration.DictionarySectionHandler> クラスを使用するカスタム構成セクションの設定を定義します。 |

## <a name="child-elements"></a>子要素

None

## <a name="example"></a>例

次の例は、カスタム構成セクションを定義し、 **\<add >** 要素を使用して設定をセクションに配置する方法を示しています。

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル *、コンピューター構成*ファイル (machine.config)、およびアプリケーションディレクトリレベルでは*ない web.config ファイル*で使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
