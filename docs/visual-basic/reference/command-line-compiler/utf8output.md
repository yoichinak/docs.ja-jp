---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 789df84bb4011d1ad128c50a9c689d1217be6694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937271"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
UTF-8 エンコードを使用してコンパイラ出力を表示します。  
  
## <a name="syntax"></a>構文  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 このオプションの既定値は`-utf8output-`です。これは、コンパイラの出力で utf-8 エンコーディングが使用されないことを意味します。 `-utf8output` を指定することは、`-utf8output+` を指定することと同じです。  
  
## <a name="remarks"></a>Remarks  
 国際対応の構成によっては、コンパイラの出力をコンソールに正しく表示できない場合があります。 このような場合は`-utf8output` 、を使用して、コンパイラの出力をファイルにリダイレクトします。  
  
> [!NOTE]
> この`-utf8output`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードで`In.vb`は、utf-8 エンコーディングを使用して出力を表示するようにコンパイラをコンパイルし、指示します。  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
