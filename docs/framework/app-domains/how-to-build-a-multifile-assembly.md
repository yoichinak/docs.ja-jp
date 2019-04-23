---
title: '方法: マルチファイル アセンブリをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcc451903f7fbf7f82e2ed64834d26e605a0c069
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187799"
---
# <a name="how-to-build-a-multifile-assembly"></a>方法: マルチファイル アセンブリをビルドする
この記事では、マルチファイル アセンブリを作成する方法を説明し、プロシージャの各手順を示すコードを提供します。

> [!NOTE]
> Visual Studio IDE for C# および Visual Basic は、シングルファイル アセンブリの作成でしか使用できません。 マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは Visual C++ 付き Visual Studio を使用する必要があります。

### <a name="to-create-a-multifile-assembly"></a>マルチファイル アセンブリを作成するには、次のようにします。

01. アセンブリ内のほかのモジュールによって参照される名前空間を含むすべてのファイルをコンパイルして、コード モジュールを生成します。 コード モジュールの既定の拡張子は .netmodule です。

    たとえば、`Stringer` ファイルに `myStringer` と呼ばれるクラスを含む `Stringer` という名前空間があるとします。 `Stringer` クラスには、コンソールに 1 つの行を書き込む `StringerMethod` メソッドが含まれます。

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    このコードをコンパイルするには、次のコマンドを使用します。

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    *module* パラメーターと **/t:** コンパイラ オプションを指定すると、ファイルはアセンブリではなくモジュールとしてコンパイルされます。 コンパイラは、アセンブリに追加できる `Stringer.netmodule` モジュールを生成します。

02. コード内で参照されるほかのモジュールを示すために必要なコンパイラ オプションを使用して、ほかのすべてのモジュールをコンパイルします。 この手順では、**/addmodule** コンパイラ オプションを使用します。

    次の例では、`Client` コード モジュールに、手順 1. で作成した `Main` モジュール内のメソッドを参照するエントリ ポイント `Stringer.dll` メソッドがあります。

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    このコードをコンパイルするには、次のコマンドを使用します。

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    このモジュールは後の手順でアセンブリに追加するため、**/t:module** オプションを指定します。 `Client` 内のコードが `Stringer.netmodule` 内のコードによって作成された名前空間を参照するため、**/addmodule** オプションを指定します。 コンパイラは、`Client.netmodule` という別のモジュールへの参照を格納する `Stringer.netmodule` モジュールを生成します。

    >[!NOTE]
    >C# コンパイラと Visual Basic コンパイラは、マルチファイル アセンブリを直接作成する場合、次の 2 種類の構文を使用します。
    >
    >- 2 回のコンパイルで、2 ファイルのアセンブリを作成する。
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >    [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- 1 回のコンパイルで、2 ファイルのアセンブリを作成する。
    >
    >    [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >    [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >    [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. [アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用して、アセンブリ マニフェストを格納する出力ファイルを作成します。 このファイルは、アセンブリの一部であるすべてのモジュールまたはリソースについての参照情報を格納します。

    コマンド プロンプトに次のコマンドを入力します。

    **al** \<*module name*> \<*module name*> … **/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*>

    このコマンドで、*module name* 引数はアセンブリに含める各モジュールの名前を指定します。 **/main:** オプションは、アセンブリのエントリ ポイントであるメソッド名を指定します。 **/out:** オプションは、アセンブリ メタデータを格納する出力ファイルの名前を指定します。 **/target:** オプションは、アセンブリがコンソール アプリケーション実行可能ファイル (.exe)、Windows 実行可能ファイル (.win)、またはライブラリ ファイル (.lib) であることを指定します。

    Al.exe を使用して、コンソール アプリケーションを実行する `myAssembly.exe` という名前のアセンブリを作成する例を次に示します。 このアプリケーションは、`Client.netmodule` と `Stringer.netmodule` の 2 つのモジュール、およびアセンブリ メタデータだけを格納する実行可能ファイル `myAssembly.exe,` で構成されます。 アセンブリのエントリ ポイントは `Main` クラスの `MainClientApp` メソッドで、`Client.dll` 内に配置されています。

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    [MSIL 逆アセンブラー (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用すると、アセンブリの内容を調査したり、ファイルがアセンブリであるかモジュールであるかを判断したりできます。

## <a name="see-also"></a>関連項目

- [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)
- [方法: アセンブリの内容を表示する](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)
