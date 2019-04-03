---
title: "'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 7616bcdc39ab479049586534fac22f1e2d96a700
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831840"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)
行のステートメントがサポートされていません。 ファイル I/O 機能は`Microsoft.VisualBasic.FileSystem.LineInput`グラフィックス機能は、`System.Drawing.Graphics.DrawLine`します。  
  
 **エラー ID:** BC30830  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ファイル アクセスを実行する場合は、使用`Microsoft.VisualBasic.FileSystem.LineInput`します。  
  
2.  グラフィックス処理を行っている場合は、 `System.Drawing.Graphics.Drawline`を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic におけるファイル アクセス](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
