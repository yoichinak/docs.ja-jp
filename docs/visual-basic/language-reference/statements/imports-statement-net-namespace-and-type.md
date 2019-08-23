---
title: Imports ステートメント-.NET 名前空間と型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912387"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports ステートメント (.NET 名前空間および型)
名前空間の修飾なしで型名を参照できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`aliasname`|任意。 完全修飾文字列では`namespace`なく、コードが参照できる*インポートエイリアス*または名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`namespace`|必須。 インポートされる名前空間の完全修飾名。 には、任意のレベルに入れ子になった名前空間の文字列を指定できます。|  
|`element`|任意。 名前空間で宣言されているプログラミング要素の名前。 任意のコンテナー要素を指定できます。|  
  
## <a name="remarks"></a>Remarks  
 ステートメント`Imports`を使用すると、特定の名前空間に含まれる型を直接参照できます。  
  
 1つの名前空間名または入れ子になった名前空間の文字列を指定できます。 入れ子になった各名前空間は、次の例に示すよう`.`に、ピリオド () で次の上位レベルの名前空間から分離されます。  
  
 `Imports System.Collections.Generic`  
  
 各ソースファイルには、任意の`Imports`数のステートメントを含めることができます。 これら`Option Strict` `Module`は、ステートメントなどの任意のオプション宣言に従う必要があり、または`Class`ステートメントなどのプログラミング要素の宣言の前に記述する必要があります。  
  
 は、ファイル`Imports`レベルでのみ使用できます。 つまり、インポートの宣言コンテキストはソースファイルである必要があり、名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックにすることはできません。  
  
 ステートメントでは`Imports` 、プロジェクトで他のプロジェクトおよびアセンブリの要素を使用できないことに注意してください。 インポートでは、参照の設定は行われません。 これにより、プロジェクトで既に使用可能な名前を修飾する必要がなくなります。 詳細については、「宣言された[要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「コンテナー要素のインポート」を参照してください。  
  
> [!NOTE]
> 暗黙`Imports`のステートメントを定義するには、[[参照] ページの [プロジェクトデザイナー] (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)を使用します。 詳細については、「[方法 :インポートされた名前空間を追加](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)または削除します (Visual Basic)。  
  
## <a name="import-aliases"></a>インポート エイリアス  
 *インポートエイリアス*は、名前空間または型のエイリアスを定義します。 インポートエイリアスは、1つまたは複数の名前空間で宣言されているものと同じ名前の項目を使用する必要がある場合に便利です。 詳細と例については、「宣言された[要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「要素名の修飾」を参照してください。  
  
 モジュールレベルでと`aliasname`同じ名前のメンバーを宣言することはできません。 この場合、Visual Basic コンパイラは、宣言`aliasname`されたメンバーに対してのみを使用し、それをインポートエイリアスとして認識しなくなります。  
  
 インポートエイリアスの宣言に使用される構文は、XML 名前空間プレフィックスのインポートに使用される構文と似ていますが、結果は異なります。 インポートエイリアスは、コード内で式として使用できます。一方、XML 名前空間プレフィックスは、xml リテラルまたは XML 軸プロパティで、修飾された要素名または属性名のプレフィックスとしてのみ使用できます。  
  
### <a name="element-names"></a>要素の名前  
 を指定`element`する場合は、*コンテナー要素*、つまり、他の要素を含むことができるプログラミング要素を表す必要があります。 コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙体が含まれます。  
  
 `Imports`ステートメントで使用できる要素のスコープは、を指定`element`したかどうかによって異なります。 のみ`namespace`を指定した場合、その名前空間の一意の名前を持つすべてのメンバーと、その名前空間内のコンテナー要素のメンバーは、修飾なしで使用できます。 `namespace` と`element`の両方を指定すると、その要素のメンバーだけが修飾なしで使用できます。  
  
## <a name="example"></a>例  
 次の例では、C:\ 内のすべてのフォルダーが返されます。クラスを使用し<xref:System.IO.DirectoryInfo>たディレクトリ。  
  
 このコードには`Imports` 、ファイルの先頭にステートメントがありません。 このため、 `DirectoryInfo`、 <xref:System.Text.StringBuilder>、および<xref:Microsoft.VisualBasic.ControlChars.CrLf>の各参照はすべて、名前空間で完全修飾されています。  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>例  
 次の例に`Imports`は、参照先の名前空間のステートメントが含まれています。 そのため、型は名前空間で完全修飾されている必要はありません。  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>例  
 次の例に`Imports`は、参照先の名前空間のエイリアスを作成するステートメントが含まれています。 型はエイリアスで修飾されます。  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>例  
 次の例に`Imports`は、参照される型のエイリアスを作成するステートメントが含まれています。 エイリアスは、型を指定するために使用されます。  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>関連項目

- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic 内の名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
