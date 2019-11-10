---
title: <GCCpuGroup> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116829"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > 要素

ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**  

## <a name="syntax"></a>構文

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br /> ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|

## <a name="enabled-attribute"></a>enabled 属性

|[値]|説明|
|-----------|-----------------|
|`false`|ガベージ コレクションは複数の CPU グループをサポートしていません。 既定値です。|
|`true`|ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>Remarks

コンピューターに複数の CPU グループがあり、サーバーのガベージコレクションが有効になっている場合 ( [\<gcServer >](gcserver-element.md)要素を参照)、この要素を有効にすると、すべての cpu グループにわたってガベージコレクションが拡張され、との作成時にすべてのコアが考慮されます。ヒープを分散しています。

> [!NOTE]
> この要素は、ガベージ コレクション スレッドにのみ適用されます。 ランタイムがすべての CPU グループにユーザースレッドを分散できるようにするには、 [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md)要素も有効にする必要があります。

## <a name="example"></a>例

次の例は、複数の CPU グループのガベージ コレクションを有効にする方法を示しています。

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [同時実行ガベージコレクションを無効にするには](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [ワークステーションとサーバーのガベージ コレクション](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
