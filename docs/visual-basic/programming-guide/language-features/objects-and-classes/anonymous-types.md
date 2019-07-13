---
title: 匿名型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: ef48ff1bbf79be981b8b8d4148f818fe40b72353
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632184"
---
# <a name="anonymous-types-visual-basic"></a>匿名型 (Visual Basic)
Visual Basic では、データ型のクラス定義を記述せずにオブジェクトを作成することを有効にする匿名型をサポートしています。 クラスは、コンパイラによって生成されます。 クラスは、使用可能な名前を持たないから直接継承<xref:System.Object>オブジェクトの宣言で指定したプロパティが含まれます。 として参照にはデータ型の名前が指定されていないため、*匿名型*します。  
  
 次の例では、宣言し、変数を作成します。`product`を 2 つのプロパティを持つ匿名型のインスタンスとして`Name`と`Price`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 A*クエリ式*匿名型を使用して、クエリによって選択されたデータの列を結合します。 特定のクエリで選択される列を予測できないため、事前に結果の型を定義することはできません。 匿名型では、任意の順序で列の任意の数を選択するクエリを記述できます。 コンパイラは、指定したプロパティと、指定した順序と一致するデータ型を作成します。  
  
 次の例で`products`多くのプロパティを持つ製品のオブジェクトの一覧を示します。 変数`namePriceQuery`、実行時は、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`Price`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 変数`nameQuantityQuery`、実行時は、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`OnHand`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 匿名型のためにコンパイラによって作成されたコードの詳細については、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)します。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラが生成され、コンパイルするたびに異なる場合があります。 コードをいないを使用して、または、プロジェクトが再コンパイルされるとき、名前が変わる可能性がある匿名型の名前に依存します。  
  
## <a name="declaring-an-anonymous-type"></a>匿名型の宣言  
 匿名型のインスタンスの宣言では、型のプロパティを指定するのに初期化子リストを使用します。 匿名型、メソッドやイベントなどの他のクラス要素いないを宣言するときに、プロパティのみを指定できます。 次の例では、`product1`を 2 つのプロパティを持つ匿名型のインスタンスです。`Name`と`Price`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 キー プロパティとしてプロパティを指定する場合は、2 つの匿名型のインスタンスの等価性を比較に使用できます。 ただし、キー プロパティの値を変更できません。 詳細については、このトピックの後半では、キーのプロパティを参照してください。  
  
 オブジェクト初期化子を使用して名前付きの型のインスタンスを宣言するようが匿名型のインスタンスを宣言することに注意してください。  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 匿名型のプロパティを指定する他の方法の詳細については、次を参照してください。[方法。匿名型の宣言におけるプロパティ名と型を推論](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)します。  
  
## <a name="key-properties"></a>キー プロパティ  
 キー プロパティは、いくつかの基本的な方法でキー以外のプロパティとは異なります。  
  
- キー プロパティの値だけは、2 つのインスタンスが等しいかどうかを判断するために比較されます。  
  
- キー プロパティの値は読み取り専用と、変更することはできません。  
  
- のみ、匿名型のコンパイラによって生成されたハッシュ コード アルゴリズムでは、キーのプロパティ値が含まれます。  
  
### <a name="equality"></a>等価比較  
 匿名型のインスタンスは、同じ匿名型のインスタンスの場合のみ等しいとすることはできます。 コンパイラでは、次の条件を満たしている場合に 2 つのインスタンスと同じ型のインスタンスとして扱います。  
  
- 同じアセンブリ内で宣言されています。  
  
- プロパティは、同じ名前では、推論された型、および同じ順序で宣言されます。 名前の比較は区別されません。  
  
- それぞれの同じプロパティは、キー プロパティとしてマークされます。  
  
- 各宣言内の少なくとも 1 つのプロパティは、キー プロパティです。  
  
 キー プロパティを持たない匿名の型のインスタンスはのみにします。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 そのキー プロパティの値が等しい場合、同じ匿名型の 2 つのインスタンスは等しいです。 次の例では、等しいかどうかをテストする方法を示します。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>読み取り専用の値  
 キー プロパティの値を変更できません。 たとえば、`prod8`前の例で、`Name`と`Price`フィールドは`read-only`が`OnHand`変更できます。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>クエリ式からの匿名型  
 クエリ式では、匿名型の作成は常に必要はありません。 可能であれば、列のデータを保持するために、既存の型が使用します。 これは、クエリ、データ ソースまたは各レコードから 1 つだけのフィールドからレコード全体が返されるときに発生します。 次のコード例で`customers`のオブジェクトのコレクションには、`Customer`クラス。 クラスには、多くのプロパティと任意の順序で、クエリ結果のうち 1 つ以上を含めることができます。 最初の 2 つの例では、匿名型は必要ありませんので、クエリが名前付きの型の要素を選択します。  
  
- `custs1` に、文字列のコレクションを格納`cust.Name`は文字列です。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2` コレクションを格納`Customer`ため、オブジェクトの各要素`customers`は、`Customer`オブジェクト、および全体の要素は、クエリで選択されます。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 ただし、適切な名前付きの型は、利用できません。 顧客の名前と目的の 1 つ、顧客 ID 番号、別の場所のアドレスと顧客の名前、アドレス、および 3 番目の注文履歴を選択する場合があります。 匿名型では、任意の順序で結果を保持する新しい名前付きの型を宣言する前に、プロパティの任意の組み合わせを選択できます。 代わりに、コンパイラは、プロパティのコンパイルごとの匿名型を作成します。 次のクエリは、それぞれからのみ、顧客の名前と ID 番号を選択します。`Customer`オブジェクト`customers`します。 そのため、コンパイラは、これら 2 つのプロパティのみを含む匿名型を作成します。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 名前と匿名型のプロパティのデータ型の両方が引数から取得されます`Select`、`cust.Name`と`cust.ID`します。 クエリによって作成される匿名型のプロパティは、常に、キーのプロパティです。 ときに`custs3`が、次に実行される`For Each`ループ、結果は、2 つのキー プロパティを持つ匿名型のインスタンスのコレクション`Name`と`ID`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 によって表されるコレクション内の要素`custs3`厳密に型指定し、使用可能なプロパティをナビゲートし、その型を確認するのには、IntelliSense を使用することができます。  
  
 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>匿名型を使用するかどうかを決定します。  
 匿名クラスのインスタンスとしてオブジェクトを作成する前に、最適なオプションがあるかどうかを検討してください。 たとえば場合は、関連するデータを格納する一時オブジェクトを作成して、その他のフィールドやメソッドが含まれる完全なクラスの必要はありません、匿名型は優れたソリューションです。 匿名型は、宣言ごとに異なるプロパティを選択する場合、またはプロパティの順序を変更する場合にも便利です。 ただし、プロジェクトには、一定の順序で、同じプロパティがありますをいくつかのオブジェクトが含まれている場合ことでも宣言できますより簡単にクラス コンス トラクターを持つ名前付きの型を使用しています。 たとえば、適切なコンス トラクターではの複数のインスタンスを宣言しやすく、`Product`クラス、匿名型のいくつかのインスタンスを宣言するよりもします。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 名前付きの型のもう 1 つの利点は、コンパイラがプロパティ名のタイプミスをキャッチできることです。 前の例で`firstProd2`、 `secondProd2`、および`thirdProd2`同じ匿名型のインスタンスにする対象としています。 ただし、誤ってにした場合宣言`thirdProd2`、次の方法の 1 つは、その型は異なることには`firstProd2`と`secondProd2`します。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 さらに、名前付きの型のインスタンスに適用されない匿名型の使用に関する制限事項があります。 `firstProd2`、 `secondProd2`、および`thirdProd2`は、同じ匿名型のインスタンスです。 ただし、共有の匿名型の名前は、ご利用いただけません、コードで型名が必要な場合は使用できません。 たとえば、匿名型を使用して、別の変数またはフィールド、または任意の型の宣言で宣言、メソッド シグネチャを定義することはできません。 その結果、メソッド間で情報を共有するときに匿名型は適していません。  
  
## <a name="an-anonymous-type-definition"></a>匿名型の定義  
 匿名型のインスタンスの宣言に応答してでは、コンパイラは、指定したプロパティを格納する新しいクラス定義を作成します。  
  
 定義から継承された 3 つのメンバーよりも優先されますが、匿名型に少なくとも 1 つのキー プロパティが含まれている場合<xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>します。 等しいかどうかをテストし、ハッシュ コード値は、主要なプロパティのみを考慮を決定するために生成されるコード。 匿名型にのみキー プロパティが含まれていないかどうかは<xref:System.Object.ToString%2A>オーバーライドされます。 生成されたこれらのメソッドと競合する、匿名型のプロパティを明示的に指定できません。 つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`にプロパティの名前します。  
  
 匿名型の定義には少なくとも 1 つを持つキー プロパティも実装、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の種類です。  
  
 コンパイラとオーバーライドされたメソッドの機能によって作成されたコードの詳細については、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)します。  
  
## <a name="see-also"></a>関連項目

- [オブジェクト初期化子:名前付きの匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [方法: 匿名型の宣言におけるプロパティ名と型を推論します。](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名型の定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
