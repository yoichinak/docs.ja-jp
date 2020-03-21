---
title: '方法 : プリンターのステータスをリモート操作で調査する'
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
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187034"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>方法 : プリンターのステータスをリモート操作で調査する
中企業および大企業では、任意の時点において、紙詰まりや用紙切れなどの問題が発生したために動作していないプリンターが複数存在する場合があります。 Microsoft .NET Framework の API で公開される豊富なプリンター プロパティのセットは、プリンターの状態を迅速に調査するための手段を提供します。  
  
## <a name="example"></a>例  
 このようなユーティリティを作成する主な手順は次のとおりです。  
  
1. プリント サーバーの一覧を取得します。  
  
2. サーバーをループして、印刷キューを照会します。  
  
3. サーバー ループの各パス内で、すべてのサーバーのキューをループして、キューが現在動作していないことを示している各プロパティを読み取ります。  
  
 以下のコードは、一連のスニペットを示しています。 この例では、説明を簡単にするために、CRLF で区切られたプリント サーバー リストがあることを想定しています。 変数`fileOfPrintServers`はこのファイルの<xref:System.IO.StreamReader>オブジェクトです。 各サーバー名は独自の行にあるため、 の<xref:System.IO.StreamReader.ReadLine%2A>呼び出しは、次のサーバーの名前<xref:System.IO.StreamReader>を取得し、's カーソルを次の行の先頭に移動します。  
  
 このコードは、外部ループ内で最新<xref:System.Printing.PrintServer>のプリント サーバーのオブジェクトを作成し、アプリケーションがサーバーに対する管理者権限を持つことを指定します。  
  
> [!NOTE]
> サーバーが多数ある場合は、必要なプロパティだけを初期化する<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>コンストラクターを使用してパフォーマンスを向上させることができます。  
  
 次に、<xref:System.Printing.PrintServer.GetPrintQueues%2A>サーバーのすべてのキューのコレクションを作成し、それらのキューをループ処理します。 この内側のループは分岐構造になっており、プリンターの状態を確認する 2 つの方法に対応しています。  
  
- 型<xref:System.Printing.PrintQueue.QueueStatus%2A><xref:System.Printing.PrintQueueStatus>のプロパティのフラグを読み取ることができます。  
  
- などの関連するプロパティ<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>を読み取ることができます。 <xref:System.Printing.PrintQueue.IsPaperJammed%2A>  
  
 この例では、両方のメソッドを示しているため、ユーザーは以前にどのメソッドを使用するかを確認し、プロパティのフラグを使用する場合は "y"<xref:System.Printing.PrintQueue.QueueStatus%2A>で応答しました。 2 つの方法の詳細については、以下を参照してください。  
  
 最後に、結果がユーザーに表示されます。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 プロパティのフラグを使用してプリンタの状態<xref:System.Printing.PrintQueue.QueueStatus%2A>を確認するには、関連する各フラグをチェックして、設定されているかどうかを確認します。 1 ビットがビット フラグ セットで設定されているかどうかを確認するには、通常、フラグ セットを 1 つのオペランドとし、フラグ自体をもう 1 つのオペランドとして、論理 AND 演算を行います。 フラグ自体には 1 ビットのみが設定されているため、論理 AND の結果は、その同じビットが上限となります。 それが該当するかどうかを確認するには、論理 AND の結果とフラグ自体を比較します。 詳細については、「 [&](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)」を参照してください<xref:System.FlagsAttribute> <xref:System.Printing.PrintQueueStatus>  
  
 次のコードでは、ビットが設定されている属性ごとに、ユーザーに表示される最終レポートに警告を追加します  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 各プロパティを使用してプリンターの状態を確認するには、各プロパティを読み取り、プロパティが `true` の場合にユーザーに表示される最終レポートに警告を追加するだけです  (コードの最後で呼び出している **ReportAvailabilityAtThisTime** メソッドについては以下で説明します)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** メソッドは、現在の時刻にキューが使用可能かどうかを確認する必要がある場合に備えて作成されたものです。  
  
 メソッドは、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>プロパティと<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティが等しい場合は何も行いません。その場合、プリンタは常に利用可能であるためです。 異なる場合、メソッドは現在の時刻を取得し、その後<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>、および<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティは<xref:System.Int32>オブジェクトではなく<xref:System.DateTime>、午前 0 時以降の分を表すため、午前 0 時を過ぎて合計分に変換する必要があります。 最後に、このメソッドは、現在の時刻が、開始時刻と終了時刻の間にあるかどうかを確認します。  
  
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
- [&演算子 (C# リファレンス)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
