---
title: クエリ プランのキャッシュ (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9f042d46d9a601c1091e36f8d81ce8f933140b20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613665"
---
# <a name="query-plan-caching-entity-sql"></a>クエリ プランのキャッシュ (Entity SQL)
クエリの実行が試行されると、クエリ パイプラインではそのクエリ プランのキャッシュを検索し、同じクエリが既にコンパイルされ使用可能になっているかどうかを確認します。 使用可能になっている場合は、新しいクエリを構築する代わりに、キャッシュされたプランを再利用します。 クエリ プランのキャッシュ内に一致するものが見つからない場合は、クエリがコンパイルされ、キャッシュされます。 クエリはその [!INCLUDE[esql](../../../../../../includes/esql-md.md)] テキストとパラメーターのコレクション (名前と型) によって識別されます。 テキストの比較では、常に大文字と小文字が区別されます。  
  
## <a name="configuration"></a>構成  
 クエリ プランのキャッシュは <xref:System.Data.EntityClient.EntityCommand> を使用して構成できます。  
  
 <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> でクエリ プランのキャッシュを有効または無効にするには、このプロパティを `true` または `false` に設定します。 2 回以上使用する予定がない個別の動的クエリ プランのキャッシュを無効にすると、パフォーマンスが向上します。  
  
 <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> を使用してクエリ プランのキャッシュを有効にできます。  
  
## <a name="recommended-practice"></a>推奨される使用方法  
 一般的に、動的クエリは避けてください。 次の動的クエリ例は、検証を行わずにユーザー入力をそのまま受け入れるので、SQL インジェクション攻撃に対して脆弱です。  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 動的に生成されたクエリを使用する場合は、再利用される可能性の低いキャッシュ エントリのためにメモリが不必要に消費されないように、クエリ プランのキャッシュを無効にすることをお勧めします。  
  
 静的クエリおよびパラメーター化クエリに対してクエリ プランをキャッシュすると、パフォーマンスが向上します。 以下は、静的クエリの例です。  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 クエリ プランのキャッシュでクエリを適切に一致させるには、次の要件に従う必要があります。  
  
- クエリ テキストは定数パターンにする必要があり、最も望ましいのは定数文字列またはリソースです。  
  
- ユーザーが指定した値を渡す必要があるときは、<xref:System.Data.EntityClient.EntityParameter> または <xref:System.Data.Objects.ObjectParameter> を使用します。  
  
 クエリ プランのキャッシュ内のスロットを必要以上に消費する次のようなクエリ パターンは避けます。  
  
- テキストの大文字または小文字の変更  
  
- 空白への変更  
  
- リテラル値への変更  
  
- コメント内のテキストの変更  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
