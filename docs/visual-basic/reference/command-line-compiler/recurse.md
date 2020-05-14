---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005252"
---
# <a name="-recurse"></a>-recurse
指定したディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir`  
 任意。 検索を開始するディレクトリ。 指定しない場合は、プロジェクト ディレクトリから検索が開始されます。  
  
 `file`  
 必須です。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>Remarks  
 `-recurse` を使わなくても、ファイル名にワイルドカードを使用することで、プロジェクト ディレクトリ内の一致するすべてのファイルをコンパイルできます。 出力ファイル名が指定されていない場合、コンパイラで最初に処理される入力ファイルに基づいて、出力ファイル名が決定されます。 これは通常、コンパイルされるファイルの一覧をアルファベット順に表示したときの先頭のファイルです。 このため、出力ファイルは `-out` オプションを使用して指定することをお勧めします。  
  
> [!NOTE]
> `-recurse` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="example"></a>例  
 次のコマンドでは、現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルします。  
  
```console
vbc *.vb  
```  
  
 次のコマンドでは、`Test\ABC` ディレクトリとそれより下にあるすべてのディレクトリ内のすべての Visual Basic ファイルをコンパイルし、`Test.ABC.dll` を生成します。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
