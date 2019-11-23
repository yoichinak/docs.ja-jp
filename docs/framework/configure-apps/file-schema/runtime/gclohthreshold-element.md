---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451324"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold element

Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>構文

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br />Specifies the threshold size that causes objects to go on the large object heap.|

### <a name="enabled-attribute"></a>enabled attribute

|[値]|説明|
|-----------|-----------------|
|`nnnn`|The threshold size, in bytes, that causes objects to go on the large object heap.|

## <a name="child-elements"></a>子要素

なし。

## <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>Remarks

This setting was introduced in .NET Framework 4.8.

## <a name="see-also"></a>関連項目

- [Run-time settings schema](index.md)
- [構成ファイル スキーマ](../index.md)
- [ガベージ コレクションの基礎](../../../../standard/garbage-collection/fundamentals.md)
- [NET Core run-time config options for GC](../../../../core/run-time-config/garbage-collector.md)
