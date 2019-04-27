---
title: 宣言された要素の特性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 98f6a7738a462e9f36abdc0380cb1fe8d488fb9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61830168"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣言された要素の特性 (Visual Basic)
A*特性*とそのコードをやり取りする方法に影響を与える要素の特定の側面は、宣言された要素の。 宣言された各要素は、関連付けられている次の特性の 1 つ以上があります。  
  
-   *データ型*: 要素が保持できる値、およびそれらの値を格納する方法。 詳細については、「[Data Types](../../../../visual-basic/language-reference/data-types/index.md)」(データ型) を参照してください。  
  
-   *有効期間*-は、要素を使用できる実行時間の期間。 詳細については、次を参照してください。 [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)します。  
  
-   *スコープ*-その名前を修飾しなくても、要素を参照できるすべてのコードのセット。 詳細については、「[方法 :変数のスコープを制御](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)します。  
  
-   *アクセス レベル*-コードに対するアクセス許可の要素を使用します。 詳細については、「[方法 :変数の可用性を制御](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)します。  
  
## <a name="characteristics-of-the-elements"></a>要素の特性  
 次の表は、宣言された要素とそれぞれに適用される特性を示します。  
  
|要素|データの種類|有効期間|スコープ<sup>1</sup>|アクセス レベル|  
|-------------|---------------|--------------|------------------------|------------------|  
|変数|[はい]|はい|はい|[はい]|  
|定数|[はい]|×|[はい]|[はい]|  
|列挙|[はい]|×|[はい]|[はい]|  
|構造体|いいえ|×|[はい]|[はい]|  
|プロパティ|[はい]|はい|はい|[はい]|  
|メソッド|いいえ|[はい]|はい|[はい]|  
|プロシージャ (`Sub`または`Function`)|いいえ|[はい]|はい|[はい]|  
|プロシージャ パラメーター|[はい]|はい|[はい]|いいえ|  
|関数の戻り値|[はい]|はい|[はい]|いいえ|  
|演算子|[はい]|×|[はい]|[はい]|  
|Interface|いいえ|×|[はい]|[はい]|  
|クラス|いいえ|×|[はい]|[はい]|  
|event|いいえ|×|[はい]|[はい]|  
|Delegate|いいえ|×|[はい]|[はい]|  
  
 <sup>1</sup>スコープとして呼ば*可視性*します。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
