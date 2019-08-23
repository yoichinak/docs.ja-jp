---
title: オプティミスティック コンカレンシー:概要
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: a61d4c5b35f3797539fe845045b8a959b0351350
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938626"
---
# <a name="optimistic-concurrency-overview"></a>オプティミスティック コンカレンシー:概要
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はオプティミスティック コンカレンシーをサポートします。 次の表では、ドキュメントで[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オプティミスティック同時実行に適用される用語について説明します。  
  
|用語|説明|  
|-----------|-----------------|  
|コンカレンシー|2 人以上のユーザーがデータベースの同じ行を同時に更新しようとした状況のことです。|  
|コンカレンシーの競合|2 人以上のユーザーが、行の中の 1 つまたは複数の列に対し、互いに競合する値を送信しようとした状況のことです。|  
|コンカレンシー制御|コンカレンシーの競合を解決するために使用する手法のことです。|  
|オプティミスティック コンカレンシー|他のトランザクションが行の値に変更を加えていないかどうかをまず調べたうえで変更の送信を許可する手法のことです。<br /><br /> ペシミスティック同時*実行制御*とは対照的に、同時実行の競合を避けるためにレコードをロックします。<br /><br /> *オプティミスティック*コントロールは、あるトランザクションが別のトランザクションに干渉する可能性が低いと見なされるため、このように呼ばれます。|  
|競合の解決|データベースを再度クエリしてから相違点を調整することによって競合する項目を更新する処理のことです。<br /><br /> オブジェクトを更新するときには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の変更トラッカーによって、以下のデータが記録されます。<br /><br /> -最初にデータベースから取得され、更新チェックに使用される値。<br />-以降のクエリの新しいデータベース値。<br /><br /> 次に [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトが競合しているかどうか (つまり 1 つまたは複数のメンバー値が変更されているかどうか) を判断します。 オブジェクトが競合している場合[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、は、どのメンバーが競合しているかを判断します。<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が見つけたメンバーの競合は、競合の一覧に追加されます。|  
  
 オブジェクトモデルでは、次の両方の条件に該当する場合、*オプティミスティック同時実行制御の競合*が発生します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- クライアントがデータベースに変更を送信しようとした。  
  
- データベースで、そのクライアントによる最後の読み取り以降に、1 つまたは複数の更新チェック値が更新されている。  
  
 この競合を解決するためには、オブジェクトのどのメンバーが競合しているかを判別し、どのように対処するかを決定することが必要です。  
  
> [!NOTE]
> オプティミスティック コンカレンシーのチェックに関与するのは、<xref:System.Data.Linq.Mapping.UpdateCheck.Always> または <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> として割り当てられているメンバーのみです。 <xref:System.Data.Linq.Mapping.UpdateCheck.Never> と指定されているメンバーには、チェックは実行されません。 詳細については、「 <xref:System.Data.Linq.Mapping.UpdateCheck> 」を参照してください。  
  
## <a name="example"></a>例  
 次のシナリオは、ユーザー 1 が、更新の手始めとして、データベースの行をクエリした状況です。 ユーザー 1 が取得した行には、Alfreds、Maria、および Sales という値が入っています。  
  
 ユーザー 1 は、Manager 列の値を Alfred に、また Department 列の値を Marketing に、それぞれ変更しようと考えています。 しかし、ユーザー 1 がその変更を発行する前に、ユーザー 2 がデータベースに変更を送信しました。 その結果、Assistant 列の値は Mary に、また Department 列の値は Service に、それぞれ変更されました。  
  
 ここで、ユーザー 1 が変更を送信しようとすると、送信は失敗し、<xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。 このような結果になるのは、データベースの Assistant 列と Department 列の値が、予期した値と異なるためです。 Assistant 列と Department 列を表すメンバーが競合しています。 この状況をまとめると次の表のようになります。  
  
||管理者|Assistant|Department|  
|------|-------------|---------------|----------------|  
|元の状態|Alfreds|Maria|販売|  
|ユーザー 1|Alfred||マーケティング|  
|ユーザー 2||Mary|サービス|  
  
 このような競合は、いくつかの方法で解決できます。 詳細については、「[方法 :変更の競合](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)を管理します。  
  
## <a name="conflict-detection-and-resolution-checklist"></a>競合の検出と解決のチェック リスト  
 競合の検出と解決は、さまざまな詳細レベルで行うことができます。 極端な方法としては、すべての競合を 3 つの方法 (<xref:System.Data.Linq.RefreshMode> を参照) のいずれかで 1 つで解決し、それ以外の考慮を一切加えないという方法もあります。 正反対の方法としては、競合している各メンバーについて、それぞれの競合の種類ごとに、特定の処理を指定するという方法もあります。  
  
- オブジェクト モデルの <xref:System.Data.Linq.Mapping.UpdateCheck> オプションを指定または変更します。  
  
     詳細については、「[方法 :同時実行の競合](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)をテストするメンバーを指定します。  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出しの try/catch ブロックで、例外がどの時点でスローされるかを指定します。  
  
     詳細については、「[方法 :同時実行例外をいつスロー](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)するかを指定します。  
  
- 取得する競合の詳細さを判断し、それに応じたコードを try/catch ブロックに記述します。  
  
     詳細については、「[方法 :エンティティの競合情報](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)を[取得し、次の操作を行います。メンバーの競合情報](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)を取得します。  
  
- 検出した`try`さまざまな競合を解決する方法を`catch`コードに/含めます。  
  
     詳細については、「[方法 :データベースの値](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)を保持して[競合を解決する方法:データベースの値](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)を上書きして競合[を解決し、次の操作を実行します。データベース値](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)とマージして競合を解決します。  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>競合の発見と解決をサポートする LINQ to SQL の型  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で、オプティミスティック コンカレンシーの競合の解決をサポートするクラスと機能を以下に示します。  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>関連項目

- [方法: 変更の競合を管理する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
