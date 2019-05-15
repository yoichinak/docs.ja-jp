---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588850"
---
# <a name="-noconfig"></a>-noconfig
コンパイラの自動的には、一般的に使用される .NET Framework アセンブリを参照またはインポートを指定します、`System`と`Microsoft.VisualBasic`名前空間。  
  
## <a name="syntax"></a>構文  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Remarks  
 `-noconfig`オプション Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを使用してコンパイルにしないコンパイラに指示します。 Vbc.rsp ファイルは、一般的に使用される .NET Framework アセンブリを参照し、インポート、`System`と`Microsoft.VisualBasic`名前空間。 コンパイラは、System.dll アセンブリを暗黙的に参照しない限り、`-nostdlib`オプションを指定します。 `-nostdlib`オプション Vbc.rsp でコンパイルや System.dll アセンブリの参照を自動的にコンパイラに指示します。  
  
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
