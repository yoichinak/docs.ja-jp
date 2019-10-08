---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 15f334f280c2aca83ba5b628a1137464c31c6282
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005556"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
指定された Visual Basic 言語バージョンに含まれている構文のみをコンパイラが受け入れるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>引数  
 `version`  
 必須。 コンパイル中に使用される言語バージョン。 許容される値は @no__t 0、`10`、`11`、`12`、`14`、`15`、`15.3`、`15.5`、`default`、`latest` です。

 すべての整数は、マイナーバージョンとして `.0` を使用して指定することもできます (例: `11.0`)。

 使用可能なすべての値の一覧を表示するには、コマンドラインで `-langversion:?` を指定します。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 オプションは、コンパイラが受け入れる構文を指定します。 たとえば、言語バージョンが9.0 であることを指定した場合、コンパイラはバージョン10.0 以降でのみ有効な構文に対してエラーを生成します。  
  
 このオプションは、異なるバージョンの .NET Framework を対象とするアプリケーションを開発する場合に使用できます。 たとえば、.NET Framework 3.5 を対象としている場合は、このオプションを使用して、言語バージョン10.0 の構文を使用しないようにすることができます。  
  
 @No__t-0 は、コマンドラインを使用して直接設定できます。 詳細については、「[対象となる特定の .NET Framework のバージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは、Visual Basic 9.0 に対して `sample.vb` をコンパイルします。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [対象となる特定の .NET Framework バージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
