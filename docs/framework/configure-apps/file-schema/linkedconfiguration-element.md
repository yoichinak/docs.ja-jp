---
title: <linkedConfiguration> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921013"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 要素

インクルードする構成ファイルを指定します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration >**

## <a name="syntax"></a>構文

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **href**  | 必須の属性です。<br><br>含める構成ファイルの URL。 **Href**属性でサポートされている形式`file://`はのみです。 ローカルファイルと UNC ファイルがサポートされています。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [assemblybinding > 要素 **\<** ](assemblybinding-element-for-configuration.md) | 構成レベルでのアセンブリ バインディング ポリシーを指定します。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

**\<Linkedconfiguration >** 要素は、コンポーネントアセンブリのサービスを簡略化します。 既知の場所に構成ファイルが存在するアセンブリが1つ以上のアプリケーションで使用されている場合、そのアセンブリを使用するアプリケーションの構成ファイルでは、  **\<linkedconfiguration >** 要素を使用して、構成情報を直接含めるのではなく、アセンブリ構成ファイル。 コンポーネントアセンブリがサービスされている場合、共通構成ファイルを更新すると、そのアセンブリを使用するすべてのアプリケーションに対して、更新された構成情報が提供されます。

> [!NOTE]
> **\<Linkedconfiguration >** 要素は、Windows サイドバイサイドマニフェストを持つアプリケーションではサポートされていません。

次の規則は、リンクされた構成ファイルの使用を制御します。

- インクルードされる構成ファイルの設定は、ローダーバインドポリシーにのみ影響し、ローダーによってのみ使用されます。 含まれる構成ファイルには、バインドポリシー以外の設定を含めることができますが、これらの設定は何の効果もありません。

- `href`属性でサポートされている形式`file://`はのみです。 ローカルファイルと UNC ファイルがサポートされています。

- 構成ファイルごとにリンクされる構成の数に制限はありません。

- C/ `#include` C++のディレクティブの動作と同様に、すべてのリンクされた構成ファイルが1つのファイルに結合されます。

- **\<Linkedconfiguration >** 要素は、アプリケーション構成ファイル内でのみ許可されます。 *machine.config*では無視されます。

- 循環参照が検出され、終了します。 つまり、  **\<** 一連の構成ファイルの linkedconfiguration > 要素がループを形成すると、ループが検出され、停止されます。

## <a name="example"></a>例

次の例は、ローカルハードディスクの構成ファイルを含める方法を示しています。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

- [assemblybinding > 要素 **\<** ](assemblybinding-element-for-configuration.md)
- [.NET Framework の構成ファイルスキーマ](index.md)
