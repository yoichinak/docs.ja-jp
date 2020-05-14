---
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 7a16e951030731bdcbb48b5fbb1a0d1881d5e1ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619389"
---
# <a name="bad-file-name-or-number"></a>ファイル名または番号が正しくありません。
指定したファイルにアクセスしようとして、エラーが発生しました。 このエラーでは以下の原因が考えられます。  
  
- ステートメントで、`FileOpen` ステートメントに指定されていないファイル名または番号を使用してファイルを参照しているか、または `FileOpen` ステートメントにそれが指定されていても、その後閉じられました。  
  
- ステートメントで、ファイル番号の範囲外の番号を使用してファイルを参照しています。  
  
- ステートメントで、無効なファイル名または番号を参照しています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `FileOpen` ステートメントでファイル名が指定されていることを確認します。 引数を指定せずに `FileClose` ステートメントを呼び出した場合、開いているすべてのファイルが誤って閉じられた可能性があることに注意してください。  
  
2. コードでアルゴリズムによってファイル番号を生成している場合、番号が有効であることを確認します。  
  
3. ファイル名をチェックして、それらがオペレーティング システムの規則に従っていることを確認してください。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
