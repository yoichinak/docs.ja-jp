---
title: SingleTagSectionHandler のカスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927502"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler のカスタム要素

\<セクション > 要素によって定義され、 <xref:System.Configuration.SingleTagSectionHandler>クラスを使用するカスタム構成セクションの設定を定義します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName>*

## <a name="syntax"></a>構文

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>属性

属性と属性値はユーザーが定義します。

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

Sectionname > 要素は、 [ **\<configsections >** ](configsections-element-for-configuration.md)要素の[ **\<セクション >** ](section-element.md)タグによって定義されたカスタム要素です。  **\<** を呼び出す<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>と、 <xref:System.Collections.IDictionary>構成システムからオブジェクトが返されます。

## <a name="example"></a>例

次の例では、 <xref:System.Configuration.SingleTagSectionHandler>クラスによって読み取られた設定を含む **\<sampleSection >** という名前のカスタム要素を宣言しています。

```xml
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

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、コンピューター構成ファイル (machine.config)、およびアプリケーションディレクトリレベルではない web.config ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
