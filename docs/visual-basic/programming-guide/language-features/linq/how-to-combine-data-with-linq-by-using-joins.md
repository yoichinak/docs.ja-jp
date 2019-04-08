---
title: '方法: 結合 (Visual Basic) を使用してデータを LINQ を結合します。'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: dde627edfeb1d4473c9d2e01b9ff83c580a0f122
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822688"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>方法: 結合 (Visual Basic) を使用してデータを LINQ を結合します。
Visual Basic では、`Join`と`Group Join`コレクション間で共通の値に基づく複数のコレクションの内容を結合するための句をクエリします。 これらの値と呼ばれる*キー*値。 リレーショナル データベースの概念に慣れている開発者が認識、 `Join` INNER JOIN 句、`Group Join`として、実際には、左外部結合句。  
  
 このトピックの例を使用してデータを結合する方法をいくつかを示す、`Join`と`Group Join`クエリ句。  
  
## <a name="create-a-project-and-add-sample-data"></a>プロジェクトを作成し、サンプル データを追加  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>サンプル データと型を含むプロジェクトを作成するには  
  
1.  このトピックのサンプルを実行するには、Visual Studio を開き、新しい Visual Basic コンソール アプリケーション プロジェクトを追加します。 Visual Basic で作成された Module1.vb ファイルをダブルクリックします。  
  
2.  このトピックで使用中のサンプル、`Person`と`Pet`型と、次のコード例からのデータ。 既定値にこのコードをコピー `Module1` Visual Basic で作成されたモジュール。  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Join 句を使用して内部結合を実行します。  
 INNER JOIN によって 2 つのコレクションからデータを結合します。 指定されたキー値に一致する対象のアイテムが含まれます。 その他のコレクションの一致する項目がありません。 いずれかのコレクションからすべての項目が除外されます。  
  
 Visual Basic で LINQ は内部結合を実行するための 2 つのオプションを提供します。 暗黙の結合と明示的な結合します。  
  
 暗黙の結合結合するコレクションの指定、`From`句に一致するキー フィールドを指定して、`Where`句。 Visual Basic は、暗黙的に指定されたキー フィールドに基づいて 2 つのコレクションを結合します。  
  
 使用して、明示的な結合を指定することができます、`Join`句には、どのキー フィールドの結合に使用する場合。 ここで、`Where`句は、クエリ結果をフィルター処理も使用できます。  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Join 句を使用して内部結合を実行するには  
  
1.  次のコードを追加、`Module1`両方暗黙的および明示的な内部結合の例を参照するプロジェクトのモジュール。  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join 句を使用して、左外部結合を実行します。  
 左外部結合には、結合および結合の右側にあるコレクションからの値が一致するのみの左側にあるコレクションからすべての項目が含まれています。 左側のコレクションに一致する項目がない結合の右側にあるコレクションからすべての項目は、クエリ結果から除外されます。  
  
 `Group Join`句実行実際には、左外部結合します。 LEFT OUTER JOIN と通常呼ばれるものとどのような違い、`Group Join`される句を返します、`Group Join`左側にあるコレクション内の各項目の結合の右側にあるコレクションから句のグループの結果。 リレーショナル データベースでは、LEFT OUTER JOIN は、クエリ内の各項目の結果の結果グループに属していないには結合の両方のコレクションから一致する項目が含まれていますを返します。 この場合、結合の左側にあるコレクションからアイテムは、右側にあるコレクションからの一致項目ごとに繰り返されます。 これがどのように、次の手順を完了すると表示されます。  
  
 結果を取得することができます、`Group Join`項目それぞれグループ化されたクエリの結果を返すクエリを拡張することによって、グループに属していない結果としてクエリ。 これを実現するをクエリすることを確認する必要がある、`DefaultIfEmpty`グループ化されたコレクションのメソッド。 これにより、結合の左側にあるコレクションの項目が右側にあるコレクションから一致する結果がない場合でも、クエリ結果に含まれるまだ。 結合の右側にあるコレクションに一致する値がない場合は、既定の結果値を提供するクエリにコードを追加することができます。  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Group Join 句を使用して左外部結合を実行するには  
  
1.  次のコードを追加、`Module1`モジュールで、プロジェクトをグループ化された左外部結合とグループに属していないの左外部結合の両方の例を参照してください。  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>複合キーを使用して、結合を実行します。  
 使用することができます、`And`キーワード、`Join`または`Group Join`句に一致するときに使用する複数のキー フィールドを識別するためには、結合するコレクションの値します。 `And`キーワードは、すべての指定に参加している項目のキー フィールドに一致する必要がありますを指定します。  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>複合キーを使用して、結合を実行するには  
  
1.  次のコードを追加、`Module1`複合キーを使用する結合の例を参照するプロジェクトのモジュール。  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>コードを実行します  
  
#### <a name="to-add-code-to-run-the-examples"></a>例を実行するコードを追加するには  
  
1.  置換、`Sub Main`で、`Module1`このトピックの例を実行する次のコードで、プロジェクトのモジュール。  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2.  F5 キーを押して、例を実行します。  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ によるデータ変換 (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
