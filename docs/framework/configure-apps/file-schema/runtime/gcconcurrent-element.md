---
title: <gcConcurrent> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674104"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent > 要素

共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。

\<configuration>
\<runtime>
\<gcConcurrent>

## <a name="syntax"></a>構文

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br /> ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|

## <a name="enabled-attribute"></a>enabled 属性

|[値]|説明|
|-----------|-----------------|
|`false`|ガベージ コレクションは同時に実行されません。|
|`true`|ガベージ コレクションを並列に実行します。 既定値です。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>Remarks

.NET Framework 4 より前の場合、ワークステーション ガベージ コレクションは、同時実行ガベージ コレクションをサポートしており、別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。 .NET Framework 4 では同時実行ガベージ コレクションはバックグラウンド GC に置き換えられており、これも別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。 .NET Framework 4.5 以降では、バックグラウンド コレクションをサーバー ガベージ コレクションで使用できるようになりました。 `<gcConcurrent>`要素はいずれかの同時実行ランタイムによって実行されるかどうかを制御またはバック グラウンドのガベージ コレクションがある場合、またはフォア グラウンドでガベージ コレクションを実行するかどうか。

### <a name="to-disable-background-garbage-collection"></a>バック グラウンド ガベージ コレクションを無効にするには

> [!WARNING]
> .NET Framework 4 以降では、同時実行ガベージ コレクションはバックグラウンド ガベージ コレクションに置き換えられています。 条件*同時*と*バック グラウンド*.NET Framework のドキュメントでは、同義です。 バックグラウンド ガベージ コレクションを無効にするには、この記事説明されているように `<gcConcurrent>` 要素を使用します。

既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。 アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。 `<gcConcurrent>` 要素の `enabled` 属性を `false` に設定すると、ランタイムは非同時実行ガベージ コレクションを使用します。これはスループットについて最適化されています。 次の構成ファイルはバック グラウンド ガベージ コレクションを無効にします。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 存在する場合、`<gcConcurrentSetting>`マシン構成ファイルで設定すると、すべての .NET Framework アプリケーションの既定値を定義します。 マシン構成ファイルの設定は、アプリケーション構成ファイルの設定をオーバーライドします。

 詳細については同時実行とバック グラウンド ガベージ コレクションを参照してください、[同時実行ガベージ コレクション](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)セクション、[ガベージ コレクションの基礎](../../../../standard/garbage-collection/fundamentals.md)記事。

## <a name="example"></a>例

次の例では、同時実行ガベージ コレクションが有効。 にします。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [ガベージ コレクションの基礎](../../../../standard/garbage-collection/fundamentals.md)
