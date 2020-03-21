---
title: <configuration> の <assemblyBinding> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155480"
---
# <a name="assemblybinding-element-for-configuration"></a>\<コンフィギュレーション>の>要素\<の組み合て

構成レベルでのアセンブリ バインディング ポリシーを指定します。

&nbsp;[**\<アセンブリ>**](configuration-element.md)&nbsp;**構成>\<**

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
| [**\<構成>**](configuration-element.md) | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |

## <a name="child-element"></a>子要素

|     | 説明 |
| --- | ----------- |
| [**\<リンクされた構成>**](linkedconfiguration-element.md) | インクルードする構成ファイルを指定します。 |

## <a name="remarks"></a>解説

[** \<linkedConfiguration>**](linkedconfiguration-element.md)要素は、アセンブリ構成設定を複製するのではなく、既知の場所にアセンブリ構成ファイルを含めることで、コンポーネント アセンブリの管理を簡素化します。

> [!NOTE]
> リンクされた構成>要素は、Windows のサイド バイ サイド マニフェストを持つアプリケーションではサポートされていません。 ** \<**

## <a name="example"></a>例

次の例は、ローカル ハード ディスクに構成ファイルを含める方法を示しています。

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイル スキーマ](index.md)
