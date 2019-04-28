---
title: Namespace ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 7f6b976af7933b3895f6992488d2d1532a8fc2f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784138"
---
# <a name="namespace-statement"></a>Namespace ステートメント
名前空間の名前を宣言し、ソース コードがその名前空間内でコンパイルするように宣言します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>指定項目  
 Global  
 省略可能です。 プロジェクトのルート名前空間から名前空間を定義することができます。 参照してください[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)します。  
  
 `name`  
 必須。 名前空間を識別する一意の名前。 有効な Visual Basic 識別子である必要があります。 詳細については、次を参照してください。 [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
  
 `componenttypes`  
 任意。 名前空間を構成する要素。 これらは、含めるが、列挙体、構造体、インターフェイス、クラス、モジュール、デリゲート、および他の名前空間に限定されません。  
  
 `End Namespace`  
 終了、`Namespace`ブロックします。  
  
## <a name="remarks"></a>Remarks  
 名前空間は、組織のシステムとして使用されます。 分類およびその他のプログラム、およびアプリケーションに公開されているプログラミング要素を表現する手段となります。 名前空間がないので注意、*型*クラスまたは構造体は、という意味で、名前空間のデータ型を持つプログラミング要素を宣言することはできません。  
  
 後で宣言されたすべてのプログラミング要素、`Namespace`ステートメントは、その名前空間に属しています。 Visual Basic がいずれかを検出するまで、最後の宣言された名前空間に要素をコンパイルするには引き続き、`End Namespace`ステートメントまたは別`Namespace`ステートメント。  
  
 名前空間は既に定義されている場合、プロジェクト以外でもをプログラミング要素を追加できます。 これを行うには、使用する、`Namespace`その名前空間に要素をコンパイルする Visual Basic を指示するステートメント。  
  
 使用することができます、`Namespace`ファイルまたは名前空間レベルでのみステートメント。 つまり、*宣言コンテキスト*名前空間は、ソース ファイルまたは別の名前空間にある必要があり、クラス、構造体、モジュール、インターフェイス、またはプロシージャにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 別の 1 つの名前空間を宣言することができます。 を宣言できますが、他のコードは、最も内側の名前空間で宣言された要素にアクセスするときに、入れ子の階層内のすべての名前空間名を含む修飾文字列を使用する必要があることに注意してください。 入れ子のレベルに厳密な制限はありません。  
  
## <a name="access-level"></a>アクセス レベル  
 名前空間として扱われますがある、`Public`アクセス レベル。 名前空間は、同じプロジェクト内、プロジェクトを参照する他のプロジェクトおよびプロジェクトからビルドされたアセンブリにアクセスできます。  
  
 つまり、名前空間内の他の任意の要素内部ではなく、名前空間レベルで宣言されたプログラミング要素が`Public`または`Friend`アクセスします。 このようなアクセス レベルの要素を使用して指定しない場合、`Friend`既定。 要素名前空間レベルで宣言するにはには、クラス、構造体、モジュール、インターフェイス、列挙型、およびデリゲートが含まれます。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
## <a name="root-namespace"></a>ルート Namespace  
 プロジェクト内のすべての名前空間名がに基づいて、*ルート名前空間*します。 Visual Studio では、プロジェクト内のすべてのコードで、既定のルート名前空間としてプロジェクト名が割り当てられます。 たとえば、プロジェクト名が `Payroll`である場合、そのプログラミング要素は `Payroll`名前空間に属します。 宣言する場合`Namespace funding`、その名前空間の完全名は`Payroll.funding`します。  
  
 既存の名前空間を指定する場合、`Namespace`ステートメントなど、ジェネリック リスト クラスの例では、null 値に、ルート名前空間を設定できます。 これを行うには、次のようにクリックします。**プロジェクト プロパティ**から、**プロジェクト**メニューと、消去、**ルート名前空間**エントリ、ボックスは空にします。 ジェネリック リスト クラスの例ではこれを実行している場合、Visual Basic コンパイラが行う`System.Collections.Generic`プロジェクト内の新しい名前空間として`Payroll`の完全な名前を持つ`Payroll.System.Collections.Generic`します。  
  
 また、使用することができます、`Global`キーワードをプロジェクトの外部で定義された名前空間の要素を参照してください。 そうには、ルート名前空間としてプロジェクト名を保持することができます。 これにより、意図せずと共に既存の名前空間のプログラミング要素にマージされる可能性が減少します。 詳細については、「グローバル キーワードで完全修飾名」のセクションを参照してください。 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)します。  
  
 `Global` Namespace ステートメントでキーワードを使用することもできます。 これにより、プロジェクトのルート名前空間から名前空間を定義できます。 詳細については、「グローバル キーワードに Namespace ステートメント」セクションを参照してください。 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)します。  
  
 **トラブルシューティングします。** ルート名前空間には、名前空間名の連結されたもので予期しないことがあります。 プロジェクトの外部で定義されている名前空間への参照を作成する場合、Visual Basic コンパイラとして解釈ルート名前空間内の入れ子になった名前空間。 このような場合は、コンパイラは、外部の名前空間で既に定義されているすべての型を認識しません。 これを回避するには、設定、ルート名前空間"Root Namespace"で説明されていると null 値にするかを使用して、`Global`外部名前空間の要素にアクセスするキーワード。  
  
## <a name="attributes-and-modifiers"></a>属性と修飾子  
 名前空間には、属性を適用することはできません。 属性は、名前空間などのソースの分類器の意味はないアセンブリのメタデータに情報を提供します。  
  
 名前空間には、すべてのアクセスまたはプロシージャ修飾子、またはその他の修飾子を適用できません。 型ではないためこれらの修飾子は意味がありません。  
  
## <a name="example"></a>例  
 次の例では、もう一方の入れ子になった 2 つの名前空間を宣言します。  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>例  
 次の例は、1 つの行に複数の入れ子になった名前空間を宣言し、これは、前の例に相当します。  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>例  
 次の例では、前の例で定義されたクラスにアクセスします。  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>例  
 次の例は、新しいジェネリック リスト クラスのスケルトンを定義しに追加します、<xref:System.Collections.Generic?displayProperty=nameWithType>名前空間。  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>関連項目

- [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
