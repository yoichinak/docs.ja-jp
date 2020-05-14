---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005436"
---
# <a name="-noconfig"></a>-noconfig
コンパイラにより、一般的に使用される .NET Framework アセンブリが自動的に参照されたり、`System` と `Microsoft.VisualBasic` 名前空間がインポートされたりしないように指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Remarks  
 `-noconfig` オプションでは、Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを使用してコンパイルが実行されないように、コンパイラに指定できます。 Vbc.rsp ファイルは、一般的に使用される .NET Framework アセンブリを参照し、`System` と `Microsoft.VisualBasic` の名前空間をインポートします。 コンパイラでは、`-nostdlib` オプションを指定しない限り、System.dll アセンブリが暗黙的に参照されます。 `-nostdlib` オプションでは、Vbc.rsp を使用してコンパイルされないように、または自動的に System.dll アセンブリが参照されないように、コンパイラに指定できます。  
  
> [!NOTE]
> Mscorlib.dll アセンブリおよび Microsoft.VisualBasic.dll アセンブリは常に参照されます。  
  
 Vbc.rsp ファイルを変更すると、(`-noconfig` オプションを指定した場合を除き) Vbc.exe のすべてのコンパイルに含めるコンパイラ オプションを追加指定できます。 詳しくは、「[@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)」をご覧ください。  
  
 コンパイラでは、`vbc` コマンドに渡されるオプションが最後に処理されます。 そのため、コマンド ラインでオプションが指定されている場合、Vbc.rsp ファイル内の同じオプション設定がオーバーライドされます。  
  
> [!NOTE]
> `-noconfig` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (応答ファイルの指定)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
