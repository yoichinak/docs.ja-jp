---
title: '方法: タイプ ライブラリへの参照を追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c12096739e66a47fadd89eb27e30ba3de43c7da3
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836436"
---
# <a name="how-to-add-references-to-type-libraries"></a>方法: タイプ ライブラリへの参照を追加する
Visual Studio は、タイプ ライブラリに参照を追加する際に、メタデータを含む相互運用機能アセンブリを生成します。 プライマリ相互運用機能アセンブリが使用可能な場合、Visual Studio では、新しい相互運用機能アセンブリを生成する前に既存のアセンブリが使用されます。  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio でタイプ ライブラリへの参照を追加するには  
  
1.  Windows Setup.exe ファイルで COM DLL ファイルまたは EXE ファイルがインストールされない場合は、このファイルをコンピューターにインストールします。  
  
2.  **[プロジェクト]**、**[参照の追加]** の順に選択します。  
  
3.  参照マネージャーで、**[COM]** を選択します。  
  
4.  一覧からタイプ ライブラリを選択するか、.tlb ファイルを参照します。  
  
5.  **[OK]** をクリックします。  
  
6.  ソリューション エクスプローラーで、追加した参照のショートカット メニューを開き、**[プロパティ]** を選択します。  
  
7.  **[プロパティ]** ウィンドウで、**[相互運用機能型の埋め込み]** プロパティが **[True]** に設定されていることを確認します。 その結果、Visual Studio により、COM 型の型情報が実行可能ファイルに埋め込まれ、アプリでプライマリ相互運用機能アセンブリを配置する必要がなくなります。  
  
> [!NOTE]
>  メニュー オプションおよびダイアログ ボックス オプションは、使用中の Visula Studio のバージョンによって異なる場合があります。  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>コマンド ライン コンパイルのために参照をタイプ ライブラリに追加するには  
  
1.  「[方法:相互運用機能アセンブリをタイプ ライブラリから生成する](how-to-generate-interop-assemblies-from-type-libraries.md)」の説明に従って、相互運用機能アセンブリを生成します。  
  
2.  相互運用機能アセンブリ名を指定して [/link (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/link-compiler-option.md) または [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) コンパイラ オプションを使用し、COM 型の型情報を実行可能ファイルに埋め込みます。  
  
## <a name="see-also"></a>関連項目
- [タイプ ライブラリのアセンブリとしてのインポート](importing-a-type-library-as-an-assembly.md)
- [.NET Framework への COM コンポーネントの公開](exposing-com-components.md)
- [チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [チュートリアル: Visual Studio でマネージド アセンブリからの型を埋め込む (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/link (C# コンパイラ オプション)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
