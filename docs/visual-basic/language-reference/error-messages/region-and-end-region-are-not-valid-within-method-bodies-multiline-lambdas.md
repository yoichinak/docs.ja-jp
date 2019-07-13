---
title: "'#Region' および ' #End Region' ステートメントはメソッド本体や複数行ラムダ内では有効ではありません。"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013765"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません。
`#Region`ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。 折りたたみ可能な領域は、1 つ以上のプロシージャを含めることができますが、開始またはプロシージャの内部で終了することはできません。  
  
 **エラー ID:** BC32025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 直前のプロシージャが、`End Function`ステートメントまたは`End Sub`ステートメントによって正しく終了していることを確認します。  
  
2. `#Region`ディレクティブおよび`#End Region`ディレクティブが同じコード ブロック内にあることを確認します。  
  
## <a name="see-also"></a>関連項目

- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
