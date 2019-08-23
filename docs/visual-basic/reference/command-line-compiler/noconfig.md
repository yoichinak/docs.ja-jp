---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ca184fa130d62dc118d0de551ac58f3165064029
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964393"
---
# <a name="-noconfig"></a>-noconfig
コンパイラが、一般的に使用される .NET Framework アセンブリを自動的に参照したり`System` 、 `Microsoft.VisualBasic`名前空間および名前空間をインポートしたりしないように指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Remarks  
 オプション`-noconfig`は、vbc.exe ファイルと同じディレクトリにある vbc.exe ファイルでコンパイルしないようにコンパイラに指示します。 Vbc.exe ファイルは、一般的に使用される .NET Framework アセンブリを参照し`System` 、 `Microsoft.VisualBasic`名前空間と名前空間をインポートします。 コンパイラは、オプションが指定されて`-nostdlib`いない限り、システム .dll アセンブリを暗黙的に参照します。 オプション`-nostdlib`は、vbc.exe でコンパイルしないようにコンパイラに指示するか、または自動的に .dll アセンブリを参照します。  
  
> [!NOTE]
> Mscorlib.dll および Microsoft の .dll アセンブリは常に参照されます。  
  
 Vbc.exe ファイルを変更して、すべての vbc.exe コンパイルに含める必要のある追加のコンパイラオプションを指定できます ( `-noconfig`オプションを指定する場合を除く)。 詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。  
  
 コンパイラは、最後に`vbc`コマンドに渡されたオプションを処理します。 したがって、コマンドラインのオプションは、Vbc.exe ファイルの同じオプションの設定よりも優先されます。  
  
> [!NOTE]
> この`-noconfig`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
