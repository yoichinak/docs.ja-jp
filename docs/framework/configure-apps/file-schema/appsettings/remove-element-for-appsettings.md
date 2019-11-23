---
title: <appSettings> の <remove> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0695d5638589d1afe48553fe32b8d070e3938353
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119202"
---
# <a name="remove-element-for-appsettings"></a>\<appSettings > の \<remove> 要素には

カスタムアプリケーション設定を削除します。

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove**>

## <a name="syntax"></a>構文

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>属性

|         | 説明 |
| ------- | ----------- |
| **key** | 必須の属性です。<br><br>削除するキーの名前を指定します。 |

### <a name="parent-element"></a>親要素

|     | 説明 |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。 |

## <a name="child-elements"></a>子要素

None

## <a name="example"></a>例

次の例は、`ApplicationName`のカスタム構成設定を削除する方法を示しています。

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>関連項目

- [.NET Framework の構成ファイルスキーマ](../index.md)
