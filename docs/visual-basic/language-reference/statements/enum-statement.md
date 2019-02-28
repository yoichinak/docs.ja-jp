---
title: Enum ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 662dc63b69a8229693471909a50b0c4f336b5637
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965697"
---
# <a name="enum-statement-visual-basic"></a>Enum ステートメント (Visual Basic)
列挙体を宣言し、そのメンバーの値を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     任意。 この列挙体に適用される属性の一覧です。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`")。  
  
     <xref:System.FlagsAttribute>属性は、列挙体のインスタンスの値が、複数の列挙型メンバーを含めることができ、各メンバーが列挙値のビット フィールドを表すことを示します。  
  
-   `accessmodifier`  
  
     任意。 この列挙体にアクセスできるコードを指定します。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     任意。 この列挙体を宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされた要素のセットを非表示にすることを指定します。 指定できる[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)列挙型自体でのみ、そのメンバーのいずれかではなく。  
  
-   `enumerationname`  
  
     必須。 列挙体の名前。 有効な名前については、次を参照してください。 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
-   `datatype`  
  
     任意。 列挙体とそのすべてのメンバーのデータ型。  
  
-   `memberlist`  
  
     必須。 このステートメントで宣言されているメンバー定数のリスト。 複数のメンバーは、個々 のソース コード行に表示されます。  
  
     各`member`が次の構文と部分。 `[<attribute list>] member name [ = initializer ]`  
  
    |パーツ|説明|  
    |---|---|  
    |`membername`|必須。 このメンバーの名前。|  
    |`initializer`|任意。 式がコンパイル時に評価され、このメンバーに割り当てられているです。|  
  
-   `End` `Enum`  
  
     
  `Enum` ブロックを終了します。  
  
## <a name="remarks"></a>Remarks  
 互いに論理的に関連する不変の値のセットがあれば、列挙体で一緒に定義できます。 これは、列挙型とそのメンバーでは、その値よりも覚えやすく、わかりやすい名前を提供します。 コードでさまざまな場所で列挙型メンバーを使用することができます。  
  
 列挙体を使用する利点を以下に示します。  
  
-   置き換えや数値の入力ミスによって発生したエラーを軽減します。  
  
-   簡単に、将来の値を変更します。  
  
-   により、コードを読みやすくするので、エラーが導入される可能性が低くなります。  
  
-   前方の互換性を確保します。 列挙体を使用する場合、コードはメンバー名に対応する値が、今後だれかが変更された場合に失敗する可能性を低減します。  
  
 名前、基のデータ型およびメンバーのセットを列挙しています 各メンバーは、定数を表します。  
  
 クラス、構造体、モジュール、またはインターフェイス レベルでは、プロシージャの外で宣言された列挙型は、*メンバー列挙*します。 クラス、構造体、モジュール、または列挙体を宣言するインターフェイスのメンバーになります。  
  
 列挙体のメンバーは、クラス、構造体、モジュール、またはインターフェイス内の任意の場所からアクセスできます。 コード、クラスの外部で構造体、またはモジュール修飾する必要があります、クラス、構造体、モジュールの名前を持つメンバーの列挙型の名前。 追加することによって完全修飾名を使用する必要を避けることができます、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントをソース ファイルにします。  
  
 任意のクラス、構造体、モジュール、またはインターフェイスの外部の名前空間レベルで宣言された列挙体が表示される名前空間のメンバーであります。  
  
 *宣言コンテキスト*列挙型のソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 属性を適用できますのメンバーではなく、全体としての列挙体に個別にします。 属性は、アセンブリのメタデータに情報を提供します。  
  
## <a name="data-type"></a>データの種類  
 `Enum`ステートメントが列挙体のデータ型を宣言できます。 各メンバーは、列挙型のデータ型を受け取る。 指定できる`Byte`、 `Integer`、 `Long`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`します。  
  
 指定しない場合`datatype`、列挙体の各メンバーがのデータ型を受け取るその`initializer`します。 両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`します。 どちらの場合`datatype`も`initializer`が存在するデータ型の既定値は`Integer`します。  
  
## <a name="initializing-members"></a>メンバーの初期化  
 `Enum`ステートメントで選択したメンバーの内容を初期化できる`memberlist`します。 使用する`initializer`メンバーに割り当てられる式を指定します。  
  
 指定しない場合`initializer`のメンバーは、Visual Basic を初期化しますが 0 のいずれか (場合、最初は`member`で`memberlist`)、またはよりも、すぐに上記のいずれかで大きな値に`member`。  
  
 それぞれに提供する式`initializer`リテラル、既に定義されている他の定数と既に定義されている、この列挙体の前のメンバーを含む列挙型メンバーの組み合わせにすることができます。 算術演算および論理演算子を使用すると、このような要素を結合します。  
  
 変数または関数で使用することはできません`initializer`します。 変換キーワードなどを使用するただし、`CByte`と`CShort`します。 使用することも`AscW`定数で呼び出す場合`String`または`Char`引数、コンパイル時に評価できるためです。  
  
 列挙体は、浮動小数点値を持つことはできません。 メンバーには、浮動小数点値が割り当てられている場合と`Option Strict`に設定されている、コンパイラ エラーが発生します。 場合`Option Strict`に値が自動的に変換がオフ、`Enum`型。  
  
 メンバーの値が基になるデータ型の許容範囲を超えた場合、または基になるデータ型で許容される最大値に任意のメンバーを初期化する場合は、コンパイラはエラーを報告します。  
  
## <a name="modifiers"></a>修飾子  
 クラス、構造体、モジュール、およびパブリック アクセスにインターフェイス メンバーの列挙体の既定です。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 Namespace フレンド アクセスを既定値の列挙体をメンバーです。 Private または protected にありませんが、パブリックにアクセス レベルを調整することができます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
 すべての列挙体メンバーは、パブリック アクセスを持ち、それらでアクセス修飾子を使用することはできません。 ただし、列挙型自体にさらに制限されたアクセス レベルがある場合は、指定した列挙体のアクセス レベルが優先されます。  
  
 既定では、すべての列挙体は型とそのフィールドは定数です。 そのため、 `Shared`、 `Static`、および`ReadOnly`列挙型またはそのメンバーを宣言するときに、キーワードを使用できません。  
  
## <a name="assigning-multiple-values"></a>複数の値を割り当てる  
 列挙体は、通常、相互に排他的な値を表します。 含めることによって、<xref:System.FlagsAttribute>属性、`Enum`宣言では、代わりに値を代入できます複数列挙体のインスタンスにします。 <xref:System.FlagsAttribute>属性は、列挙体をビット フィールド、つまりフラグのセットとして扱われることを指定します。 これらと呼びます*ビット*列挙体。  
  
 使用して列挙体を宣言する場合、<xref:System.FlagsAttribute>属性、お勧めの値は、2、1、2、4、8、16、およびの累乗を使用することです。 また、値が 0 のメンバーの名前を"None"ことをお勧めします。 追加のガイドラインについては、次を参照してください。<xref:System.FlagsAttribute>と<xref:System.Enum>します。  
  
## <a name="example"></a>例  
 `Enum` ステートメントを使用する方法の例を次に示します。 メンバーと呼びます注`EggSizeEnum.Medium`ではなく`Medium`します。  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a>例  
 次の例では、メソッドが範囲外です、`Egg`クラス。 そのため、`EggSizeEnum`として完全に修飾されます`Egg.EggSizeEnum`します。  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a>例  
 次の例では、`Enum`という名前の定数値を関連のセットを定義するステートメント。 ここでは、値は、色のデータベースのデータ入力フォームをデザインすることもできます。  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a>例  
 次の例では、正と負の両方の数値を含む値を示します。  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a>例  
 次の例では、`As`句を使用して、指定、`datatype`列挙体の。  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a>例  
 次の例では、ビットごとの列挙型を使用する方法を示します。 複数の値は、ビットごとの列挙体のインスタンスに割り当てることができます。 `Enum`宣言が含まれる、<xref:System.FlagsAttribute>属性には、列挙型をフラグのセットとして処理できることを示します。  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a>例  
 次の例は、列挙型を反復処理します。 使用して、 <xref:System.Enum.GetNames%2A> 、列挙体のメンバー名の配列を取得するメソッドをおよび<xref:System.Enum.GetValues%2A>メンバーの値の配列を取得します。  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)
