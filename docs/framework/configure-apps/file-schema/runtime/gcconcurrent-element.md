---
title: gcコンカレント要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400981"
---
# <a name="gcconcurrent-element"></a>\<gcコンカレント>要素

共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。

[\<構成>](../configuration-element.md)\
&nbsp;&nbsp;[\<ランタイム>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gc同時実行>

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
|`enabled`|必須の属性です。<br /><br />ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|

#### <a name="enabled-attribute"></a>有効な属性

|Value|説明|
|-----------|-----------------|
|`false`|ガベージ コレクションを同時に実行しません。|
|`true`|ガベージ コレクションを並列に実行します。 これは既定値です。|

### <a name="child-elements"></a>子要素

[なし] :

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|

## <a name="remarks"></a>解説

.NET Framework 4 より前のバージョンでは、ワークステーションのガベージ コレクションは、別のスレッドでバックグラウンドでガベージ コレクションを実行する同時実行ガベージ コレクションをサポートしました。 NET Framework 4 では、同時実行ガベージ コレクションはバックグラウンド GC に置き換えられました。 NET Framework 4.5 以降、サーバー のガベージ コレクションでバックグラウンド コレクションを使用で使用するようになりました。 **gcConcurrent**要素は、ランタイムが同時実行ガベージ コレクションとバックグラウンド ガベージ コレクションのどちらを実行するか (使用可能な場合)、またはフォアグラウンドでガベージ コレクションを実行するかどうかを制御します。

### <a name="to-disable-background-garbage-collection"></a>バックグラウンド ガベージ コレクションを無効にするには

> [!WARNING]
> NET Framework 4 以降、同時実行ガベージ コレクションはバックグラウンド ガベージ コレクションに置き換えられました。 *同時実行*と*背景*という用語は、.NET Framework ドキュメントで同じ意味で使用されます。 バックグラウンド ガベージ コレクションを無効にするには、この記事で説明するように**gcConcurrent**要素を使用します。

既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。 アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。 **gcConcurrent**要素`enabled`の属性を に`false`設定すると、ランタイムはスループットに最適化された非同時実行ガベージ コレクションを使用します。

次の構成ファイルは、バックグラウンド ガベージ コレクションを無効にします。

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

マシン構成ファイルに**gcConcurrentSetting 設定**がある場合は、すべての .NET Framework アプリケーションの既定値が定義されます。 マシン構成ファイルの設定は、アプリケーション構成ファイルの設定をオーバーライドします。

同時実行ガベージ コレクションとバックグラウンド ガベージ コレクションの詳細については、「ガベージ コレクション[の基礎](../../../../standard/garbage-collection/fundamentals.md)」の「[コンカレント ガベージ コレクション](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection)」、[バックグラウンド ワークステーションのガベージ コレクション](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)、およびバックグラウンド サーバーのガベージ[コレクション](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection)のセクションを参照してください。

## <a name="example"></a>例

次の例では、バックグラウンド ガベージ コレクションを有効にします。

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
