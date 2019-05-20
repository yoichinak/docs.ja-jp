---
title: '方法: シングルファイル アセンブリをビルドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a409a93e5d84e96bbab13f2f6268d7f7ce6464ed
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634242"
---
# <a name="how-to-build-a-single-file-assembly"></a>方法: シングルファイル アセンブリをビルドする

アセンブリの最も単純な形式であるシングルファイル アセンブリには、型の情報、実装、[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)が含まれています。 コマンド ライン コンパイラや Visual Studio を利用し、シングルファイル アセンブリを作成できます。 既定では、コンパイラは .exe 拡張子でアセンブリ ファイルを作成します。

> [!NOTE]
> C# と Visual Basic の Visual Studio は、シングルファイル アセンブリの作成にのみ使用できます。 マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは Visual C++ を使用する必要があります。

次の手順は、コマンド ライン コンパイラでシングルファイル アセンブリを作成する方法です。

## <a name="to-create-an-assembly-with-an-exe-extension"></a>拡張子が .exe のアセンブリを作成するには

1. コマンド プロンプトに次のコマンドを入力します。

     \<*コンパイラ コマンド*> \<*モジュール名*>

     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。

 次の例では、`myCode` という名前のコード モジュールから `myCode.exe` という名前のアセンブリが作成されます。

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>拡張子が .exe のアセンブリを作成し、出力ファイル名を指定するには

1. コマンド プロンプトに次のコマンドを入力します。

     \<*コンパイラ コマンド*> **/out:**\<*ファイル名*> \<*モジュール名*>

     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンド、*ファイル名*は出力ファイル名、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。

 次の例では、`myCode` という名前のコード モジュールから `myAssembly.exe` という名前のアセンブリが作成されます。

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>ライブラリ アセンブリを作成する
 ライブラリ アセンブリはクラス ライブラリに似ています。 他のアセンブリにより参照される型が含まれますが、実行を開始するためのエントリ ポイントがありません。

### <a name="to-create-a-library-assembly"></a>ライブラリ アセンブリを作成するには

1. コマンド プロンプトに次のコマンドを入力します。

     \<*コンパイラ コマンド*> **/t:library** \<*モジュール名*>

     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。 **/out:** オプションなど、他のコンパイラ オプションも使用できます。

 次の例では、`myCode` という名前のコード モジュールから `myCodeAssembly.dll` という名前のライブラリ アセンブリが作成されます。

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>関連項目

- [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)
- [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)
- [方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
