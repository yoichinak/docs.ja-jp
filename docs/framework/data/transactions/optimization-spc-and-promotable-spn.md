---
title: 単一フェーズ コミットおよび昇格可能単一フェーズ通知を使用した最適化
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 73340f5f65de1d743e046cf669258ab5f6c66298
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371204"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>単一フェーズ コミットおよび昇格可能単一フェーズ通知を使用した最適化

ここでは、パフォーマンスを最適化するために <xref:System.Transactions> インフラストラクチャに用意されているメカニズムについて説明します。

## <a name="promotable-single-phase-enlistment"></a>PSPE (Promotable Single Phase Enlistment)

<xref:System.Transactions> インフラストラクチャは、単一の永続性リソースまたは複数の揮発性リソースを含む単一のアプリケーション ドメイン内のトランザクションを管理します。 <xref:System.Transactions> インフラストラクチャは、アプリケーション内ドメインの呼び出しのみを使用するため、最良のスループットおよびパフォーマンスを得られます。

ただし、トランザクションが同じコンピューター上の別のアプリケーション ドメインにある別のオブジェクト (プロセスやコンピューターの境界にまたがるものを含む) に供給される場合や、別の永続的リソース マネージャーを参加させる場合、<xref:System.Transactions> インフラストラクチャは、MSDTC によって管理されるトランザクションを自動的にエスカレートします。 MSDTC によって管理されるトランザクションは、<xref:System.Transactions> インフラストラクチャによって管理されるトランザクションに比べて、パフォーマンスが落ちます。

パフォーマンスを最適化するため、<xref:System.Transactions> インフラストラクチャには PSPE (Promotable Single Phase Enlistment) が用意されており、異なるアプリケーション ドメイン、プロセス、またはコンピューターにある単一のリモート永続性リソースが、MSDTC トランザクションにエスカレートされることなく <xref:System.Transactions> トランザクションに参加できるようになります。 このリソース マネージャー (RM) は、必要に応じて後で分散トランザクション (または MSDTC トランザクション) にエスカレートできるトランザクションをホストおよび "所有" できます。 これにより、MSDTC の使用頻度が少なくなります。

この特別なリソース マネージャーは通常、内部に独自の非分散トランザクションを所有しており、実行時にこれらのトランザクションを分散トランザクションに変換する必要があります。 たとえば、SQL Server 2005 はこのようなリソース マネージャーです。 この場合、<xref:System.Transactions> インフラストラクチャは、トランザクションのエスカレーションが必要かどうかを監視するだけという受動的な管理役割を担います。 <xref:System.Transactions> インフラストラクチャとリソース マネージャー間の相互動作をサポートするため、リソース マネージャーは、<xref:System.Transactions.IPromotableSinglePhaseNotification> インターフェイスを実装する必要があります。

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> メソッドは、後でエスカレートできる単一の永続性リソースを参加させるのに使用されます。 このメソッドにより、必要に応じて参加リストをエスカレートできます。 参加が成功すると、RM は内部トランザクションを作成し、<xref:System.Transactions> トランザクションに関連付けます。 PSPE の参加が失敗すると、RM は代わりに <xref:System.Transactions.Transaction.EnlistDurable%2A> メソッドを使用して参加を行います。 トランザクションが既に分散トランザクションである場合や、別の RM が既に PSPE の参加を実行している場合、PSPE の参加は失敗します。

参加すると、<xref:System.Transactions> トランザクションをコミットまたは中止するクライアントからの呼び出しがリソース マネージャーでの呼び出しに変換されます。これは、それぞれ <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> メソッドまたは <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> を呼び出すことで行われます。

<xref:System.Transactions> トランザクションのエスカレーションが必要ない場合、トランザクションがコミットされると、RM が <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 通知を受信します。 次に、最初に作成された内部トランザクションがコミットされます。

<xref:System.Transactions> トランザクションのエスカレートが必要な場合 (複数の RM をサポートする場合など) は、<xref:System.Transactions> がリソース マネージャーに通知します。この通知は、<xref:System.Transactions.ITransactionPromoter.Promote%2A> インターフェイスの派生元である <xref:System.Transactions.ITransactionPromoter> インターフェイス上の <xref:System.Transactions.IPromotableSinglePhaseNotification> メソッドを呼び出すことで行われます。 次に、リソース マネージャーは、ローカル トランザクション (ログが不要) から DTC トランザクションに参加できるトランザクション オブジェクトへ、トランザクションを内部的に変換し、既に実行済みの作業に関連付けます。 トランザクションのコミットが要求されると、トランザクション マネージャーが <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 通知をリソース マネージャーに送信し、リソース マネージャーがエスカレーション中に作成される分散トランザクションをコミットします。

> [!NOTE]
> **TransactionCommitted** (エスカレートされたトランザクションで Commit が呼び出されたときに生成される) トレースには、DTC トランザクションのアクティビティ ID が含まれています。

管理エスカレーションの詳細については、[Transaction Management Escalation](../../../../docs/framework/data/transactions/transaction-management-escalation.md)を参照してください。

## <a name="transaction-management-escalation-scenario"></a>トランザクション管理エスカレーションのシナリオ

次のシナリオは、<xref:System.Data>名前空間をリソース マネージャーの "プロキシ" として使用して、分散トランザクションにエスカレートする操作を示しています。 このシナリオでは、トランザクションで呼び出されたデータベースへの <xref:System.Data><xref:System.Data>接続 (CN1) が既に存在し、アプリケーションが別の  接続 (CN2) を呼び出そうとしている場合を想定しています。 トランザクションは、完全な分散 2 フェーズ コミット トランザクションとして、DTC にエスカレートする必要があります。

このシナリオの内容

1. CN1 は、トランザクションに参加するため、<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> メソッドを呼び出します。 ここで、トランザクションはまだローカルであり、トランザクションには他に昇格可能参加リストがないため、<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 呼び出しは成功します。

2. 2 番目の接続 (CN2) が <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> を呼び出すと、関連する別の昇格可能参加リストがあるため、呼び出しが失敗します。 このため、CN2 は、DTC トランザクションを取得して、SQL に渡す必要があります。 これには、<xref:System.Transactions.TransactionInterop> クラスで提供されるメソッドの 1 つを使用して、SQL に渡すことができるトランザクションの形式を生成します。

3. <xref:System.Transactions> は、CN1 によって実装された <xref:System.Transactions.ITransactionPromoter.Promote%2A> インターフェイス上で、<xref:System.Transactions.ITransactionPromoter> メソッドを呼び出します。

4. この時点で CN1 は、SQL 2005 固有のメカニズムと <xref:System.Data> を使用して、トランザクションをエスカレートします。

5. 
  <xref:System.Transactions.ITransactionPromoter.Promote%2A> メソッドからの戻り値は、トランザクションの反映トークンを含むバイト配列です。 <xref:System.Transactions> ローカル トランザクションに組み込むことのできる DTC トランザクションを作成するのにには、この反映トークンを使用します。

6. この時点で CN2 は、<xref:System.Transactions.TransactionInterop> によるメソッドの 1 つを呼び出すことで受信したデータを使用して、SQL にトランザクションを渡すことができます。

7. ここで、両方が DTC 分散トランザクションに参加します。

## <a name="single-phase-commit-optimization"></a>単一フェーズ コミットの最適化

単一フェーズ コミット プロトコルは、すべての更新が明示的な調整なしに行われるため、実行時に、より効率的です。 この最適化を活用するには、リソースの <xref:System.Transactions.ISinglePhaseNotification> インターフェイスを使用してリソース マネージャーを実装し、<xref:System.Transactions.Transaction.EnlistDurable%2A> メソッドまたは <xref:System.Transactions.Transaction.EnlistVolatile%2A> メソッドを使用してトランザクションに参加する必要があります。 具体的には、 *EnlistmentOptions*パラメーターと等しく必要があります<xref:System.Transactions.EnlistmentOptions.None>単一フェーズ コミットが実行されることを確認します。


  <xref:System.Transactions.ISinglePhaseNotification> インターフェイスは <xref:System.Transactions.IEnlistmentNotification> インターフェイスから派生するため、RM が単一フェーズ コミットを実行できない場合でも、2 フェーズ コミット通知を受信できます。 RM が TM から <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> 通知を受信した場合は、コミットするために必要な作業を実行する必要があります。そして、それに応じて <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A> パラメーター上の <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>、<xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A>、または <xref:System.Transactions.SinglePhaseEnlistment> メソッドを呼び出すことにより、トランザクションのコミットまたはロールバックのどちらが実行されるかを、トランザクション マネージャーに通知する必要があります。 この段階で、参加リストの <xref:System.Transactions.Enlistment.Done%2A> の応答は、ReadOnly セマンティクスを意味します。 したがって、他のメソッドに加えて、<xref:System.Transactions.Enlistment.Done%2A> を応答しないでください。

1 つだけの揮発性参加リストとなしの永続参加リストが場合、揮発性参加リストが SPC 通知を受信します。 任意の揮発性参加リストと 1 つだけの永続参加リストがある場合は、揮発性参加リストは 2 pc を受信します。 完了すると、永続参加リストが SPC を受信します。

## <a name="see-also"></a>関連項目

- [トランザクションの参加要素としてのリソースの参加](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
- [単一フェースおよび複数フェーズでのトランザクションのコミット](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
