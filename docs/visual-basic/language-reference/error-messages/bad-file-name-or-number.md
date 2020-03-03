---
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 7a16e951030731bdcbb48b5fbb1a0d1881d5e1ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619389"
---
# <a name="bad-file-name-or-number"></a>ファイル名または番号が正しくありません。
指定したファイルにアクセスしているときにエラーが発生しました。 このエラーの考えられる原因には。  
  
- ステートメントで指定されていないファイルの名前または番号のファイルを参照して、`FileOpen`で指定されたステートメントまたはを`FileOpen`ステートメントは、その後が終了します。  
  
- ステートメントは、ファイル番号の範囲外にある数値を持つファイルを参照します。  
  
- ステートメントを指すファイルの名前または番号が無効です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. ファイル名がで指定されたことを確認、`FileOpen`ステートメント。 呼び出した場合、`FileClose`ステートメント引数を指定せず可能性がありますが誤って閉じたすべての開いているファイル。  
  
2. 場合は、コードの生成は、ファイルの番号にアルゴリズムが、番号は有効なことを確認します。  
  
3. オペレーティング システムの規約に準拠しているかどうかを確認するファイル名を確認します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
