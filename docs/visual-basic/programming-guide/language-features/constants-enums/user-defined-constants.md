---
title: ユーザー定義定数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813913"
---
# <a name="user-defined-constants-visual-basic"></a>ユーザー定義定数 (Visual Basic)
定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。 定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。 コントロールまたは使用するコンポーネントで定義されている定数を使用することができますか、独自に作成することができます。 自分で作成した定数は*ユーザー定義*します。  
  
 定数を宣言する、`Const`ステートメントでは、変数名を作成するための場合と同じガイドラインを使用します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
## <a name="const-statement-usage"></a>Const ステートメントの使用状況  
 A`Const`ステートメント、数学的表現したり、数量の日付/時刻。  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 これも定義できます`String`定数。  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 等号の右側にある式 ( `=` )、数値またはリテラル文字列は、多くの場合は、(ただし、その式には、関数への呼び出しを含めることはできません)、数値または文字列に評価される式を指定することもできます。 以前に定義された定数の観点から定数を定義することもできます。  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>ユーザー定義関数のスコープ  
 A`Const`ステートメントのスコープは、同じ場所で宣言された変数の場合と同じです。 スコープは、次の方法のいずれかで指定できます。  
  
-   プロシージャ内でのみ存在する定数を作成するには、そのプロシージャ内で宣言します。  
  
-   使用できるは、そのモジュール外のコードではなく、クラス内のすべてのプロシージャに定数を作成するには、クラスの宣言セクションに宣言します。  
  
-   アセンブリの外部のクライアントではなく、アセンブリでは、すべてのメンバーに使用できる定数を作成するには、宣言を使用して、`Friend`クラスの宣言セクション内のキーワード。  
  
-   アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`セクション クラスの宣言でキーワード。  
  
 詳細については、「[方法 :定数を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)します。  
  
### <a name="avoiding-circular-references"></a>循環参照の回避  
 他の定数では、定数を定義することができます、ために、誤ってを作成することは、*サイクル*、または 2 つ以上の定数との間の循環参照。 サイクルは、2 つ以上パブリック定数がある場合、次の例のように、他の観点から各が定義されているときに発生します。  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 循環参照が発生した場合、Visual Basic には、コンパイラ エラーが生成されます。  
  
## <a name="see-also"></a>関連項目

- [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [定数と列挙体](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [方法: 列挙体を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
