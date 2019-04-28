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
ms.openlocfilehash: 909ee7cbb7cd31cf213f305b23237cb69e295882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674650"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > 要素

インクルードする構成ファイルを指定します。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a>構文

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **href**  | 必須の属性です。<br><br>含める構成ファイルの URL。 唯一の形式のサポート、 **href**属性が`file://`します。 ローカル ファイルと UNC ファイルがサポートされています。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<assemblyBinding >** 要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | 構成レベルでのアセンブリ バインディング ポリシーを指定します。 |

## <a name="child-elements"></a>子要素

なし

## <a name="remarks"></a>Remarks

 **\<LinkedConfiguration >** 要素は、サービス コンポーネントのアセンブリを簡略化します。 1 つまたは複数のアプリケーションでは、既知の場所に存在する構成ファイルを持つアセンブリを使用する場合、アセンブリを使用するアプリケーションの構成ファイルを使用できます、  **\<linkedConfiguration >** 構成情報を直接含むのではなく、アセンブリの構成ファイルを含める要素。 コンポーネント アセンブリが処理されるときに一般的な構成ファイルの更新、アセンブリを使用するすべてのアプリケーションに最新の構成情報を提供します。

> [!NOTE]
>  **\<LinkedConfiguration >** Windows サイド バイ サイドでマニフェストを使用するアプリケーションの要素がサポートされていません。

次の規則は、リンクされた構成ファイルの使用を制御します。

- 含まれる構成ファイルの設定は、ローダーのバインディング ポリシーの影響を与えるし、のみローダーでのみ使用されます。 含まれる構成ファイルではバインディング ポリシー以外の設定を使用できますが、これらの設定は、影響はありません。

- 唯一の形式のサポート、`href`属性が`file://`します。 ローカル ファイルと UNC ファイルがサポートされています。

- 構成ファイルごとにリンクされている構成の数に制約はありません。

- すべてのリンクされた構成ファイルを結合し、1 つのファイルの動作と同様に、 `#include` C と C++ のディレクティブ。

-  **\<LinkedConfiguration >** 要素がアプリケーション構成ファイルにのみ使用できます。 以外では無視されます*Machine.config*します。

- 循環参照が検出され、終了します。 つまり場合、  **\<linkedConfiguration >** ループを形成する一連の構成ファイルの要素、ループが検出され、停止します。

## <a name="example"></a>例

次の例では、ローカルのハード ディスクから構成ファイルをインクルードする方法を示します。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

- [**\<assemblyBinding >** 要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)
- [.NET Framework の構成ファイル スキーマ](~/docs/framework/configure-apps/file-schema/index.md)
