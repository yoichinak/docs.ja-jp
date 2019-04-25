---
title: -ターゲット (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: c91e69e3d9f17f758990b8385f6b8d0a1c03bef6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344742"
---
# <a name="-target-visual-basic"></a>-ターゲット (Visual Basic)
コンパイラの出力形式を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Remarks  
 次の表に、効果、`-target`オプション。  
  
|**Option**|**Behavior**|  
|----------------|------------------|  
|`-target:exe`|コンパイラ実行可能ファイルのコンソール アプリケーションを作成します。<br /><br /> ない場合、既定のオプションは、この`-target`オプションを指定します。 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> それ以外の場合を指定しない限り、`/out`オプション、出力ファイル名を含む入力ファイルの名前、`Sub Main`プロシージャ。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャ。|  
|`-target:library`|コンパイラがダイナミック リンク ライブラリ (DLL) を作成します。<br /><br /> ダイナミック リンク ライブラリ ファイルは、拡張子が .dll で作成されます。<br /><br /> それ以外の場合を指定しない限り、`-out`オプション、出力ファイル名は、最初の入力ファイルの名前を受け取ります。<br /><br /> DLL を作成するときに、`Sub Main`手順は必要ありません。|  
|`-target:module`|コンパイラがアセンブリに追加できるモジュールを生成します。<br /><br /> .Netmodule の拡張子を持つ出力ファイルが作成されます。<br /><br /> .NET 共通言語ランタイムは、アセンブリがないファイルを読み込むことができません。 ただし、組み込むことができます、このようなファイル、アセンブリのアセンブリ マニフェストを使用して`-reference`します。<br /><br /> 使用して両方のモジュールをアセンブリ マニフェストに組み込む必要があります 1 つのモジュール内のコードでは、別のモジュールの内部型を参照するときに`-reference`します。<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。|  
|`-target:winexe`|コンパイラ実行可能ファイルの Windows ベースのアプリケーションを作成します。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。 Windows ベースのアプリケーションは、いずれかのいずれかからユーザー インターフェイスを提供する、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラス ライブラリまたは Windows Api を使用します。<br /><br /> それ以外の場合を指定しない限り、`-out`オプション、出力ファイル名を含む入力ファイルの名前、`Sub Main`プロシージャ。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 コードが 1 つ以上のクラスがある場合、`Sub Main`プロシージャを使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャ|  
|`-target:appcontainerexe`|コンパイラで、アプリケーション コンテナーで実行する必要がある実行可能な Windows ベース アプリケーションを作成します。 この設定が使用するように設計[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]アプリケーション。<br /><br /> **Appcontainerexe**設定は、ビットの特性のフィールドを設定、[ポータブル実行可能ファイル](/windows/desktop/Debug/pe-format)ファイル。 このビットは、アプリケーション コンテナーでアプリを実行する必要があることを示します。 場合にエラーが発生したこのビットが設定されている場合、`CreateProcess`メソッドは、アプリ コンテナーの外部でアプリケーションを起動しようとしています。 このビットを設定するとは別 **-/target:appcontainerexe**と等価 **-/target:winexe**します。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> それ以外の場合を使用して指定しない限り、`-out`オプション、出力ファイル名を含む入力ファイルの名前、`Sub Main`プロシージャ。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 コードを持つ 1 つ以上のクラスに含まれるかどうか、`Sub Main`プロシージャを使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャ|  
|`-target:winmdobj`|コンパイラが、Windows ランタイム バイナリ (.winmd) ファイルに変換できる中間ファイルを作成します。 .Winmd ファイルは、マネージ言語プログラムだけでなく、JavaScript および C++ プログラムで使用できます。<br /><br /> 拡張子が .winmdobj 中間ファイルが作成されます。<br /><br /> それ以外の場合を使用して指定しない限り、`-out`オプション、出力ファイル名は、最初の入力ファイルの名前を受け取ります。 A`Sub Main`手順は必要ありません。<br /><br /> .Winmdobj ファイルが入力として使用するように設計、 <xref:Microsoft.Build.Tasks.WinMDExp> Windows メタデータ (WinMD) ファイルを生成するためのツールをエクスポートします。 WinMD ファイルは、.winmd の拡張機能を備え、JavaScript、C++、および Windows ランタイム使用して、元のライブラリと WinMD 定義から、コード両方にはが含まれています。|  
  
 指定しない限り`-target:module`、`-target`により、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]出力ファイルに追加するアセンブリのマニフェスト。  
  
 Vbc.exe の各インスタンスの生成は、最大で 1 つの出力ファイル。 コンパイラ オプションを指定する場合`-out`または`-target`1 つ以上の時間、最後の 1 つは、コンパイラが有効にします。 コンパイルですべてのファイルに関する情報は、マニフェストに追加されます。 すべての出力ファイルで作成されたものを除く`-target:module`マニフェストにアセンブリ メタデータが含まれます。 使用[Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)が出力ファイルにメタデータを表示します。  
  
 `-target` の省略形は `-t` です。  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE をターゲットに設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。   
  
2. **[アプリケーション]** タブをクリックします。  
  
3. 値を変更、**アプリケーションの種類**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`in.vb`作成、 `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-除外 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
