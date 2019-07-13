---
title: DLL 読み込み時のエラーです。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 5a26443a49b0b853f2f2188fb58d7ed907d671b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659615"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL 読み込み時のエラーです。(Visual Basic)
ダイナミック リンク ライブラリ (DLL) がで指定されているライブラリ、`Lib`の句、`Declare`ステートメント。 このエラーの考えられる原因は次のとおりです。  
  
- ファイルは、DLL の実行可能ファイルではありません。  
  
- ファイルは、Microsoft Windows の DLL ではありません。  
  
- DLL が存在しない別の DLL を参照します。  
  
- DLL または参照される DLL がパスに指定されたディレクトリではありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- ソース テキスト ファイルとそのための DLL が実行可能ファイルがある場合に、コンパイルして DLL の実行可能ファイル形式にリンクする必要があります。  
  
- ファイルが Microsoft Windows DLL でない場合は、同等の Microsoft Windows を入手します。  
  
- DLL が存在しない別の DLL を参照する場合は、参照される DLL を入手して使用できるようにします。  
  
- DLL または参照される DLL がパスで指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
