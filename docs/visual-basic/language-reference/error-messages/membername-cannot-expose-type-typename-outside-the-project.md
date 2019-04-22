---
title: "'<membername>' は、型 '<typename>' を <containertype> '<containertypename>' 経由でプロジェクトの外側に公開できません。"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818344"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername >' の型を公開できません'\<typename >' 経由でプロジェクトの外部\<でフィルター処理します > '\<containertypename >'。
変数、プロシージャのパラメーター、または関数の戻り値が、そのコンテナーの外部に公開されているが、コンテナーの外に必ず公開しない型として宣言されています。  
  
 次のスケルトン コードは、このエラーが発生する状況を示しています。  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 宣言されている型`Protected`、 `Friend`、 `Protected Friend`、または`Private`その宣言コンテキストの外部アクセスを制限するためのものです。 データとして使用制限の少ない方のアクセス権を持つ変数の型はこの目的を倒すとします。 上記のスケルトン コード`exposedVar`は`Public`公開と`privateClass`にアクセス権のないコードにします。  
  
 **エラー ID:** BC30909  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   変数、プロシージャのパラメーター、または関数のアクセス レベルの変更は、少なくともそのデータ型のアクセス レベルと同程度に制限するように返します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
