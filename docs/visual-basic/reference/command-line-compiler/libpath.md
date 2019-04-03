---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b8e28b821f6536ddb5c7612e8706e024dd79a0bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833316"
---
# <a name="-libpath"></a>-libpath
参照先アセンブリの場所を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`dirList`|必須。 場合に参照アセンブリを検索するコンパイラ用のディレクトリのセミコロン区切りのリストに含まれていないか、現在の作業ディレクトリ (コンパイラの起動元のディレクトリ) または共通言語ランタイムのシステム ディレクトリ。 ディレクトリ名にスペースが含まれている場合は、名前を引用符で囲みます ("")。|  
  
## <a name="remarks"></a>Remarks  
 `-libpath`オプションによって参照されるアセンブリの場所を指定する、 [-参照](../../../visual-basic/reference/command-line-compiler/reference.md)オプション。  
  
 コンパイラは、完全に修飾されていないアセンブリ参照を次の順序で検索します。  
  
1.  現在の作業ディレクトリ。 これは、コンパイラを起動したディレクトリです。  
  
2.  共通言語ランタイムのシステム ディレクトリ。  
  
3.  によって指定されたディレクトリ`/libpath`します。  
  
4.  LIB 環境変数によって指定されているディレクトリ。  
  
 `-libpath`オプションが指定するには複数を指定すると、前の値に 1 回追加します。  
  
 使用`-reference`アセンブリ参照を指定します。  
  
|Visual Studio で/libpath を設定するのには、統合開発環境|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[参照]** タブをクリックします。<br />3.をクリックして、**パスを参照しています.** ボタンをクリックします。<br />4.**参照パス** ダイアログ ボックスで、ディレクトリ名を入力、**フォルダー:** ボックス。<br />5.クリックして**フォルダーの追加**します。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`.exe ファイルを作成します。 コンパイラは、アセンブリ参照の作業ディレクトリ、c: ドライブのルート ディレクトリおよび c: ドライブの新しいアセンブリのディレクトリを検索します。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](../../../standard/assembly/index.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
