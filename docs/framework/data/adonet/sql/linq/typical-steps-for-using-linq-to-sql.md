---
title: 典型的な LINQ to SQL の使用手順
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: c7964c821a838e027302cddce704d86cc6a34f66
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792347"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>典型的な LINQ to SQL の使用手順
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装するには、このトピックで説明する手順に従います。 多くの手順は省略できます。 既定の状態でオブジェクト モデルを使用することもできます。  
  
 非常に高速に開始するには、オブジェクトリレーショナルデザイナーを使用してオブジェクトモデルを作成し、クエリのコーディングを開始します。  
  
## <a name="creating-the-object-model"></a>オブジェクト モデルの作成  
 最初に、既存のリレーショナル データベースのメタデータからオブジェクト モデルを作成します。 オブジェクト モデルは、開発者のプログラミング言語に従ってデータベースを表します。 詳細については、「 [LINQ to SQL オブジェクトモデル](the-linq-to-sql-object-model.md)」を参照してください。  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1.モデルを作成するツールを選択します。  
 モデルを作成するツールとして、3 つのツールを使用できます。  
  
- オブジェクトリレーショナルデザイナー  
  
     このデザイナーは、既存のデータベースからモデルを作成する多機能なユーザー インターフェイスを備えています。 このツールは Visual Studio IDE の一部であり、小規模または中規模のデータベースに最適です。  
  
- SQLMetal コード生成ツール  
  
     このコマンドラインユーティリティは、O/R デザイナーとは若干異なるオプションセットを提供します。 このツールは、大規模なデータベースのモデル化に適しています。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
- コード エディター  
  
     Visual Studio コードエディターまたは別のエディターを使用して、独自のコードを記述することができます。 この方法は、既存のデータベースがあり、O/R デザイナーまたは SQLMetal ツールを使用できる場合に、エラーが発生する可能性があるため、お勧めしません。 ただし、コード エディターは、他のツールを使用して既に生成されたコードを調整または変更する場合に役立ちます。 詳細については、「[方法 :コードエディター](how-to-customize-entity-classes-by-using-the-code-editor.md)を使用してエンティティクラスをカスタマイズします。  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2.生成するコードの種類を選択します。  
  
- C#または Visual Basic 属性ベースのマッピング用のソースコードファイル。  
  
     次に、このコードファイルを Visual Studio プロジェクトに含めます。 詳細については、「[属性ベースのマッピング](attribute-based-mapping.md)」を参照してください。  
  
- 外部マッピング用の XML ファイル。  
  
     この方法を使用すると、アプリケーション コードとは別にマッピング メタデータを保持できます。 詳細については、「[外部マッピング](external-mapping.md)」を参照してください。  
  
    > [!NOTE]
    > O/R デザイナーは、外部マッピングファイルの生成をサポートしていません。 SQLMetal ツールを使用してこの機能を実装する必要があります。  
  
- 最終コード ファイルを生成する前に変更できる DBML ファイル。  
  
     これは高度な機能です。  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3.コード ファイルを調整して、アプリケーションのニーズを反映します。  
 このためには、O/R デザイナーまたはコードエディターを使用できます。  
  
## <a name="using-the-object-model"></a>オブジェクト モデルの使用  
 2 層シナリオでの開発者とデータの関係を次の図に示します。 その他のシナリオについては、「 [LINQ to SQL を使用した N 層とリモートアプリケーション](n-tier-and-remote-applications-with-linq-to-sql.md)」を参照してください。  
  
 ![Linq オブジェクトモデルを示すスクリーンショット。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 オブジェクト モデルが完成したので、そのモデル内で情報要求を記述し、データを操作します。 オブジェクト モデルのオブジェクトとプロパティを使用し、データベースの行と列は使用しません。 データベースを直接操作することはありません。  
  
 クエリを実行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]するように指示した場合、または操作`SubmitChanges()`したデータに対してを[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]呼び出す場合、はデータベースの言語でデータベースと通信します。  
  
 作成したオブジェクト モデルの典型的な使用手順を次に示します。  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1.クエリを作成し、データベースから情報を取得します。  
 詳細については、「[クエリの概念](query-concepts.md)」および「[クエリの例](query-examples.md)」を参照してください。  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2.挿入、更新、および削除の既定の動作をオーバーライドします。  
 この手順は省略できます。 詳細については、「[挿入、更新、および削除の操作をカスタマイズ](customizing-insert-update-and-delete-operations.md)する」を参照してください。  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3.適切なオプションを設定し、コンカレンシーの競合を検出およびレポートします。  
 コンカレンシーの競合の処理について、モデルの既定値をそのまま使用することも、目的に合わせて変更することもできます。 詳細については、「[方法 :同時実行の競合](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)をテストするメンバーと、 [次の方法を指定します。同時実行例外をいつスロー](how-to-specify-when-concurrency-exceptions-are-thrown.md)するかを指定します。  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4.継承階層を確立します。  
 この手順は省略できます。 詳細については、「[継承のサポート](inheritance-support.md)」を参照してください。  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5.適切なユーザー インターフェイスを提供します。  
 この手順は省略でき、アプリケーションの使用方法によって異なります。  
  
### <a name="6-debug-and-test-your-application"></a>6.アプリケーションをデバッグおよびテストします。  
 詳細については、「[デバッグのサポート](debugging-support.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [はじめに](getting-started.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
- [ストアド プロシージャ](stored-procedures.md)
