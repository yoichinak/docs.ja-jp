---
title: <NetFx40_PInvokeStackResilience> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 318473d2913d62404c58b9d3681800ae22a9ecbf
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689851"
---
# <a name="netfx40pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience > 要素

ランタイムが実行時の不適切なプラットフォーム呼び出し宣言を自動的に修正するかどうかを指定します。これにより、マネージド コードとアンマネージド コード間の遷移が遅くなります。

\<configuration>
\<runtime>
\<NetFx40_PInvokeStackResilience>

## <a name="syntax"></a>構文

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`enabled`|必須の属性です。<br /><br /> ランタイムは不適切なプラットフォームを検出するかどうかを指定します。 宣言を呼び出すと、スタックを 32 ビット プラットフォーム上で実行時に自動的に修正します。|

## <a name="enabled-attribute"></a>enabled 属性

|値|説明|
|-----------|-----------------|
|`0`|ランタイムが高速な相互運用が検出されない、.NET Framework 4 で導入されたアーキテクチャをマーシャ リングを使用し、修正プログラムの不適切なプラットフォーム呼び出し宣言します。 既定値です。|
|`1`|不適切なプラットフォームを検出してランタイムは低速遷移は呼び出しの宣言です。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|

## <a name="remarks"></a>Remarks

この要素では、高速な相互運用マーシャ リングの実行時の回復性に対して不適切なプラットフォーム呼び出し宣言を犠牲にすることができます。

以降、.NET Framework 4 では、合理化された相互運用マーシャ リング アーキテクチャは、マネージ コードからアンマネージ コードに遷移の大幅なパフォーマンス向上を提供します。 .NET Framework の以前のバージョンでは、マーシャ リング検出レイヤーの不適切なプラットフォームが 32 ビット プラットフォーム上で宣言を起動し、スタックを自動的に固定します。 新しいマーシャ リング アーキテクチャは、この手順を排除します。 その結果、遷移は非常に高速が不適切なプラットフォーム呼び出し宣言プログラム エラーが発生することができます。

開発中に正しくない宣言を検出するためにを Visual Studio のデバッグ エクスペリエンスが改善されました。 [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)マネージ デバッグ アシスタント (MDA) は、アタッチされたデバッガーでアプリケーションを実行しているときに、宣言を呼び出すの不適切なプラットフォームに通知します。

アプリケーションが再コンパイルすることはできませんを使用できます、不適切なプラットフォームは宣言を呼び出すが、コンポーネントを使用してシナリオに対処する、`NetFx40_PInvokeStackResilience`要素。 この要素を追加すると、アプリケーション構成ファイルを`enabled="1"`遷移が遅くなりますが、.NET Framework の以前のバージョンの動作との互換モードを選択します。 .NET Framework の以前のバージョンに対してコンパイルされたアセンブリでは、この互換モードが自動的に選択されるためし、この要素は必要ありません。

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイルでのみ使用できます。

## <a name="example"></a>例

次の例はプラットフォーム呼び出しの間の遷移が遅くなりますが、アプリケーションの宣言が正しくないに対する回復を強化を有効にする方法は、管理され、アンマネージ コード。

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>関連項目

- [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
