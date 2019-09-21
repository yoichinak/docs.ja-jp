---
title: '方法: PrintTickets を検証およびマージする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918344"
---
# <a name="how-to-validate-and-merge-printtickets"></a>方法: PrintTickets を検証およびマージする
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [印刷スキーマ](https://go.microsoft.com/fwlink/?LinkId=186397)には、柔軟で拡張<xref:System.Printing.PrintCapabilities>可能<xref:System.Printing.PrintTicket>な要素と要素が含まれています。 前者は印刷デバイスの機能を示しています。後者では、デバイスが特定の順序のドキュメント、個々のドキュメント、または個々のページに対してこれらの機能をどのように使用するかを指定します。  
  
 印刷をサポートするアプリケーションの一般的なタスクシーケンスは、次のとおりです。  
  
1. プリンターの機能を確認します。  
  
2. これらの<xref:System.Printing.PrintTicket>機能を使用するようにを構成します。  
  
3. を<xref:System.Printing.PrintTicket>検証します。  
  
 この記事では、これを行う方法について説明します。  
  
## <a name="example"></a>例  
 次の簡単な例では、プリンターが両面印刷をサポートしているかどうかのみを知りたいと考えています。 主な手順は次のとおりです。  
  
1. メソッド<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>を<xref:System.Printing.PrintCapabilities>使用してオブジェクトを取得します。  
  
2. 必要な機能があるかどうかをテストします。 次の例では、 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> <xref:System.Printing.PrintCapabilities>オブジェクトのプロパティをテストして、用紙の両面に印刷機能があり、シートの横に "ページめくり" が付いていることを確認します。 は<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>コレクションであるため、の`Contains` <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>メソッドを使用します。  
  
    > [!NOTE]
    > この手順は、厳密には必要ありません。 以下で使用する<xref:System.Printing.PrintTicket> メソッドは、内の各要求をプリンターの機能と照合してチェックします。<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 要求された機能がプリンターでサポートされていない場合、プリンタードライバーは、 <xref:System.Printing.PrintTicket>メソッドによって返されたの代替要求を置き換えます。  
  
3. プリンターが両面印刷をサポートしている場合は<xref:System.Printing.PrintTicket> 、このサンプルコードによって、二重化を求めるが作成されます。 ただし、アプリケーションでは、 <xref:System.Printing.PrintTicket>要素で使用可能なすべてのプリンター設定が指定されていません。 これは、プログラマとプログラム時間の両方で無駄になります。 代わりに、この<xref:System.Printing.PrintTicket>コードでは二重の要求のみを設定し、これを既存の、完全に構成<xref:System.Printing.PrintTicket>および検証された (この場合は<xref:System.Printing.PrintTicket>ユーザーの既定値) とマージします。  
  
4. したがって、このサンプルで<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>は、メソッドを呼び出して、ユーザー <xref:System.Printing.PrintTicket>の既定値<xref:System.Printing.PrintTicket>を使用して、新しいを最小限にします。 これにより<xref:System.Printing.ValidationResult> 、新しい<xref:System.Printing.PrintTicket>をプロパティの1つとして含むが返されます。  
  
5. このサンプルでは、新しい<xref:System.Printing.PrintTicket>要求が二重になっていることをテストします。 存在する場合は、サンプルによってユーザーの既定の印刷チケットが新しく作成されます。 上記の手順 2 `false`. を省略した場合、プリンターでは、長辺に沿った両面印刷がサポートされていないと、テストの結果としてが発生します。 (上記のメモを参照してください)。  
  
6. 最後の重要な手順は、 <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue.Commit%2A>メソッドを使用して、 <xref:System.Printing.PrintQueue>のプロパティに対する変更をコミットすることです。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 この例を簡単にテストできるように、この例の残りの部分を以下に示します。 プロジェクトと名前空間を作成し、この記事の両方のコードスニペットを名前空間ブロックに貼り付けます。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
- [スキーマの印刷](https://go.microsoft.com/fwlink/?LinkId=186397)
