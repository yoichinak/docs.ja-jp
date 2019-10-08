---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 2d7ccfc6b033a9021e683a4a2501ca2ccc29956d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004940"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
コンパイラ出力の形式を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>コメント  
 次の表は、`-target` オプションの効果をまとめたものです。  
  
|**Option**|**Behavior**|  
|----------------|------------------|  
|`-target:exe`|コンパイラによって実行可能なコンソールアプリケーションが作成されます。<br /><br /> これは、`-target` オプションが指定されていない場合の既定のオプションです。 実行可能ファイルは .exe 拡張子を使用して作成されます。<br /><br /> @No__t-0 オプションで特に指定しない限り、出力ファイル名は、`Sub Main` プロシージャを含む入力ファイルの名前になります。<br /><br /> .Exe ファイルにコンパイルされるソースコードファイルには、1つの `Sub Main` プロシージャのみが必要です。 @No__t-0 コンパイラオプションを使用して、`Sub Main` プロシージャを含むクラスを指定します。|  
|`-target:library`|コンパイラによってダイナミックリンクライブラリ (DLL) が作成されます。<br /><br /> ダイナミックリンクライブラリファイルは、.dll 拡張子を使用して作成されます。<br /><br /> @No__t-0 オプションで特に指定しない限り、出力ファイル名は最初の入力ファイルの名前になります。<br /><br /> DLL をビルドする場合、@no__t 0 のプロシージャは必要ありません。|  
|`-target:module`|アセンブリに追加できるモジュールをコンパイラによって生成します。<br /><br /> 出力ファイルは、.netmodule の拡張子を使用して作成されます。<br /><br /> .NET 共通言語ランタイムは、アセンブリのないファイルを読み込むことができません。 ただし、このようなファイルは、`-reference` を使用してアセンブリのアセンブリマニフェストに組み込むことができます。<br /><br /> あるモジュールのコードが別のモジュールの内部型を参照する場合は、`-reference` を使用して、両方のモジュールをアセンブリマニフェストに組み込む必要があります。<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。|  
|`-target:winexe`|コンパイラによって、実行可能な Windows ベースのアプリケーションが作成されます。<br /><br /> 実行可能ファイルは .exe 拡張子を使用して作成されます。 Windows ベースのアプリケーションは、.NET Framework クラスライブラリまたは Windows Api のいずれかからユーザーインターフェイスを提供するアプリケーションです。<br /><br /> @No__t-0 オプションで特に指定しない限り、出力ファイル名は、`Sub Main` プロシージャを含む入力ファイルの名前になります。<br /><br /> .Exe ファイルにコンパイルされるソースコードファイルには、1つの `Sub Main` プロシージャのみが必要です。 コードに @no__t 0 のプロシージャを持つクラスが複数ある場合は、`-main` コンパイラオプションを使用して、`Sub Main` プロシージャを含むクラスを指定します。|  
|`-target:appcontainerexe`|アプリコンテナーで実行する必要がある実行可能な Windows ベースのアプリケーションをコンパイラで作成します。 この設定は @no__t 0 のアプリケーションに使用するように設計されています。<br /><br /> **Appcontainerexe**設定は、[移植可能な実行可能](/windows/desktop/Debug/pe-format)ファイルの特性フィールドにビットを設定します。 このビットは、アプリがアプリコンテナーで実行される必要があることを示します。 このビットが設定されている場合、@no__t 0 のメソッドがアプリコンテナーの外部でアプリケーションを起動しようとすると、エラーが発生します。 **-Target: appcontainerexe**は、このビット設定とは別に、 **-target: winexe**に相当します。<br /><br /> 実行可能ファイルは .exe 拡張子を使用して作成されます。<br /><br /> @No__t-0 オプションを使用して指定しない限り、出力ファイル名には、`Sub Main` プロシージャを含む入力ファイルの名前が使用されます。<br /><br /> .Exe ファイルにコンパイルされるソースコードファイルには、1つの `Sub Main` プロシージャのみが必要です。 コードに @no__t 0 のプロシージャを持つクラスが複数含まれている場合は、`-main` コンパイラオプションを使用して、`Sub Main` プロシージャを含むクラスを指定します。|  
|`-target:winmdobj`|コンパイラによって、Windows ランタイムバイナリ (winmd) ファイルに変換できる中間ファイルが作成されます。 Winmd ファイルは、マネージ言語プログラムに加えてC++ 、JavaScript とプログラムでも使用できます。<br /><br /> 中間ファイルは、winmdobj 拡張子を使用して作成されます。<br /><br /> @No__t-0 オプションを使用して指定しない限り、出力ファイル名は最初の入力ファイルの名前になります。 @No__t 0 のプロシージャは必要ありません。<br /><br /> Winmdobj ファイルは、Windows メタデータ (WinMD) ファイルを生成するために <xref:Microsoft.Build.Tasks.WinMDExp> エクスポートツールの入力として使用されるように設計されています。 WinMD ファイルには、winmd という拡張子が付いており、元のライブラリのコードと、JavaScript、 C++、および Windows ランタイムが使用する winmd の定義の両方が含まれています。|  
  
 @No__t-0 を指定しない限り、`-target` を指定すると、.NET Framework のアセンブリマニフェストが出力ファイルに追加されます。  
  
 Vbc.exe の各インスタンスは、最大で1つの出力ファイルを生成します。 @No__t-0 や `-target` などのコンパイラオプションを複数回指定した場合、コンパイラが処理する最後のオプションは有効になります。 コンパイル内のすべてのファイルに関する情報がマニフェストに追加されます。 @No__t-0 で作成されたものを除くすべての出力ファイルには、マニフェスト内のアセンブリメタデータが含まれます。 [Ildasm.exe (IL 逆アセンブラー)](../../../framework/tools/ildasm-exe-il-disassembler.md)を使用して、出力ファイル内のメタデータを表示します。  
  
 `-target` の省略形は `-t` です。  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE で-target を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。   
  
2. **[アプリケーション]** タブをクリックします。  
  
3. **[アプリケーションの種類]** ボックスの値を変更します。  
  
## <a name="example"></a>例  
 次のコードは `in.vb` をコンパイルし、`in.dll` を作成します。  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
