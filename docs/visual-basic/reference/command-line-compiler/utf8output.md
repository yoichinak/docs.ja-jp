---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004661"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 エンコードを使用してコンパイラ出力を表示します。  
  
## <a name="syntax"></a>構文  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 このオプションの既定値は `-utf8output-` です。これは、コンパイラの出力で UTF-8 エンコードが使用されないことを意味します。 `-utf8output` を指定することは、`-utf8output+` を指定することと同じです。  
  
## <a name="remarks"></a>コメント  
 国際対応の構成によっては、コンパイラの出力をコンソールに正しく表示できない場合があります。 このような場合は、@no__t 0 を使用して、コンパイラの出力をファイルにリダイレクトします。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは `In.vb` をコンパイルし、UTF-8 エンコーディングを使用して出力を表示するようにコンパイラに指示します。  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
