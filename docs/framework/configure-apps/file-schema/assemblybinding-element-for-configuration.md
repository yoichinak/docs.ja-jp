---
title: <assemblyBinding>appSettings&gt;の<configuration>add&gt;要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921275"
---
# <a name="assemblybinding-element-for-configuration"></a>\<構成 > の\<assemblybinding > 要素

構成レベルでのアセンブリ バインディング ポリシーを指定します。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding >**

## <a name="syntax"></a>構文

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>属性

|           | 説明 |
| --------- | ----------- |
| **xmlns** | 必須の属性です。<br><br>アセンブリのバインディングに必要な XML 名前空間を指定します。 値として、文字列 "urn:schemas-microsoft-com:asm.v1" を使用します。 |

## <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-element"></a>子要素

|     | 説明 |
| --- | ----------- |
| [ **\<linkedConfiguration >** ](linkedconfiguration-element.md) | インクルードする構成ファイルを指定します。 |

## <a name="remarks"></a>Remarks

[ **\<Linkedconfiguration >** ](linkedconfiguration-element.md)要素は、アセンブリを複製するのではなく、既知の場所にアセンブリ構成ファイルを含めることをアプリケーション構成ファイルに許可することで、コンポーネントアセンブリの管理を簡略化します。構成設定。

> [!NOTE]
> **\<Linkedconfiguration >** 要素は、Windows サイドバイサイドマニフェストを持つアプリケーションではサポートされていません。

## <a name="example"></a>例

次の例は、ローカルのハードディスクに構成ファイルを含める方法を示しています。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](index.md)
