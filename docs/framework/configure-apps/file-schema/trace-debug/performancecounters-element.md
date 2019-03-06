---
title: <performanceCounters> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 6144bcbda69b2ba799e87c3e7fa2118fbe4d9bf6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357080"
---
# <a name="performancecounters-element"></a>\<performanceCounters > 要素

パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。

 \<configuration>\
\<system.diagnostics>\
\<performanceCounters>

## <a name="syntax"></a>構文

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|filemappingsize|必須の属性です。<br /><br /> パフォーマンス カウンターが共有するグローバル メモリのバイト単位のサイズを指定します。 既定値は 524288 です。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|

## <a name="remarks"></a>Remarks

パフォーマンス カウンターでは、メモリ マップ ファイル、または共有メモリを使用して、パフォーマンス データを公開します。  インスタンスの数を一度に使用できる共有メモリのサイズを決定します。  共有メモリの 2 種類があります。 グローバルの共有メモリと個別の共有メモリです。  グローバル共有メモリは、.NET Framework バージョン 1.0 または 1.1 と共にインストールされるすべてのパフォーマンス カウンター カテゴリによって使用されます。  .NET Framework version 2.0 にインストールされているパフォーマンス カウンター カテゴリは、独自のメモリを持っている各パフォーマンス カウンター カテゴリ別の共有メモリを使用します。

グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。  既定のサイズは 524, 288 バイト、最大サイズは 33,554, 432 バイト、および最小のサイズは 32,768 バイトです。  グローバル共有メモリは、すべてのプロセスとカテゴリが共有しているために、最初の作成者は、サイズを指定します。  アプリケーション構成ファイルのサイズを定義すると、のみには、そのサイズは、アプリケーションが最初のアプリケーションを実行するパフォーマンス カウンターを原因となる場合に使用されます。  正しい場所を指定するため、`filemappingsize`値は、Machine.config ファイルです。  個々 のパフォーマンス カウンターによって、最終的に多数の異なる名前を持つパフォーマンス カウンター インスタンスが作成されている場合、グローバル共有メモリが使い果たされるグローバル共有メモリ内のメモリを解放できません。

別の共有メモリのサイズが、レジストリの DWORD FileMappingSize 値キーの hkey_local_machine \system\currentcontrolset\services\\*\<カテゴリ名 >* \Performance が参照されています。最初に、構成ファイルのグローバル共有メモリに指定された値に続きます。 FileMappingSize 値が存在しないかどうかは、別の共有メモリのサイズが 4 分の 1 に設定されて (1/4)、構成ファイルのグローバル設定です。

## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
