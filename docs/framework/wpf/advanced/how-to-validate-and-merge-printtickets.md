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
ms.openlocfilehash: be8b299c99515394bc676cfd7a715cb82ac4d58c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301153"
---
# <a name="how-to-validate-and-merge-printtickets"></a>方法: PrintTickets を検証およびマージする
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [印刷スキーマ](https://go.microsoft.com/fwlink/?LinkId=186397)柔軟性と拡張性が含まれています<xref:System.Printing.PrintCapabilities>と<xref:System.Printing.PrintTicket>要素。 印刷デバイスの機能を列記前者と後者の場合、デバイスが特定のシーケンスのドキュメント、個々 のドキュメント、または個々 のページに対してこれらの機能を使用する方法を指定します。  
  
 印刷をサポートするアプリケーションのタスクの一般的なシーケンスであるようです。  
  
1. プリンターの機能を決定します。  
  
2. 構成、<xref:System.Printing.PrintTicket>それらの機能を使用します。  
  
3. 検証、<xref:System.Printing.PrintTicket>します。  
  
 この記事では、これを行う方法を示します。  
  
## <a name="example"></a>例  
 次の単純な例でプリンターが両面印刷をサポートするかどうかのみが必要な両面印刷します。 主要な手順は次のとおりです。  
  
1. 取得、<xref:System.Printing.PrintCapabilities>オブジェクトを<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>メソッド。  
  
2. 必要な機能の有無をテストします。 次の例では、テスト、<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>のプロパティ、<xref:System.Printing.PrintCapabilities>用紙の長辺に沿って「ページに」用紙の両面に印刷の機能が存在するオブジェクトします。 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>はコレクションを使用して、`Contains`メソッドの<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>。  
  
    > [!NOTE]
    >  この手順では、厳密には必要ありません。 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>以下で使用方法は、各要求を確認するのには、<xref:System.Printing.PrintTicket>プリンターの機能を比較します。 プリンター ドライバーがで別の要求を置き換えて、要求された機能がプリンターでサポートされていない場合、<xref:System.Printing.PrintTicket>メソッドによって返されます。  
  
3. サンプル コードを作成、プリンターが両面印刷をサポートする場合、<xref:System.Printing.PrintTicket>二重求められます。 アプリケーションでは設定で使用可能なすべての可能なプリンターが指定されていない、<xref:System.Printing.PrintTicket>要素。 プログラマとプログラムの時間の無駄なことです。 代わりに、コードは二重化の要求のみを設定し、これをマージ<xref:System.Printing.PrintTicket>既存の完全に構成され、検証、 <xref:System.Printing.PrintTicket>、ここでは、ユーザーの既定<xref:System.Printing.PrintTicket>します。  
  
4. したがって、サンプルを呼び出す、<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>メソッドを新しいマージ最小限、 <xref:System.Printing.PrintTicket> 、既定値は、ユーザーの<xref:System.Printing.PrintTicket>します。 返されます、<xref:System.Printing.ValidationResult>を含む新しい<xref:System.Printing.PrintTicket>としてそのプロパティのいずれか。  
  
5. サンプルをテストし、新しい<xref:System.Printing.PrintTicket>二重化を要求します。 場合は、サンプルを使用すると、ユーザーの新しい既定の印刷チケット。 上記の手順 2 を省略したかどうかと、プリンターが両面印刷、長辺に沿ってをサポートしていませんでしたし、テスト結果となります`false`します。 (上記の注を参照してください)。  
  
6. 最後の重要な手順に変更をコミットするには、<xref:System.Printing.PrintQueue.UserPrintTicket%2A>のプロパティ、<xref:System.Printing.PrintQueue>で、<xref:System.Printing.PrintQueue.Commit%2A>メソッド。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 すぐにこの例をテストするように、残りの部分は次に示します。 プロジェクトと名前空間を作成し、この記事では、名前空間ブロックに両方のコード スニペットを貼り付けます。  
  
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
- [印刷スキーマ](https://go.microsoft.com/fwlink/?LinkId=186397)
