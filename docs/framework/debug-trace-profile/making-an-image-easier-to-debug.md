---
title: イメージを .NET でデバッグしやすきます。
description: IDE を使用してデバッグを容易に切り替えるは、実行可能イメージを構成する方法とコマンド ライン オプションについて説明します。
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bab707afb059d4fcbd46a9ee54edead991be523
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362015"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>イメージを .NET でデバッグしやすきます。

アンマネージ コードをコンパイルするときは、IDE スイッチまたはコマンド ライン オプションを使用して、デバッグ用の実行可能イメージを構成できます。 たとえば、Visual C++ で /**Zi** コマンド ライン オプションを使用すると、デバッグ シンボル ファイル (拡張子 .pdb) が生成されます。 同様に、/**Od** コマンド ライン オプションを使用すると、コンパイラは最適化処理を無効にします。 結果のコードの実行速度が遅く、方が簡単ですをデバッグするにはこの必要となります。

マネージ コードを .NET Framework をコンパイルするときに、Visual C、Visual Basic、および C# などのコンパイラは、Microsoft intermediate language (MSIL) にそのソース プログラムをコンパイルします。 MSIL は、ネイティブ マシン コードに、実行される直前に、JIT でコンパイルします。 アンマネージ コードでは、IDE スイッチまたはコマンド ライン オプションを設定することにより、デバッグ用の実行可能イメージを構成できます。 ほぼ同じ方法でのデバッグ用の JIT コンパイルを構成することもできます。

このような目的で JIT を構成する場合、次の 2 つの要素が関係してきます。

- 追跡情報を生成する、JIT コンパイラを要求することができます。 追跡情報を生成すると、デバッガーは、MSIL のチェインをマシン語コードの対応部分に対応させたり、ローカル変数と関数の引数が格納される位置を追跡したりできるようになります。 以降、.NET Framework version 2.0 では、JIT コンパイラ必ず生成します追跡情報を要求する必要はありません。

- いない結果として得られるマシン語コードを最適化するために、JIT コンパイラを要求することができます。

通常、MSIL を生成するコンパイラこれらの JIT コンパイラ オプション、適切に設定された IDE スイッチまたはコマンド ライン オプションを指定すると、たとえば、に基づいて/**Od**します。

場合によっては、JIT コンパイラが生成するマシン語コードをデバッグしやすくするために、JIT コンパイラの動作の変更が必要となることがあります。 たとえば、製品版またはコントロールを最適化するために JIT 追跡情報の生成が必要となる場合などです。 このような場合は、初期化 (.ini) ファイルを使用します。

たとえば、アセンブリをデバッグする場合が呼び出されます*MyApp.exe*、という名前のテキスト ファイルを作成し、 *MyApp.ini*と同じフォルダーに*MyApp.exe*が含まれています次の 3 行:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

各オプションの値として、0 または 1 を設定できます。記述しなかったオプションの値は、既定値の 0 に設定されます。 `GenerateTrackingInfo` を 1 に設定し、`AllowOptimize` を 0 に設定すると、デバッグが最も簡単になります。

以降、.NET Framework version 2.0 では、JIT コンパイラ常に生成の値に関係なく追跡情報`GenerateTrackingInfo`。 ただし、、`AllowOptimize`値は引き続き効力を持ちます。 [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) を使用して最適化を行わずにネイティブ イメージをプリコンパイルする場合は、`AllowOptimize=0` が記述された .ini ファイルが、Ngen.exe 実行時にターゲット フォルダー内に存在している必要があります。 最適化を行わずにアセンブリをプリコンパイルする場合は、NGen.exe を使用してプリコンパイルされたコードを削除する必要があります **/uninstall** Ngen.exe を再度実行する前に最適化、コードをプリコンパイルするためのオプション。 .Ini ファイルがフォルダーに存在しない場合は、既定では Ngen.exe プリコンパイル コード最適化します。

アセンブリの設定は、<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> によって制御されます。 **DebuggableAttribute** JIT コンパイラの最適化や追跡情報を生成する必要があるかどうか 2 つのフィールドにはコントロールが含まれます。 以降、.NET Framework version 2.0 では、JIT コンパイラは常に、追跡情報を生成します。

製品版ビルドでは、コンパイラはありませんも設定**DebuggableAttribute**します。 既定では、JIT コンパイラは、マシン語コードのデバッグが困難な最高のパフォーマンスを生成します。 JIT 追跡を有効にすると、パフォーマンスが多少低下します。最適化処理を無効にすると、パフォーマンスは大幅に低下します。

**DebuggableAttribute** は、アセンブリに含まれる個々のモジュールではなく、アセンブリ全体に適用されます。 そのため開発ツールでは、アセンブリが既に作成されている場合は、カスタム属性をアセンブリのメタデータ トークン、または **System.Runtime.CompilerServices.AssemblyAttributesGoHere** というクラスに追加できる必要があります。 これらは、ALink ツールが、昇格**DebuggableAttribute**各モジュールからアセンブリへの属性の一部になります。 競合がある場合、ALink の操作が失敗します。

> [!NOTE]
> .NET Framework Version 1.0 では、**/clr** および **/Zi** コンパイラ オプションを指定すると、Microsoft Visual C++ コンパイラによって **DebuggableAttribute** が追加されます。 .NET Framework version 1.1 で追加する、 **DebuggableAttribute**に手動でコードの使用、 **/ASSEMBLYDEBUG**リンカー オプション。

## <a name="see-also"></a>関連項目

- [デバッグ、トレース、およびプロファイリング](../../../docs/framework/debug-trace-profile/index.md)
- [JIT アタッチ デバッグの有効化](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [プロファイルの有効化](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
