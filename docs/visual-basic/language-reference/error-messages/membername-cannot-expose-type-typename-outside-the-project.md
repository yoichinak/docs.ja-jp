---
title: "'<membername>' は、型 '<typename>' を <containertype> '<containertypename>' 経由でプロジェクトの外側に公開できません。"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700897"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername>' は、型 '\<typename>' を \<containertype> '\<containertypename>' 経由でプロジェクトの外側に公開できません
変数、プロシージャ パラメーター、または関数の戻り値がそのコンテナーの外側に公開されていますが、コンテナーの外側に公開できない型として宣言されています。  
  
 次のスケルトン コードは、このエラーが生成される状況を示しています。  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 `Protected`、`Friend`、`Protected Friend`、または `Private` として宣言されている型は、その宣言コンテキストの外部でアクセスが制限されることを目的としています。 アクセス制限が緩い変数のデータ型として使用すると、この目的が損なわれます。 上記のスケルトン コードでは、`exposedVar` は `Public` であり、アクセス権を持たないコードに `privateClass` を公開します。  
  
 **エラー ID:** BC30909  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 変数、プロシージャ パラメーター、または関数の戻り値のアクセス レベルを、少なくともそのデータ型のアクセス レベルと同じ制限になるように変更します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
