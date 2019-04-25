---
title: 定数の概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2939110de77718baf32e2a0d8f1aa52dba997cf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841298"
---
# <a name="constants-overview-visual-basic"></a>定数の概要 (Visual Basic)
定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。 定数は、名前が示すようは、アプリケーションの実行全体で同じ値を格納します。 大幅に、コードの読みやすさを向上し、定数を使用して管理しやすくできます。 再び表示される値を含むコードで使用するが困難に注意してくださいまたは明確な意味のない特定の番号に依存します。  
  
## <a name="how-to-create-and-use-constants"></a>作成、および定数を使用する方法  
 Visual Basic には、さまざまな定義済み定数は、主に印刷と表示の使用が含まれています。 独自の定数を作成することもできます、`Const`ステートメントでは、変数名を作成するための場合と同じガイドラインを使用します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
 定数のスコープは、その名前を修飾せずに参照できるすべてのコードのセットは、同じ場所で宣言された変数の場合と同じです。 特定のプロシージャのスコープ内に存在する定数を作成するには、そのプロシージャ内で宣言します。 アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`クラスの宣言セクション内のキーワード。  
  
> [!NOTE]
>  定数には、変数と似ていますは、それらを変更または変数には、それらを新しい値を割り当てることはできません。  
  
 コントロールまたはコンポーネントを使用すると、動作するためのオブジェクト モデルでは、コードで使用する定数を定義できますまたはユーザー定義されている可能性がある (つまり、自分で作成した)。  
  
## <a name="compile-time-and-run-time-constants"></a>コンパイル時と実行時の定数  
 コンパイル時定数は、実行時の定数は、アプリケーションの実行中にのみ計算するときに、コードのコンパイル時に計算されます。 コンパイル時定数では、毎回アプリケーションを実行中に、実行時の定数は毎回変えることがあります、同じ値があります。 コンパイル時定数では、配列の範囲、case 式は、列挙子の初期化子などの場合必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|定義|用語|  
|---|---|  
|[方法: 定数を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|使用する方法について説明します、`Const`定数を宣言し、その値を設定するステートメントの定数を宣言する値にわかりやすい名前を割り当てます。|  
|[ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|循環参照を回避する方法とスコープに関する情報など、独自の定数を作成する方法について説明します。|  
|[定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Visual Basic コンパイラが定数を初期化する方法についての情報と`Option Explicit`は無効になります。|  
|[方法: 関連する定数値をまとめてグループ](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|関連する定数値をグループ化する方法を示します。|  
  
## <a name="reference"></a>参照  
  
|定義|用語|  
|---|---|  
|[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic での定義済み定数を示します。|  
|[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)|について説明します、`Const`ステートメントとその使用します。|  
|[Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|について説明します、`Option Strict`ステートメントとその使用します。|  
  
## <a name="see-also"></a>関連項目

- [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [方法: Visual Basic で配列変数を初期化します。](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
