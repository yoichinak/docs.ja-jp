---
title: "'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339074"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)
行のステートメントがサポートされていません。 ファイル I/O 機能は`Microsoft.VisualBasic.FileSystem.LineInput`グラフィックス機能は、`System.Drawing.Graphics.DrawLine`します。  
  
 **エラー ID:** BC30830  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. ファイル アクセスを実行する場合は、使用`Microsoft.VisualBasic.FileSystem.LineInput`します。  
  
2. グラフィックス処理を行っている場合は、 `System.Drawing.Graphics.Drawline`を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic におけるファイル アクセス](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
