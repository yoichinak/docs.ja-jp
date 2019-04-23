---
title: '方法: データベースに変更内容を送信する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 222ce575d9e977cc8b68862385b4a1b147c6394a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326386"
---
# <a name="how-to-submit-changes-to-the-database"></a>方法: データベースに変更内容を送信する
オブジェクトに加えた変更は、その数にかかわらず、メモリ内のレプリカに対してのみ反映されています。 データベースの実際のデータは変更されていません。 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の <xref:System.Data.Linq.DataContext> を明示的に呼び出すまでは、変更内容はサーバーに送信されません。  
  
 この呼び出しを行うと、<xref:System.Data.Linq.DataContext> は、変更内容を、同等の SQL コマンドに変換します。 これらのアクションをオーバーライドする独自のカスタム ロジックを使用することができますが、送信の順序のサービスによって統制されます、<xref:System.Data.Linq.DataContext>と呼ばれる、*変更プロセッサ*します。 イベントの順序は次のとおりです。  
  
1. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すと、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、一連の既知のオブジェクトをチェックして、新しいインスタンスがアタッチされているかどうかを判断します。 その場合、それらの新しいインスタンスが、一連の追跡対象オブジェクトに追加されます。  
  
2. 保留中の変更があるすべてのオブジェクトが、互いの依存関係に基づいて、オブジェクトのシーケンスに配置されます。 他のオブジェクトに依存して変更内容が決まるオブジェクトは、その依存対象の後でシーケンスに配置されます。  
  
3. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、実際の変更を送信する直前に、一連の各コマンドをカプセル化するトランザクションを開始します。  
  
4. オブジェクトに対する変更内容が 1 つずつ SQL コマンドに変換され、サーバーに送信されます。  
  
 この時点で、データベースによってエラーが検出された場合、送信処理は中断され、例外が発生します。 データベースに加えた変更はすべてロールバックされ、送信を行わなかった場合と同じ状態になります。 この時点でも、<xref:System.Data.Linq.DataContext> には、すべての変更内容の記録がそのまま残っています。 したがって、次のコード例のように、問題を修正したうえで <xref:System.Data.Linq.DataContext.SubmitChanges%2A> を再度呼び出すことができます。  
  
## <a name="example"></a>例  
 一連の送信処理のトランザクションが正常に完了した場合、<xref:System.Data.Linq.DataContext> は、変更追跡情報を無視して、オブジェクトに対する変更を受け入れます。  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [方法: 検出および送信の競合を解決します。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [方法: 変更の競合を管理します。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [データの変更と変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
