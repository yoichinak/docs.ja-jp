---
title: <configuration> の <configSections> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155350"
---
# <a name="configsections-element-for-configuration"></a>\<構成>>要素\<

構成セクションと名前空間の宣言が含まれます。

&nbsp;[**\<構成>**](configuration-element.md)&nbsp;**構成セクション>\<**

## <a name="attributes"></a>属性

なし

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成>**](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<セクション>**](section-element.md) | 構成セクションの宣言を含みます。 |
| [**\<セクショングループ>**](sectiongroup-element-for-configsections.md) | 構成セクションの名前空間を定義します。 |
| [**\<>を削除する**](remove-element-for-configsections.md) | 定義済みのセクションまたはセクション グループを削除します。 |
| [**\<クリア>**](clear-element-for-configsections.md) | 以前に定義したすべてのセクションおよびセクション グループをクリアします。 |

## <a name="remarks"></a>解説

この要素が構成ファイル内にある場合は、**\<要素の構成要素**の最初の子要素>必要があります。

## <a name="example"></a>例

次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。

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
