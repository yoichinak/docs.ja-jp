---
title: カスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155155"
---
# <a name="custom-element-for-singletagsectionhandler"></a>カスタム要素

要素の\<セクションで定義され、クラスを使用するカスタム構成セクション>設定を定義<xref:System.Configuration.SingleTagSectionHandler>します。

&nbsp;[**\<構成>**](configuration-element.md)&nbsp;*セクション名>\<*

## <a name="syntax"></a>構文

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>属性

属性と属性値はユーザー定義です。

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成>**](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

セクション名>要素は、セクション>要素要素の[**\<タグ**](section-element.md)によって定義される**\<**[**\<カスタム要素>。**](configsections-element-for-configuration.md) 構成システムは、<xref:System.Collections.IDictionary>を呼び出<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>すとオブジェクトを返します。

## <a name="example"></a>例

次の例では、クラスによって読み取られた設定を含む**\<sampleSection>** と呼ばれるカスタム要素を<xref:System.Configuration.SingleTagSectionHandler>宣言します。

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

この要素は、アプリケーションディレクトリレベルではないアプリケーション構成ファイル、マシン構成ファイル (*Machine.config*) および*Web.config*ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](index.md)
