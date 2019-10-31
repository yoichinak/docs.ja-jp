---
title: カスタム データベース関数を呼び出す方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: e357868361e11dc919fa09db9a36185923a6e40e
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847093"
---
# <a name="how-to-call-custom-database-functions"></a>カスタム データベース関数を呼び出す方法

ここでは、データベースで定義されたカスタム関数を LINQ Entities クエリから呼び出す方法について説明します。

LINQ to Entities クエリから呼び出されるデータベース関数は、データベース内で実行されます。 データベース内で関数を実行すると、アプリケーションのパフォーマンスが向上します。

下に示す手順は、カスタム データベース関数を呼び出す方法の概要をまとめたものです。 各手順の詳しい説明は、その後の例で示します。

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>データベースで定義されるカスタム関数を呼び出すには

1. データベースにカスタム関数を作成します。

     SQL Server でカスタム関数を作成する方法の詳細については、「 [CREATE FUNCTION (transact-sql)](https://go.microsoft.com/fwlink/?LinkID=139871)」を参照してください。

2. 関数を .edmx ファイルのストア スキーマ定義言語 (SSDL) で宣言します。 関数の名前は、データベースで宣言される関数と同じ名前にする必要があります。

     詳細については、「 [Function 要素 (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl)」を参照してください。

3. 対応するメソッドをアプリケーション コードのクラスに追加して、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をそのメソッドに適用する必要があります。属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間名と概念モデルの関数名であることに注意してください。 LINQ の関数名解決では、大文字と小文字が区別されます。

4. LINQ to Entities クエリからメソッドを呼び出します。  

## <a name="example"></a>例

次の例は、カスタム データベース関数を LINQ to Entities クエリから呼び出す方法について説明します。 この例では、School モデルを使用します。 School モデルの詳細については、「 [School サンプルデータベースの作成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))」および「 [school .Edmx ファイルの生成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))」を参照してください。

次のコードは、`AvgStudentGrade` 関数を School のサンプル データベースに追加しています。

> [!NOTE]
> カスタム データベース関数を呼び出す手順は、データベース サーバーとは無関係にすべて同じです。 ただし、下に示すコードは、SQL Server データベースで関数を作成する方法に固有のものです。 他のデータベース サーバーでカスタム関数を作成する場合には、コードは異なることがあります。

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>例

次に、 *.edmx*ファイルのストアスキーマ定義言語 (SSDL) で関数を宣言します。 次のコードは、SSDL の `AvgStudentGrade` 関数を宣言しています。

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>例

ここで、メソッドを作成し、SSDL で宣言された関数にマップします。 次のクラスのメソッドは、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用して SSDL (上を参照) で定義される関数にマップされます。 このメソッドが呼び出されると、データベース内の対応する関数が実行されます。

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>例

最後に、メソッドを LINQ to Entities クエリで呼び出します。 次のコードは、学生の姓と平均の成績をコンソールに表示します。

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>関連項目

- [.edmx ファイルの概要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities でのクエリ](queries-in-linq-to-entities.md)
