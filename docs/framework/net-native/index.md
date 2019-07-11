---
title: .NET ネイティブによるアプリのコンパイル
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660904"
---
# <a name="compiling-apps-with-net-native"></a>.NET ネイティブによるアプリのコンパイル

.NET ネイティブは、Visual Studio 2015 と以降のバージョンに含まれているビルドと Windows アプリを展開するためのプリコンパイル テクノロジです。 マネージド コード (C# または Visual Basic) で記述された、.NET Framework および Windows 10 を対象とするアプリのリリース バージョンを自動的にネイティブ コードにコンパイルします。

通常、.NET Framework を対象とするアプリは中間言語 (IL) にコンパイルされます。 実行時に、Just-In-Time (JIT) コンパイラによって IL がネイティブ コードに変換されます。 これに対し、.NET ネイティブのコンパイル、Windows アプリを直接ネイティブ コードにします。 開発者にとって、これは次のことを意味します。

- ネイティブ コードのパフォーマンスをアプリに機能します。 通常、パフォーマンスは、まず IL にコンパイルされ、JIT コンパイラでネイティブ コードにコンパイルし、コードに優れたになります。

- 引き続き C# または Visual Basic でプログラムを作成できます。

- クラス ライブラリ、自動メモリ管理とガベージ コレクション、例外処理など、.NET Framework で提供されるリソースを引き続き利用できます。

アプリのユーザーは、.NET ネイティブは、これらの利点を提供します。

- ほとんどのアプリやシナリオの実行時間が高速化します。

- アプリやシナリオの大半はスタートアップ時間が短くします。

- 配置と更新コストが低い。

- アプリのメモリ使用量を最適化します。

> [!IMPORTANT]
> 大半のアプリおよびシナリオでは、.NET ネイティブは提供が大幅に高速起動時間、または NGEN イメージに IL にコンパイルされたアプリと比較して優れたパフォーマンスを発揮します。 ただし、結果は異なる場合があります。 アプリが .NET ネイティブのパフォーマンス向上による恩恵を受けていることを確認するには、.NET ネイティブ以外のバージョンのアプリのパフォーマンスを比較する必要があります。 詳細については、次を参照してください。[パフォーマンス セッションの概要](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview)します。

.NET ネイティブは、複数のネイティブ コードにコンパイルします。 .NET Framework アプリのビルド方法と実行方法が変更されます。 特に次の点に注意してください。

- プリコンパイル時に、.NET Framework の必要な部分がアプリに静的にリンクされます。 これにより、アプリは .NET Framework のアプリ ローカルのライブラリを使用して実行でき、コンパイラはグローバル分析を実行してパフォーマンスを向上させることができます。 その結果、.NET Framework の更新後であっても、アプリは常に高速に起動します。

- .NET ネイティブ ランタイムでは、静的プリコンパイル用は最適化され、ほとんどの場合で、優れたパフォーマンスを提供します。 同時に、開発者に役立つ主要なリフレクション機能もあります。

- .NET ネイティブと同じバックエンドを使用して、C++コンパイラは静的プリコンパイル シナリオ用に最適化されています。

.NET ネイティブはパフォーマンス上の利点を提供できますC++管理している開発者のコードと同じか類似のツールを使用しているためC++内部的に、この表に示すようにします。

||.NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|ライブラリ|.NET Framework + Windows ランタイム|Win32 + Windows ランタイム|
|コンパイラ|UTC 最適化コンパイラ|UTC 最適化コンパイラ|
|配置|実行可能バイナリ|実行可能バイナリ (ASM)|
|ランタイム|MRT.dll (最小 CLR ランタイム)|CRT.dll (C ランタイム)|

Windows 10 用の Windows アプリの場合は、.NET ネイティブ コード コンパイル バイナリをアプリ パッケージ (.appx ファイル) に入れて Windows ストアにアップロードします。

## <a name="in-this-section"></a>このセクションの内容

.NET ネイティブ コード コンパイルを使用したアプリ開発の詳細については、次のトピックを参照してください。

- [.NET ネイティブの概要](../../../docs/framework/net-native/getting-started-with-net-native.md)

- [.NET ネイティブとコンパイル:](../../../docs/framework/net-native/net-native-and-compilation.md)どのネイティブ コードに、プロジェクトのコンパイルは .NET ネイティブのようにします。

- [リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [リフレクションに依存する API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [リフレクション API リファレンス](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [シリアル化とメタデータ](../../../docs/framework/net-native/serialization-and-metadata.md)

- [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [.NET ネイティブの一般的なトラブルシューティング](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
