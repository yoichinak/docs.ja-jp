---
title: <GCCpuGroup> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102893"
---
# <a name="gccpugroup-element"></a>\<>要素

ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<ランタイム>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>**

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

|値|説明|
|-----------|-----------------|
|`false`|ガベージ コレクションは複数の CPU グループをサポートしていません。 これは既定値です。|
|`true`|ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。|

### <a name="child-elements"></a>子要素

[なし] :

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>解説

コンピュータに複数の CPU グループがあり、サーバー のガベージ コレクションが有効になっている場合[\<(gcServer>](gcserver-element.md)要素を参照)、この要素を有効にすると、すべての CPU グループにガベージ コレクションが拡張され、ヒープの作成とバランスをとるときにすべてのコアが考慮されます。

> [!NOTE]
> この要素は、ガベージ コレクション スレッドにのみ適用されます。 ランタイムがユーザー・スレッドをすべての CPU グループに分散できるようにするには[\<、Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)エレメントも有効にする必要があります。

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
- [同時実行ガベージ コレクションを無効にする](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [ワークステーションとサーバーのガベージ コレクション](../../../../standard/garbage-collection/workstation-server-gc.md)
