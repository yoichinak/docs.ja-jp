---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956273"
---
# <a name="-recurse"></a>-recurse
指定されたディレクトリまたはプロジェクトディレクトリのすべての子ディレクトリにあるソースコードファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  
 `dir`  
 任意。 検索を開始するディレクトリ。 指定しない場合は、プロジェクトディレクトリから検索が開始されます。  
  
 `file`  
 必須。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>Remarks  
 `-recurse` を使用せずにプロジェクト ディレクトリ内の一致するすべてのファイルをコンパイルするには、ワイルドカードを使用できます。 出力ファイル名が指定されない場合、コンパイラは処理する最初の入力ファイルに基づいて出力ファイル名を決定します。 これは一般に、コンパイルされるファイルの一覧をアルファベット順に表示したときの先頭のファイルです。 この理由から、出力ファイルは `-out` オプションを使用して指定するのが最善です。  
  
> [!NOTE]
> この`-recurse`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコマンドは、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。  
  
```console
vbc *.vb  
```  
  
 次のコマンドは、 `Test\ABC`ディレクトリ内のすべての Visual Basic ファイルとその下のすべてのディレクトリをコンパイルし、を生成`Test.ABC.dll`します。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
