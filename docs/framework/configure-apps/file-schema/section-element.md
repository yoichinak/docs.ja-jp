---
title: <section> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153732"
---
# <a name="section-element"></a>\<セクション>要素

構成セクションの宣言を含みます。

[**\<構成>**](configuration-element.md)\
&nbsp;&nbsp;[**\<構成セクション>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<セクション>**

[**\<構成>**](configuration-element.md)\
&nbsp;&nbsp;[**\<構成セクション>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<セクショングループ>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<セクション>**

## <a name="syntax"></a>構文

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必須属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 構成セクションの名前を指定します。 |
| **型**  | 構成ファイルからセクションを読み取る構成セクション ハンドラー クラスの名前を指定します。 型の値は、"完全修飾セクション ハンドラー クラス名、単純アセンブリ名" という構文を持ちます。 簡易アセンブリ名は *、.dll*ファイル拡張子を持たないルート ファイル名です。 |

## <a name="optional-attributes"></a>省略可能な属性

次の属性は、ASP.NETアプリケーションにのみ適用できます。 構成システムは、他のアプリケーション・タイプのこれらの属性を無視します。

|                     | 説明 |
| ------------------- | ----------- |
| **定義を許可する** | セクションを使用できる構成ファイルを指定します。 次のいずれかの値を使用します。<br><br>**すべての場所**<br>任意の構成ファイルでセクションを使用できます。 これは既定値です。<br>**マシンのみ**<br>このセクションは、マシン構成ファイル (*Machine.config*) でのみ使用できます。<br>**マシンからアプリケーションへ**<br>マシン構成ファイルまたはアプリケーション構成ファイルでセクションを使用できるようにします。 |
| **場所を許可します。**   | 要素の場所内でセクション**\<>** 使用できるかどうかを決定します。 次のいずれかの値を使用します。<br><br>**true**<br>要素の位置内でセクション**\<>** 使用できるようにします。 これは既定値です。<br>**false**<br>要素の**\<場所**内でセクションを使用>許可しません。 |

## <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<構成セクション>** 要素](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれます。 |
| [**\<セクショングループ>** 要素](sectiongroup-element-for-configsections.md) | 構成セクションの名前空間を定義します。 |

> [!NOTE]
> 要素>**\<セクションは、configSection>** または**\<セクショングループ>** の子要素ですが、両方ではありません。 ** \<**

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>解説

構成セクションを宣言すると、基本的に構成ファイルの新しい要素が定義されます。 新しい要素には、構成セクション ハンドラー (つまり、インターフェイスを実装するクラス)<xref:System.Configuration.IConfigurationSectionHandler>が読み取る設定が含まれています。 定義するセクションの属性と子要素は、設定の読み取りに使用するセクション ハンドラーによって異なります。

*Machine.config*ファイルで構成セクション ハンドラーを宣言すると **、allowDefinition**属性で指定されていない限り、そのコンピューター上のアプリケーション構成ファイルで構成セクションを使用できます。

## <a name="example"></a>例

次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
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
