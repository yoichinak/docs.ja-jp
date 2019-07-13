---
title: -除外 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788896"
---
# <a name="-out-visual-basic"></a>-除外 (Visual Basic)
出力ファイルの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|必須。 コンパイラの出力ファイルの名前を作成します。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("")。|  
  
## <a name="remarks"></a>Remarks  
 作成するファイルの拡張機能と完全な名前を指定します。 .Exe ファイルを含むソース コード ファイルから、その名前は、そうでない場合、`Sub Main`プロシージャ、および .dll ファイルは、最初のソース コード ファイルからの名前を取得します。  
  
 .Exe または .dll 拡張子のないファイル名を指定するコンパイラが自動的に追加、拡張機能、指定された値に応じて、`-target`コンパイラ オプション。  
  
|設定 - アウト、Visual Studio 統合開発環境にする|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**アセンブリ名**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`出力ファイルを作成します`T2.exe`します。  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
