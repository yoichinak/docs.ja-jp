---
title: '方法: .NET Framework シングルファイル アセンブリをビルドする'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991243"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>方法: .NET Framework シングルファイル アセンブリをビルドする

アセンブリの最も単純な形式であるシングルファイル アセンブリには、型の情報、実装、[アセンブリ マニフェスト](../../standard/assembly/manifest.md)が含まれています。 コマンド ライン コンパイラや Visual Studio を利用し、.NET Framework を対象とするシングルファイル アセンブリを作成できます。 既定では、コンパイラでは *.exe* 拡張子でアセンブリ ファイルが作成されます。

> [!NOTE]
> C# と Visual Basic の Visual Studio は、シングルファイル アセンブリの作成にのみ使用できます。 マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは Visual C++ を使用する必要があります。

次の手順は、コマンド ライン コンパイラでシングルファイル アセンブリを作成する方法です。

## <a name="create-an-assembly-with-an-exe-extension"></a>拡張子が .exe のアセンブリを作成する

コマンド プロンプトに次のコマンドを入力します。

\<*コンパイラ コマンド*> \<*モジュール名*>

このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。

次の例では、`myCode` というコード モジュールから *myCode.exe* という名前のアセンブリが作成されます。

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>拡張子が .exe のアセンブリを作成し、出力ファイル名を指定する

コマンド プロンプトに次のコマンドを入力します。

\<*コンパイラ コマンド*>  **/out:** \<*ファイル名*> \<*モジュール名*>

このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンド、*ファイル名*は出力ファイル名、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。

次の例では、`myCode` というコード モジュールから *myAssembly.exe* という名前のアセンブリが作成されます。

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>ライブラリ アセンブリを作成する
 ライブラリ アセンブリはクラス ライブラリに似ています。 他のアセンブリにより参照される型が含まれますが、実行を開始するためのエントリ ポイントがありません。

ライブラリ アセンブリを作成するには、コマンド プロンプトで次のコマンドを入力します。

\<*コンパイラ コマンド*>  **/t:library** \<*モジュール名*>

このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。 **/out:** オプションなど、他のコンパイラ オプションも使用できます。

次の例では、`myCode` というコード モジュールから *myCodeAssembly.dll* という名前のライブラリ アセンブリが作成されます。

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>関連項目

- [アセンブリを作成する](../../standard/assembly/create.md)
- [マルチファイル アセンブリ](multifile-assemblies.md)
- [方法: マルチファイル アセンブリをビルドする](build-multifile-assembly.md)
- [アセンブリを使用したプログラム](../../standard/assembly/program.md)
