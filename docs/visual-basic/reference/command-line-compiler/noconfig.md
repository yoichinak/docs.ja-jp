---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819438"
---
# <a name="-noconfig"></a>-noconfig
コンパイラが自動的に参照していないこと、一般的に使用される指定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリまたはインポート、`System`と`Microsoft.VisualBasic`名前空間。  
  
## <a name="syntax"></a>構文  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Remarks  
 `-noconfig`オプション Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを使用してコンパイルにしないコンパイラに指示します。 Vbc.rsp ファイルを一般的に使用される参照[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリとインポート、`System`と`Microsoft.VisualBasic`名前空間。 コンパイラは、System.dll アセンブリを暗黙的に参照しない限り、`-nostdlib`オプションを指定します。 `-nostdlib`オプション Vbc.rsp でコンパイルや System.dll アセンブリの参照を自動的にコンパイラに指示します。  
  
> [!NOTE]
>  Mscorlib.dll および Microsoft.VisualBasic.dll のアセンブリは、常に参照されます。  
  
 Vbc.exe のすべてのコンパイルに含める必要がある追加のコンパイラ オプションを指定する Vbc.rsp ファイルを変更することができます (を指定する場合を除いて、`-noconfig`オプション)。 詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。  
  
 コンパイラに渡されるオプションの処理、`vbc`最後コマンドします。 そのため、コマンドラインで任意のオプションは、Vbc.rsp ファイル内の同じオプションの設定を上書きします。  
  
> [!NOTE]
>  `-noconfig`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="see-also"></a>関連項目

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
