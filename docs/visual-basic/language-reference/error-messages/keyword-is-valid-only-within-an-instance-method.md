---
title: "'<keyword>' は、インスタンス メソッド内でのみ有効です。"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 5ff82b932f9bea4c7fd087651e34277ef94bc27c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820719"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>'\<keyword>' は、インスタンス メソッド内でのみ有効です。
`Me`、 `MyClass`、および`MyBase`キーワードは、特定のクラスのインスタンスを参照してください。 共有内で使用することはできません`Function`または`Sub`プロシージャ。  
  
 **エラー ID:** BC30043  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   プロシージャからキーワードを削除または削除、`Shared`プロシージャ宣言からキーワード。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数の代入](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
