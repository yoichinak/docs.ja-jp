---
title: "'#Region' および ' #End Region' ステートメントはメソッド本体や複数行ラムダ内では有効ではありません。"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: deef3de645040d7c3d95b1a6c8a25fcf10de881b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842708"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません。
`#Region`ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。 折りたたみ可能な領域は、1 つ以上のプロシージャを含めることができますが、開始またはプロシージャの内部で終了することはできません。  
  
 **エラー ID:** BC32025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  直前のプロシージャが、`End Function`ステートメントまたは`End Sub`ステートメントによって正しく終了していることを確認します。  
  
2.  `#Region`ディレクティブおよび`#End Region`ディレクティブが同じコード ブロック内にあることを確認します。  
  
## <a name="see-also"></a>関連項目

- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
