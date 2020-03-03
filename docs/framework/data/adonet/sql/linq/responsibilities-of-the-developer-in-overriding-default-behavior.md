---
title: 既定の動作をオーバーライドするときの開発者の責任
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4bfb108e81f64ea368c6bcc846553eb1af5c23b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792728"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>既定の動作をオーバーライドするときの開発者の責任
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]では次の要件は適用されませんが、これらの要件が満たされていない場合、動作は定義されていません。  
  
- オーバーライドするメソッドでは、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> も <xref:System.Data.Linq.Table%601.Attach%2A> も呼び出さないでください。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オーバーライドメソッドでこれらのメソッドが呼び出されると、例外がスローされます。  
  
- オーバーライド メソッドは、トランザクションの開始、コミット、および中断には使用できません。 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 操作はトランザクションの下で実行されます。 入れ子になった内側のトランザクションは、外側のトランザクションと干渉する可能性があります。 読み込みのオーバーライド メソッドでは、<xref:System.Transactions.Transaction> 内で実行されている操作でないことを確認した場合にのみ、トランザクションを開始できます。  
  
- オーバーライド メソッドでは、該当するオプティミスティック コンカレンシーの対応付けに従うことが望まれます。 オプティミスティック コンカレンシーの競合が発生したときに、オーバーライド メソッドは <xref:System.Data.Linq.ChangeConflictException> をスローすることが望まれています。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.DataContext.SubmitChanges%2A> で<xref:System.Data.Linq.DataContext.SubmitChanges%2A>指定されたオプションを正しく処理できるように、この例外をキャッチします。  
  
- 作成 (`Insert`) および `Update` のオーバーライド メソッドでは、操作が正常に完了した場合、データベースによって生成された列の値を、対応するオブジェクト メンバーに反映することが望まれます。  
  
     たとえば、が id `Order.OrderID`列にマップされている場合 (プライマリキーの自動*増分*)、オーバーライドメソッドは`InsertOrder()` `Order.OrderID`データベースで生成された id を取得し、メンバーをその id に設定する必要があります。 同様に、タイムスタンプ型のメンバーは、データベースが生成したタイムスタンプ値に更新して、更新後のオブジェクトの一貫性を維持する必要があります。 データベースが生成した値を反映しなかった場合、データベースと、<xref:System.Data.Linq.DataContext> が追跡するオブジェクトとの間で、矛盾が生じる可能性があります。  
  
- 正しい動的 API を呼び出す必要があります。 たとえば、更新のオーバーライド メソッドで呼び出すことができるのは <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> のみです。 呼び出した動的メソッドが対象の操作に一致するかどうかについて、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、検出や検査は行いません。 適合しないメソッドを呼び出した場合 (たとえば、更新するオブジェクトについて <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> を呼び出した場合)、結果は未定義です。  
  
- オーバーライド メソッドでは、決められた操作を実行することが望まれます。 Eager Loading、遅延読み込み、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] など、<xref:System.Data.Linq.DataContext.SubmitChanges%2A> 操作のセマンティクスでは、決められたサービスをオーバーライド メソッドで提供する必要があります。 たとえば、読み込みのオーバーライドで、データベースの内容をチェックせずに空のコレクションを返した場合、データの矛盾につながる可能性があります。  
  
## <a name="see-also"></a>関連項目

- [挿入、更新、および削除の各操作のカスタマイズ](customizing-insert-update-and-delete-operations.md)
