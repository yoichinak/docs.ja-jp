---
title: <configSections> の <remove> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154531"
---
# <a name="remove-element-for-configsections"></a>\<構成>要素を\<削除するセクション>

定義済みのセクションまたはセクション グループを削除します。

[**\<構成>**](configuration-element.md)\
&nbsp;&nbsp;[**\<構成セクション>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>を削除する**

## <a name="syntax"></a>構文

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>削除するセクションまたはセクション グループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成セクション>** 要素](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれます。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

**\<削除>** 要素を使用して、構成ファイル階層の上位レベルで定義されたセクションおよびセクション グループをアプリケーションから削除できます。

## <a name="example"></a>例

次の例は、アプリケーション構成ファイルで**\<remove>** 要素を使用して、コンピューター構成ファイルで以前に定義されたセクションを削除する方法を示しています。

次のマシン構成ファイル コードは、セクション**\<のサンプルセクション>** を宣言します。

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

次のアプリケーション構成ファイル コードは、**\<セクションセクション>セクション**を削除します。 削除後、アプリケーションは**\<sampleSection>** の設定を取得できません。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーションディレクトリレベルではないアプリケーション構成ファイル、マシン構成ファイル (*Machine.config*) および*Web.config*ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](index.md)
