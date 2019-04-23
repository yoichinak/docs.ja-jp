---
title: '方法: 印刷キューのサブセットを列挙する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: adcfff0196bd0430ec1ae563fbd5489062de11f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217186"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>方法: 印刷キューのサブセットを列挙する
プリンターの全社的なセットを管理する情報技術 (IT) プロフェッショナルが直面する一般的な状況では、特定の特性を持つプリンターの一覧を生成します。 この機能によって提供されます、<xref:System.Printing.PrintServer.GetPrintQueues%2A>のメソッド、<xref:System.Printing.PrintServer>オブジェクトと<xref:System.Printing.EnumeratedPrintQueueTypes>列挙体。  
  
## <a name="example"></a>例  
 次の例では、コードは一覧を取得すると印刷キューの特性を指定するフラグの配列を作成して開始します。 この例がローカル プリント サーバーにインストールされ、共有、印刷キューを探していること。 <xref:System.Printing.EnumeratedPrintQueueTypes>列挙体は、その他の多くの可能性を提供します。  
  
 このコードを作成し、<xref:System.Printing.LocalPrintServer>オブジェクトから派生したクラス<xref:System.Printing.PrintServer>します。 ローカル プリント サーバーは、アプリケーションが実行されているコンピューターです。  
  
 最後の重要な手順は、先の配列を渡すには、<xref:System.Printing.PrintServer.GetPrintQueues%2A>メソッド。  
  
 最後に、結果がユーザーに表示されます。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 で、この例を拡張する可能性があります、`foreach`ループの各印刷キューをステップ実行をさらに実行するスクリーン処理します。 たとえば、する可能性があります画面がループの呼び出しによって、両面印刷をサポートしていないプリンターを各印刷キューの<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>メソッドと二重化の有無、返される値をテストします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
- [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)
