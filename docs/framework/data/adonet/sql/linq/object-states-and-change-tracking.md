---
title: オブジェクトの状態と変更の追跡
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 8de415ba68ca1b0a5c4214e586ad2a4d4940690a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953228"
---
# <a name="object-states-and-change-tracking"></a>オブジェクトの状態と変更の追跡
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクトは常に何らかの*状態*に関与します。 たとえば、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が新しいオブジェクトを作成すると、そのオブジェクトは `Unchanged` 状態です。 自分で作成した新しいオブジェクトは、 <xref:System.Data.Linq.DataContext>にとって不明であり、状態に`Untracked`あります。 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が正常に実行されると、すべてのオブジェクトが [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] にとって既知となり、`Unchanged` 状態になります (データベースから削除されたオブジェクトは例外です。これは `Deleted` 状態であり、<xref:System.Data.Linq.DataContext> インスタンスの中で使用できません)。  
  
## <a name="object-states"></a>オブジェクトの状態  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] オブジェクトで有効な状態を次の表に示します。  
  
|状態|説明|  
|-----------|-----------------|  
|`Untracked`|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって追跡されないオブジェクト。 具体的には次のものがあります。<br /><br /> -現在<xref:System.Data.Linq.DataContext>のを使用してクエリを実行しないオブジェクト (新しく作成されたオブジェクトなど)。<br />-逆シリアル化によって作成されたオブジェクト<br />-別<xref:System.Data.Linq.DataContext>のを使用してクエリを実行するオブジェクト。|  
|`Unchanged`|現在の <xref:System.Data.Linq.DataContext> を使用して取得され、作成後に変更された履歴がないオブジェクト。|  
|`PossiblyModified`|に<xref:System.Data.Linq.DataContext>*アタッチ*されているオブジェクト。 詳細については、「 [N 層アプリケーションでのデータの取得と CUD の操作 (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)」を参照してください。|  
|`ToBeInserted`|現在の <xref:System.Data.Linq.DataContext> を使用して取得されていないオブジェクト。 この場合、`INSERT` 中にデータベースの <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が発生します。|  
|`ToBeUpdated`|取得後に変更された履歴があるオブジェクト。 この場合、`UPDATE` 中にデータベースの <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が発生します。|  
|`ToBeDeleted`|削除がマークされているオブジェクト。`DELETE` 中にデータベースの <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が発生します。|  
|`Deleted`|データベース内で削除されたオブジェクト。 これは最後の状態であり、次の状態に移行できません。|  
  
## <a name="inserting-objects"></a>オブジェクトの挿入  
 `Inserts` を使用して、<xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> を明示的に要求できます。 また、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は、 `Inserts`更新する必要がある既知のオブジェクトのいずれかに接続されているオブジェクトを検索することによって推論できます。 たとえば`Untracked` 、オブジェクトを<xref:System.Data.Linq.EntityRef%601> <xref:System.Data.Linq.EntitySet%601>に追加し`Untracked`たり、をオブジェクトに設定したりすると、グラフ内`Untracked`の追跡対象オブジェクトによってオブジェクトに到達できるようになります。 処理<xref:System.Data.Linq.DataContext.SubmitChanges%2A>中、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は追跡対象オブジェクトを走査し、追跡されない、到達可能なすべての永続オブジェクトを検出します。 このようなオブジェクトは、データベースへの挿入候補です。  
  
 継承階層のクラスの場合、 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) は、*識別子*として指定されたメンバーの値をオブジェクト`o`の型と一致するように設定します。 既定の識別子の値の型が一致する場合、この操作によって、識別子の値が既定値で上書きされます。 詳細については、「[継承のサポート](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)」を参照してください。  
  
> [!IMPORTANT]
> `Table` に追加されたオブジェクトは、ID キャッシュにはありません。 ID キャッシュは、データベースから取得されたもののみを反映します。 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> を呼び出した後、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> が正常終了するまで、追加されたエンティティはデータベースに対するクエリで使用されません。  
  
## <a name="deleting-objects"></a>オブジェクトの削除  
 適切な `o` で <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) を呼び出すことにより、追跡オブジェクト <xref:System.Data.Linq.Table%601> に削除のマークを付けることができます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]は<xref:System.Data.Linq.EntitySet%601> 、更新操作としてのオブジェクトの削除を考慮し、対応する外部キー値は null に設定されます。 操作の対象 (`o`) はテーブルから削除されません。 たとえば、`cust.Orders.DeleteOnSubmit(ord)` は、外部キー `cust` を null に設定することによって `ord` と `ord.CustomerID` のリレーションシップが切断される更新を表します。 `ord` に対応する行の削除は行われません。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]テーブルからオブジェクトが削除された (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) ときに、次の処理を実行します。  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すときに、そのオブジェクトに対して `DELETE` 操作が実行されます。  
  
- 関連オブジェクトが読み込まれているかどうかにかかわらず、関連オブジェクトに削除は反映されません。 特に、リレーションシップ プロパティを更新するために関連オブジェクトが読み込まれることはありません。  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A> が正常に実行されると、オブジェクトは `Deleted` 状態に設定されます。 その結果、その `id` で、オブジェクトまたはその <xref:System.Data.Linq.DataContext> を使用することはできません。 データベース内でオブジェクトが削除された後でも、<xref:System.Data.Linq.DataContext> インスタンスによって保持される内部キャッシュは、取得されたオブジェクトや新規として追加されたオブジェクトを消去しません。  
  
 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> によって追跡されたオブジェクトでのみ、<xref:System.Data.Linq.DataContext> を呼び出すことができます。 `Untracked` オブジェクトの場合は、<xref:System.Data.Linq.Table%601.Attach%2A> を呼び出す前に <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> を呼び出す必要があります。 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> オブジェクトで `Untracked` を呼び出すと、例外がスローされます。  
  
> [!NOTE]
> テーブル[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]からオブジェクトを削除すると、の<xref:System.Data.Linq.DataContext.SubmitChanges%2A>時点で対応`DELETE`する SQL コマンドが生成されます。 この処理によって、キャッシュからオブジェクトが削除されたり、関連オブジェクトに削除が反映されることはありません。  
>   
>  削除されたオブジェクトの `id` を再要求するには、新しい <xref:System.Data.Linq.DataContext> インスタンスを使用します。 関連オブジェクトをクリーンアップするには、データベースの*cascade delete*機能を使用するか、関連するオブジェクトを手動で削除します。  
>   
>  関連オブジェクトは、データベースの場合とは異なり、特別な順序で削除する必要はありません。  
  
## <a name="updating-objects"></a>オブジェクトの更新  
 変更の通知を確認することで、`Updates` を検出できます。 通知は、プロパティ Set アクセス操作子の <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> イベントを通じて提供されます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトへの最初の変更が通知されると、オブジェクトのコピーを作成し、オブジェクトを、`Update` ステートメントを生成する候補と見なします。  
  
 を実装<xref:System.ComponentModel.INotifyPropertyChanging>していないオブジェクト[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の場合、は、オブジェクトが最初に具体化されたときに保持していた値のコピーを保持します。 を呼び出す<xref:System.Data.Linq.DataContext.SubmitChanges%2A>と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、は現在の値と元の値を比較して、オブジェクトが変更されたかどうかを判断します。  
  
 リレーションシップの更新の場合、子から親への参照 (つまり、外部キーに対応する参照) が基準と見なされます。 逆方向 (つまり、親から子) の参照はオプションです。 リレーションシップ クラス (<xref:System.Data.Linq.EntitySet%601> および <xref:System.Data.Linq.EntityRef%601>) は、一対多および一対一のリレーションシップで双方向の参照が一致することを保証します。 オブジェクト モデルが <xref:System.Data.Linq.EntitySet%601> または <xref:System.Data.Linq.EntityRef%601> を使用していない場合、かつ、逆方向の参照が存在する場合は、ユーザーが、リレーションシップが更新されるときに前方参照と一致するようにする必要があります。  
  
 要求される参照と対応する外部キーの両方を更新する場合は、両者が一致する必要があります。 <xref:System.InvalidOperationException> を呼び出したときに 2 つが同期しない場合は、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 例外がスローされます。 外部キー値を変更するだけで、基になる行を更新することはできますが、オブジェクト グラフの接続と、リレーションシップの双方向の一貫性を保持するには、参照を変更する必要があります。  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [挿入、更新、および削除の各操作](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
