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
ms.openlocfilehash: 6900bca2bd94f52ea5603c752681163cde52ce19
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457308"
---
# <a name="compiling-apps-with-net-native"></a>.NET ネイティブによるアプリのコンパイル
[!INCLUDE[net_native](../../../includes/net-native-md.md)] Visual Studio 2015 およびそれ以降のバージョンに含まれているプリコンパイル テクノロジを構築および Windows アプリを展開するためです。 マネージ コード (C# または Visual Basic) で記述された、.NET Framework および Windows 10 を対象とするアプリのリリース バージョンを自動的にネイティブ コードにコンパイルします。  
  
 通常、.NET Framework を対象とするアプリは中間言語 (IL) にコンパイルされます。 実行時に、Just-In-Time (JIT) コンパイラによって IL がネイティブ コードに変換されます。 これに対し、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] は、Windows アプリを直接ネイティブ コードにコンパイルします。 開発者にとって、これは次のことを意味します。  
  
-   ネイティブ コードのパフォーマンスをアプリに機能します。 通常、パフォーマンスは IL に最初にコンパイルされ、JIT コンパイラによるネイティブ コードにコンパイルし、コードをより上位になります。 
  
-   引き続き C# または Visual Basic でプログラムを作成できます。  
  
-   クラス ライブラリ、自動メモリ管理とガベージ コレクション、例外処理など、.NET Framework で提供されるリソースを引き続き利用できます。  
  
 アプリのユーザーにとっては、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] には次のような利点があります。  
  
-   ほとんどのアプリとシナリオの実行時間が短縮します。
  
-   ほとんどのアプリとシナリオのスタートアップに時間が高速化します。 
  
-   配置と更新コストが低い。  
  
-   アプリのメモリ使用量を最適化します。  

> [!IMPORTANT]
> ほとんどのアプリとのシナリオでは、.NET ネイティブではスタートアップに時間が大幅に高速と IL をまたは NGEN イメージにコンパイルされたアプリを比較した場合にパフォーマンスが優れています。 ただし、結果は異なる場合があります。 アプリが .NET ネイティブのパフォーマンス向上の恩恵を受けていることを確認するには、.NET ネイティブ以外のバージョンのアプリのパフォーマンスを比較する必要があります。 詳細については、[パフォーマンス セッションの概要](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview)を参照してください。
 
ただし、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] では、ネイティブ コードへのコンパイル以上の操作が行われます。 .NET Framework アプリのビルド方法と実行方法が変更されます。 特に次の点に注意してください。  
  
-   プリコンパイル時に、.NET Framework の必要な部分がアプリに静的にリンクされます。 これにより、アプリは .NET Framework のアプリ ローカルのライブラリを使用して実行でき、コンパイラはグローバル分析を実行してパフォーマンスを向上させることができます。 その結果、.NET Framework の更新後であっても、アプリは常に高速に起動します。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]ランタイムは静的プリコンパイル用に最適化されたおよびほとんどの場合に、優れたパフォーマンスを提供します。 同時に、開発者に役立つ主要なリフレクション機能もあります。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] は、静的プリコンパイル シナリオ用に最適化されている、C++ コンパイラと同じバックエンドを使用します。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] は、この表に示すように、内部で C++ と同じか類似のツールを使用しているため、マネージド コードの開発者に C++ のパフォーマンス上の利点を提供できます。  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|ライブラリ|.NET Framework + Windows ランタイム|Win32 + Windows ランタイム|  
|コンパイラ|UTC 最適化コンパイラ|UTC 最適化コンパイラ|  
|配置|実行可能バイナリ|実行可能バイナリ (ASM)|  
|ランタイム|MRT.dll (最小 CLR ランタイム)|CRT.dll (C ランタイム)|  
  
 Windows 10 用の Windows アプリの場合は、.NET ネイティブ コード コンパイル バイナリをアプリ パッケージ (.appx ファイル) に入れて Windows ストアにアップロードします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 .NET ネイティブ コード コンパイルを使用したアプリ開発の詳細については、次のトピックを参照してください。  
  
-   [.NET ネイティブの概要](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET ネイティブとコンパイル:](../../../docs/framework/net-native/net-native-and-compilation.md) .NET ネイティブがプロジェクトをネイティブ コードにコンパイルする方法を取り上げます。  
  
-   [リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [リフレクションに依存する API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [リフレクション API リファレンス](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [シリアル化とメタデータ](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [.NET ネイティブの一般的なトラブルシューティング](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
