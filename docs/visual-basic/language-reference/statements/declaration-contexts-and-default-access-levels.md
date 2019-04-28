---
title: 宣言コンテキストと既定のアクセス レベル (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 0d899342383bdf9d262fc9a1ab5e00bbe43066e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638188"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣言コンテキストと既定のアクセス レベル (Visual Basic)
このトピックでは、他の種類内でどの Visual Basic の型を宣言することができ、どのようなアクセス レベルを既定の指定されていない場合について説明します。  
  
## <a name="declaration-context-levels"></a>宣言コンテキスト レベル  
 *宣言コンテキスト*のプログラミング要素が宣言されているコードの領域。 これが呼び出される、別のプログラミング要素は、多くの場合、*要素を含む*します。  
  
 宣言コンテキストのレベルは、次のとおりです。  
  
- *Namespace レベル*: ソース ファイルまたは名前空間内にあるが、クラス、構造体、モジュール、またはインターフェイス  
  
- *モジュール レベル*-クラス、構造体、モジュール、またはインターフェイス内にあるが、プロシージャまたはブロック  
  
- *プロシージャ レベル*— プロシージャまたはブロック内 (など`If`または`For`)  
  
 次の表では、その宣言コンテキストに応じて、さまざまな宣言されたプログラミングの要素の既定のアクセス レベルを示します。  
  
|宣言された要素|Namespace レベル|モジュール レベル|プロシージャ レベル|  
|----------------------|---------------------|------------------|---------------------|  
|変数 ([Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md))|使用できません|`Private` (`Public`で`Structure`で許可されていない、 `Interface`)|`Public`|  
|定数 ([Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md))|使用できません|`Private` (`Public`で`Structure`で許可されていない、 `Interface`)|`Public`|  
|列挙 ([Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|使用できません|  
|クラス ([Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|使用できません|  
|構造体 ([ステートメントの構造体](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|使用できません|  
|モジュール ([モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|使用できません|使用できません|  
|インターフェイス ([Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|使用できません|  
|プロシージャ ([Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)、 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md))|使用できません|`Public`|使用できません|  
|外部参照 ([Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md))|使用できません|`Public` (では許可されません`Interface`)|使用できません|  
|演算子 ([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md))|使用できません|`Public` (では許可されません`Interface`または`Module`)|使用できません|  
|プロパティ ([Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md))|使用できません|`Public`|使用できません|  
|既定のプロパティ ([既定](../../../visual-basic/language-reference/modifiers/default.md))|使用できません|`Public` (では許可されません`Module`)|使用できません|  
|イベント ([Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md))|使用できません|`Public`|使用できません|  
|デリゲート ([Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|使用できません|  
  
 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
