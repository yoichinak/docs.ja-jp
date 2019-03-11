---
title: Winmdexp.exe (Windows ランタイム メタデータのエクスポート ツール)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4649663338efd0cc07b435991f90ba15843cc301
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496834"
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows ランタイム メタデータのエクスポート ツール)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] メタデータ エクスポート ツール (Winmdexp.exe) は、.NET Framework モジュールを、[!INCLUDE[wrt](../../../includes/wrt-md.md)] メタデータを含むファイルに変換します。 .NET Framework アセンブリと [!INCLUDE[wrt](../../../includes/wrt-md.md)] メタデータ ファイルは同じ物理形式を使用しますが、メタデータ テーブルの内容に違いがあります。つまり、.NET Framework アセンブリは、自動的に [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントとして使用できるわけではありません。 .NET Framework モジュールを [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントにするプロセスは、*エクスポート*と呼ばれます。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] では、生成される Windows メタデータ (.winmd) ファイルにメタデータと実装の両方が含まれます。  
  
 Visual Studio 2013 または Visual Studio 2012 で、C# および Visual Basic の **Windows ストア**にある **[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネント** テンプレートを使用する場合、コンパイラのターゲットは .winmdobj ファイルであり、後続のビルド ステップで Winmdexp.exe が呼び出され、.winmdobj ファイルが .winmd ファイルにエクスポートされます。 [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントをビルドする場合は、この方法をお勧めします。 Visual Studio による制御より細かくビルド プロセスを制御する場合は、Winmdexp.exe ファイルを直接使用します。  
  
 このツールは、Visual Studio と共に自動的にインストールされます。 このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。 詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。  
  
 コマンド プロンプトに次のように入力します。  
  
## <a name="syntax"></a>構文  
  
```  
winmdexp [options] winmdmodule  
```  
  
## <a name="parameters"></a>パラメーター  
  
|引数またはオプション|説明|  
|------------------------|-----------------|  
|`winmdmodule`|エクスポートするモジュール (.winmdobj) を指定します。 指定できるのは 1 つのモジュールのみです。 このモジュールを作成するには、`/target` ターゲットと共に `winmdobj` コンパイラ オプションを使用します。 「[/target:winmdobj (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)」または「[/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md)」を参照してください。|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Winmdexp.exe が生成する出力 XML ドキュメント ファイルを指定します。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、出力ファイルは基本的に入力 XML ドキュメント ファイルと同じです。|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|コンパイラが `winmdmodule` と共に生成した XML ドキュメント ファイルの名前を指定します。|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|`winmdmodule` のシンボルを含むプログラム データベース (PDB) ファイルの名前を指定します。|  
|`/nowarn:` `warning`|指定した警告番号が使用されなくなります。 *warning* の場合は、エラー コードの数字部分だけを先行ゼロなしで指定してください。|  
|`/out:` `file`<br /><br /> `/o:` `file`|出力 Windows メタデータ (.winmd) ファイルの名前を指定します。|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|エクスポートされた Windows メタデータ (.winmd) ファイルのシンボルを含む出力プログラム データベース (PDB) ファイルの名前を指定します。|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|エクスポート時に参照するメタデータ ファイル (.winmd またはアセンブリ) を指定します。 「\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5」(32 ビット コンピューターでは「\Program Files\\...」) にある参照アセンブリを使用する場合は、System.Runtime.dll と mscorlib.dll の両方への参照を含めます。|  
|`/utf8output`|UTF-8 エンコードでメッセージが出力される必要があることを指定します。|  
|`/warnaserror+`|すべての警告をエラーとして扱うよう指定しています。|  
|**@** `responsefile`|オプション (および、必要に応じて `winmdmodule`) を含む応答 (.rsp) ファイルを指定します。 `responsefile` の各行に 1 つの引数またはオプションが含まれている必要があります。|  
  
## <a name="remarks"></a>解説  
 Winmdexp.exe は、任意の .NET Framework アセンブリを .winmd ファイルに変換するようには設計されていません。 `/target:winmdobj` オプションでコンパイルされるモジュールが必要で、追加の制限が適用されます。 この中で最も重要な制限は、アセンブリの API サーフェイスで公開されるすべての型は必ず [!INCLUDE[wrt](../../../includes/wrt-md.md)] 型であるということです。 詳細については、Windows デベロッパー センターの記事「[C# および Visual Basic での Windows ランタイム コンポーネントの作成](https://go.microsoft.com/fwlink/p/?LinkID=238313)」の「Windows ランタイム コンポーネントの宣言型」セクションを参照してください。  
  
 C# または Visual Basic で [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリまたは [!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントを作成する場合は、[!INCLUDE[wrt](../../../includes/wrt-md.md)] でのプログラミングをより自然にするためのサポートが .NET Framework で提供されています。 これは、記事「[Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)」で解説されています。 プロセスでは、一般的に使用される [!INCLUDE[wrt](../../../includes/wrt-md.md)] 型が .NET Framework 型にマップされます。 Winmdexp.exe は、このプロセスを反転し、対応する [!INCLUDE[wrt](../../../includes/wrt-md.md)] 型を使用する API サーフェイスを生成します。 たとえば、<xref:System.Collections.Generic.IList%601> インターフェイスから構築された型は、[!INCLUDE[wrt](../../../includes/wrt-md.md)][IVector\<T>](https://go.microsoft.com/fwlink/p/?LinkId=251132) インターフェイスから構築された型にマップされます。  
  
## <a name="see-also"></a>関連項目
- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [C# および Visual Basic での Windows ランタイム コンポーネントの作成](https://go.microsoft.com/fwlink/p/?LinkID=238313)
- [Winmdexp.exe のエラー メッセージ](../../../docs/framework/tools/winmdexp-exe-error-messages.md)
- [ビルド ツール、配置ツール、および構成ツール (.NET Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd233108(v=vs.100))
