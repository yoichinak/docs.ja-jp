---
title: '方法: プリンターのステータスをリモート操作で調査する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: 6eba3c5edd9095a25c0a387a3b37f68e3799d1c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359706"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>方法: プリンターのステータスをリモート操作で調査する
中企業および大企業では、任意の時点において、紙詰まりや用紙切れなどの問題が発生したために動作していないプリンターが複数存在する場合があります。 プリンターのプロパティで公開されている一連の豊富な[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft .NET Framework のプリンターの状態を迅速に調査を実行する手段を提供します。  
  
## <a name="example"></a>例  
 このようなユーティリティを作成する主な手順は次のとおりです。  
  
1.  プリント サーバーの一覧を取得します。  
  
2.  サーバーをループして、印刷キューを照会します。  
  
3.  サーバー ループの各パス内で、すべてのサーバーのキューをループして、キューが現在動作していないことを示している各プロパティを読み取ります。  
  
 以下のコードは、一連のスニペットを示しています。 この例では、説明を簡単にするために、CRLF で区切られたプリント サーバー リストがあることを想定しています。 変数`fileOfPrintServers`は、<xref:System.IO.StreamReader>このファイルのオブジェクト。 すべての呼び出しのため、各サーバー名は、独自の行では、<xref:System.IO.StreamReader.ReadLine%2A>次のサーバーの名前を取得し、移動、<xref:System.IO.StreamReader>の次の行の先頭にカーソル。  
  
 外側のループ内でコードを作成、<xref:System.Printing.PrintServer>最新のプリント サーバーのオブジェクトし、アプリケーションがサーバーに管理権限を持っていることを指定します。  
  
> [!NOTE]
>  使用してパフォーマンスを向上させることができます、多数のサーバーがある場合、<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>のみ必要があるプロパティを初期化するコンス トラクター。  
  
 使用して<xref:System.Printing.PrintServer.GetPrintQueues%2A>のキューに配置してループを開始し、サーバーのすべてのコレクションを作成します。 この内側のループは分岐構造になっており、プリンターの状態を確認する 2 つの方法に対応しています。  
  
-   フラグを読み取ることができます、<xref:System.Printing.PrintQueue.QueueStatus%2A>型のプロパティ<xref:System.Printing.PrintQueueStatus>します。  
  
-   など、各関連プロパティを読み取ることができます<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>、および<xref:System.Printing.PrintQueue.IsPaperJammed%2A>します。  
  
 この例では、両方の方法、ユーザーが以前に使用する方法に関して入力を求めし、求めのフラグを使用する場合は、"y"で応答したため、<xref:System.Printing.PrintQueue.QueueStatus%2A>プロパティ。 2 つの方法の詳細については、以下を参照してください。  
  
 最後に、結果がユーザーに表示されます。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 フラグを使用してプリンターの状態を確認する、<xref:System.Printing.PrintQueue.QueueStatus%2A>プロパティに設定されているかどうかを参照してください。 各関連フラグを確認します。 1 ビットがビット フラグ セットで設定されているかどうかを確認するには、通常、フラグ セットを 1 つのオペランドとし、フラグ自体をもう 1 つのオペランドとして、論理 AND 演算を行います。 フラグ自体には 1 ビットのみが設定されているため、論理 AND の結果は、その同じビットが上限となります。 それが該当するかどうかを確認するには、論理 AND の結果とフラグ自体を比較します。 詳細については、<xref:System.Printing.PrintQueueStatus>、 [& 演算子 (C#リファレンス)](~/docs/csharp/language-reference/operators/and-operator.md)、および<xref:System.FlagsAttribute>を参照してください。  
  
 次のコードでは、ビットが設定されている属性ごとに、ユーザーに表示される最終レポートに警告を追加します  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 各プロパティを使用してプリンターの状態を確認するには、各プロパティを読み取り、プロパティが `true` の場合にユーザーに表示される最終レポートに警告を追加するだけです  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** メソッドは、現在の時刻にキューが使用可能かどうかを確認する必要がある場合に備えて作成されたものです。  
  
 メソッドは何も場合、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プリンターは常に使用できる、そうであるために、プロパティが等しい。 メソッドが、ため、合計分数に変換するには、現在の時刻を取得するが異なる場合、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティは、<xref:System.Int32>いない深夜後分を表す<xref:System.DateTime>オブジェクト。 最後に、このメソッドは、現在の時刻が、開始時刻と終了時刻の間にあるかどうかを確認します。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [& 演算子 (C#リファレンス)](~/docs/csharp/language-reference/operators/and-operator.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
