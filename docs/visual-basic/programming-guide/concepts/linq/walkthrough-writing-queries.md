---
title: Visual Basic におけるクエリの作成
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: f3671b7071cc30f5fae0dbd85677987f441d846f
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505983"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>チュートリアル: Visual Basic におけるクエリの作成
このチュートリアルでは、Visual Basic 言語の機能を使用して、記述する方法について説明[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ式。 このチュートリアルでは、学生オブジェクトの一覧にクエリを作成する方法、クエリを実行する方法、およびそれらを変更する方法を示します。 クエリでは、オブジェクト初期化子、ローカル型推論では、匿名型など、いくつかの機能を組み込みます。  
  
 このチュートリアルを完了できるようになりますサンプルと、特定のドキュメントに移動する準備ができて[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーには、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、LINQ to DataSet、および[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]します。  
  
## <a name="create-a-project"></a>プロジェクトの作成  
  
#### <a name="to-create-a-console-application-project"></a>コンソール アプリケーション プロジェクトを作成するには  
  
1. Visual Studio を起動します。  
  
2. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3. **インストールされたテンプレート**一覧で、 **Visual Basic**します。  
  
4. プロジェクトの種類の一覧でクリックして**コンソール アプリケーション**します。 **名前**ボックスで、プロジェクトの名前を入力し、クリックして**OK**。  
  
     プロジェクトが作成されます。 既定では、System.Core.dll への参照が含まれます。 また、**インポートされた名前空間**ボックスの一覧、[参照設定 ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)が含まれています、<xref:System.Linq?displayProperty=nameWithType>名前空間。  
  
5. [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**で**します。  
  
## <a name="add-an-in-memory-data-source"></a>メモリ内データ ソースを追加します。  
 このチュートリアルのクエリのデータ ソースの一覧は、`Student`オブジェクト。 各`Student`オブジェクトには、名、姓、名、クラスの年、および学生の本文に教育機関のランクが含まれています。  
  
#### <a name="to-add-the-data-source"></a>データ ソースを追加するには  
  
- 定義、`Student`クラスおよびクラスのインスタンスの一覧を作成します。  
  
    > [!IMPORTANT]
    >  定義に必要なコード、`Student`クラスを使用するリストの作成のチュートリアルで例が提供されている[方法。項目の一覧を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。 そこからコピーして、プロジェクトに貼り付けます。 新しいコード プロジェクトを作成したときに表示されたコードで置き換えます。  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>学生のリストに新しい生徒を追加するには  
  
- パターンに従い、`getStudents`の別のインスタンスを追加するメソッドを`Student`クラスの一覧にします。 受講者を追加することをオブジェクト初期化子が紹介されます。 詳細については、次を参照してください。[オブジェクト初期化子。名前付きの匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。  
  
## <a name="create-a-query"></a>クエリを作成する  
 実行すると、このセクションでは追加のクエリは、学生の成績順位に上位 10 件の配置の一覧を生成します。 完全なクエリが選択されるので`Student`オブジェクトたびに、クエリ結果の型が`IEnumerable(Of Student)`します。 ただし、クエリの種類通常が指定されていないクエリの定義にします。 代わりに、コンパイラは、種類を決定するのにローカル型推論を使用します。 詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。 クエリの範囲変数、 `currentStudent`、それぞれへの参照として機能`Student`、ソース内のインスタンス`students`、内の各オブジェクトのプロパティへのアクセスを提供する`students`します。  
  
#### <a name="to-create-a-simple-query"></a>簡単なクエリを作成するには  
  
1. 内の位置を検索、`Main`次のようにマークされているプロジェクトのメソッド。  
  
     [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]  
  
     次のコードをコピーして貼り付けます。  
  
     [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]  
  
2. マウス ポインターを合わせる`studentQuery`コンパイラによって割り当てられた型があることを確認するコードで`IEnumerable(Of Student)`します。  
  
## <a name="run-the-query"></a>クエリを実行します。  
 変数`studentQuery`クエリの実行結果ではありません、クエリの定義が含まれています。 クエリを実行するための一般的なメカニズムは、`For Each`ループします。 返されたシーケンス内の各要素は、ループの反復変数を通じてアクセスされます。 クエリの実行の詳細については、次を参照してください。[書き込みで初めて Your の LINQ クエリ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
#### <a name="to-run-the-query"></a>クエリを実行するには  
  
1. 次の追加`For Each`プロジェクト内のクエリの下のループします。  
  
     [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]  
  
2. ループ コントロール変数の上にマウス ポインターを置く`studentRecord`にそのデータ型を参照してください。 型`studentRecord`推論されます`Student`ため、`studentQuery`のコレクションを返します`Student`インスタンス。  
  
3. 構築し、CTRL + f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
## <a name="modify-the-query"></a>クエリの変更  
 指定した順序内にある場合は、クエリの結果をスキャンしやすくなります。 使用可能なフィールドに基づいて、返されたシーケンスを並べ替えることができます。  
  
#### <a name="to-order-the-results"></a>結果を並べ替えるには  
  
1. 次の追加`Order By`句の間、`Where`ステートメントおよび`Select`クエリのステートメント。 `Order By`句は結果の順序をアルファベット順に A から z、に従って最後の各生徒の名前。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2. 姓の最初の名前順で並べ替えには、クエリに両方のフィールドを追加します。  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     指定することも`Descending`Z から a の順に  
  
3. 構築し、CTRL + f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-introduce-a-local-identifier"></a>ローカル識別子を導入するには  
  
1. クエリ式でのローカル識別子を導入するには、このセクションでは、コードを追加します。 ローカルの識別子では、中間結果を保持します。 次の例では、`name`受講者を連結したものを保持する識別子の最初と姓と名は、します。 便宜上、ローカル識別子を使用できますか、複数回を計算するそれ以外の場合は、式の結果を格納することでパフォーマンスの向上につながります。  
  
     [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]  
  
2. 構築し、CTRL + f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Select 句で 1 つのフィールドを射影するには  
  
1. クエリの追加と`For Each`ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションからループします。 次の例では、ソースが一連の`Student`オブジェクトではなく各オブジェクトの 1 メンバーのみが返されます。 姓が Garcia 学生の姓。 `currentStudent.First`によって返されるシーケンスのデータ型の文字列`studentQuery3`は`IEnumerable(Of String)`文字列のシーケンス。 前の例のように、データの割り当てを入力`studentQuery3`はローカル型推論を使用して確認するコンパイラの残しておきます。  
  
     [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]  
  
2. マウス ポインターを合わせる`studentQuery3`割り当てられた型があることを確認するコードで`IEnumerable(Of String)`します。  
  
3. 構築し、CTRL + f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select 句で匿名型を作成するには  
  
1. クエリで使用する方法に匿名型を表示するには、このセクションのコードを追加します。 完全な記録ではなく、データ ソースからいくつかのフィールドを取得するときにクエリで使用する (`currentStudent`前の例でのレコード) 1 つのフィールド (`First`前のセクションで)。 内のフィールドを指定する結果に含めるフィールドを含む新しい名前付きの型を定義するには、代わりに、`Select`句と、コンパイラは、それらのフィールドのプロパティとして持つ匿名型を作成します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例では、名前と成績順位の 1 ~ 10 の教育機関のランクの順序で、最上級生のランクを返すクエリを作成します。 この例では、型で`studentQuery4`ため、推論する必要があります、`Select`句は、匿名型のインスタンスを返し、匿名型に使用できる名前がありません。  
  
     [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]  
  
2. 構築し、CTRL + f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
## <a name="additional-examples"></a>その他の例  
 電源と柔軟性を説明するためにその他の例の一覧を次に、基本を理解したところで[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 それぞれの例には、機能の簡単な説明が付きます。 推論された型を表示するには、各クエリのクエリ結果の変数にマウス ポインターを置きます。 使用して、`For Each`ループを使用して、結果を生成します。  
  
 [!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]  
  
## <a name="additional-information"></a>追加情報  
 特定の種類のドキュメントとサンプルを読み取る準備が完了したらクエリの基本的な概念を理解したら、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [オブジェクト初期化子:名前付きの匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
