---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937256"
---
# <a name="-verbose"></a>-verbose
コンパイラによって、詳細なステータスとエラーメッセージが生成されます。  
  
## <a name="syntax"></a>構文  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 を指定すること`-verbose+`は、を指定することと同じです。これにより、コンパイラは詳細なメッセージを出力します。`-verbose` このオプションの既定値は`-verbose-`です。  
  
## <a name="remarks"></a>Remarks  
 この`-verbose`オプションは、コンパイラによって発行されたエラーの合計数に関する情報を表示し、どのアセンブリがモジュールによって読み込まれているかを報告し、現在コンパイルされているファイルを表示します。  
  
> [!NOTE]
> この`-verbose`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは`In.vb` 、コンパイルを行い、詳細な状態情報を表示するようにコンパイラを指示します。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
