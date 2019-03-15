---
title: NameValueSectionHandler および DictionarySectionHandler のカスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 731e52958b89886c2bc069c4c181c0cc3928d487
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845710"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler および DictionarySectionHandler のカスタム要素

使用して、カスタム構成セクションの設定を定義、<xref:System.Configuration.NameValueSectionHandler>と<xref:System.Configuration.DictionarySectionHandler>クラス。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<追加 >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md)の<xref:System.Configuration.NameValueSectionHandler>と <xref:System.Configuration.DictionarySectionHandler>  | カスタム アプリケーションの設定を追加します。 |
| [**\<削除 >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md)の<xref:System.Configuration.NameValueSectionHandler>と <xref:System.Configuration.DictionarySectionHandler> | 以前に定義された設定を削除します。 |
| [**\<クリア >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md)の<xref:System.Configuration.NameValueSectionHandler>と <xref:System.Configuration.DictionarySectionHandler> | セクション内のすべての以前に定義された設定をクリアします。 |

## <a name="remarks"></a>Remarks

 **\<SectionName >** 要素がによって定義されるカスタム要素、 **\<セクション >** にタグを付ける、  **\<configSections >** 要素。

次の表は、各構成セクション ハンドラー オブジェクト ConfigurationSettings.GetConfig メソッドの型を返します。

| 構成セクション ハンドラー                        | 戻り値の型                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>例

次の例を使用するセクションを宣言する方法を示しています、<xref:System.Configuration.DictionarySectionHandler>と<xref:System.Configuration.NameValueSectionHandler>クラス。

最初のカスタム要素は **\<dictionarySample >**、によって読み取られた設定を含む、<xref:System.Configuration.DictionarySectionHandler>クラス、`System.dll`アセンブリ。 2 番目のカスタム要素は **\<mySection >**、によって読み取られた設定を含む、<xref:System.Configuration.NameValueSectionHandler>クラス、`System.dll`アセンブリ。

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
