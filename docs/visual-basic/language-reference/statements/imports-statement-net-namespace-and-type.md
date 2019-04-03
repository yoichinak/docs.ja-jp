---
title: Imports ステートメント - .NET Namespace よぶ型 (Visual Basic)
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
ms.openlocfilehash: 4574bab62ca6d095ab66c17bf186da5f3d79bfb7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826523"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports ステートメント (.NET 名前空間および型)
有効では、名前空間の修飾せずに参照する名前を入力します。  
  
## <a name="syntax"></a>構文  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`aliasname`|省略可能です。 *インポート エイリアス*または名前が使用されるコードを参照できます`namespace`完全に修飾文字列の代わりにします。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`namespace`|必須。 インポートされる名前空間の完全修飾名。 名前空間の文字列はネストできますを任意のレベル。|  
|`element`|省略可能です。 名前空間で宣言されたプログラミング要素の名前。 任意のコンテナー要素を指定できます。|  
  
## <a name="remarks"></a>Remarks  
 `Imports`ステートメントを直接参照できる特定の名前空間に含まれる型を有効にします。  
  
 単一の名前空間名または入れ子になった名前空間の文字列を指定することができます。 入れ子になった各名前空間は、ピリオドで次のより高いレベルの名前空間から分離 (`.`)、次の例に示すようにします。  
  
 `Imports System.Collections.Generic`  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメント。 オプションの任意の宣言をなどこれらに従う必要があります、`Option Strict`ステートメント、および、必要がありますの前に任意のプログラミング要素宣言など`Module`または`Class`ステートメント。  
  
 使用することができます`Imports`ファイル レベルでのみです。 つまり、宣言のコンテキストのインポートでは、ソース ファイルである必要があります、名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。  
  
 なお、`Imports`ステートメントは行いません他のプロジェクトおよびアセンブリからの要素をプロジェクトに使用できます。 インポートしても、参照設定の代わりにはなりません。 既にプロジェクトに使用できる名前を修飾する必要性を削除するだけです。 詳細については、「を格納している要素のインポート」を参照してください[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
> [!NOTE]
>  暗黙の型を定義する`Imports`ステートメントを使用して、[参照設定 ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。 詳細については、「[方法 :追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)します。  
  
## <a name="import-aliases"></a>インポート エイリアス  
 *インポート エイリアス*名前空間または型のエイリアスを定義します。 インポート エイリアスは、1 つまたは複数の名前空間で宣言されているのと同じ名前の項目を使用する必要がある場合に便利です。 詳細と例では、「an 要素名を修飾する」を参照してください[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)します。  
  
 同じ名前では、モジュール レベルのメンバーを宣言する必要があります`aliasname`します。 Visual Basic コンパイラを使用する場合は、`aliasname`されなくし、宣言されたメンバーに対してのみインポート エイリアスとして認識します。  
  
 XML 名前空間プレフィックスをインポートするのには、インポート エイリアスの宣言に使用される構文は使用がそのような結果は異なります。 インポート エイリアスは、XML 名前空間プレフィックスとして使用できます XML リテラルまたは XML 軸のプロパティでのみ、プレフィックス修飾要素または属性名は、コードで、式として使用できます。  
  
### <a name="element-names"></a>要素の名前  
 指定する場合`element`、表す必要がありますが、*コンテナー要素*、他の要素を含むことのできるプログラミング要素は、します。 コンテナー要素には、クラス、構造体、モジュール、インターフェイス、および列挙が含まれます。  
  
 によって提供される要素のスコープ、`Imports`ステートメントが指定するかどうかに依存`element`します。 のみを指定する場合`namespace`、すべて一意に、その名前空間のメンバーとその名前空間内のコンテナー要素のメンバーの名前、修飾なしで利用されます。 両方を指定する場合`namespace`と`element`、のみその要素のメンバーを修飾なしで利用できます。  
  
## <a name="example"></a>例  
 次の例では、C:\ ディレクトリ内のすべてのフォルダーを返しますを使用して、<xref:System.IO.DirectoryInfo>クラス。  
  
 コードを持たない`Imports`ファイルの上部にあるステートメント。 そのため、 `DirectoryInfo`、 <xref:System.Text.StringBuilder>、および<xref:Microsoft.VisualBasic.ControlChars.CrLf>の参照がすべて完全修飾名前空間にします。  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照の名前空間のステートメント。 そのため、型は、完全修飾名前空間にするのにはありません。  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照の名前空間のエイリアスを作成するステートメント。 種類は、エイリアスで修飾されます。  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>例  
 次の例が含まれます`Imports`参照先の型のエイリアスを作成するステートメント。 エイリアスを使用して、種類を指定します。  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>関連項目

- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [宣言された要素の参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
