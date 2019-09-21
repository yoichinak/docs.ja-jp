---
title: <sectionGroup>appSettings&gt;の<configSections>add&gt;要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4e28e8ccea1090e6a5704b541e09dc11681278ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920647"
---
# <a name="sectiongroup-element-for-configsections"></a>\<configsections の\<sectionGroup > 要素 >

構成セクションの名前空間を定義します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**

## <a name="syntax"></a>構文

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **name**  | 必須の属性です。<br><br>定義するセクショングループの名前を指定します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [要素 > configsections  **\<** ](configsections-element-for-configuration.md) | 構成セクションと名前空間の宣言が含まれています。 |

## <a name="child-elements"></a>子要素

|     | 説明 |
| --- | ----------- |
| [ **\<セクション >** ](section-element.md) | 構成セクションの宣言が含まれています。 |

## <a name="remarks"></a>Remarks

セクショングループを宣言すると、構成セクションのコンテナータグが作成され、他のユーザーが定義した構成セクションと名前の競合が発生しなくなります。 **\<SectionGroup >** 要素は、相互に入れ子にすることができます。

## <a name="example"></a>例

次の例は、セクショングループを宣言し、セクショングループ内でセクションを宣言する方法を示しています。

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイル、コンピューター構成ファイル (machine.config)、およびアプリケーションディレクトリレベルではない web.config ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
