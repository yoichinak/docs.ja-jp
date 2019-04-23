---
title: '方法: 現在、印刷ジョブが印刷可能であるかどうかを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: 7eed5400744f1010cbf52dc8d3b3d0bc24aa4371
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326867"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>方法: 現在、印刷ジョブが印刷可能であるかどうかを検出する
印刷キューは常に使用できません、1 日 24 時間です。 特定の時間帯で使用できないように設定可能な開始と終了時のプロパティがあります。 たとえば、この機能は、特定の部門午後 5 時以降後に排他的に使用するプリンターを予約するは使用できます。 その部門は、別のキュー サービスの他の部門よりプリンターを使用して、必要があります。 他の部署のキューは午後 5 時以降に設定されます、する部門用のキューに設定できるときに常に利用できます。  
  
 さらに、印刷ジョブ自体は、指定した期間内のみで印刷できるように設定できます。  
  
 <xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>で公開されているクラス、 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework の現在のところ、特定のキューで指定した印刷ジョブが印刷できるかどうかをリモートで確認するため手段を提供します。  
  
## <a name="example"></a>例  
 次の例では、印刷ジョブに関する問題を診断できるサンプルを示します。  
  
 この種類の関数の 2 つの主要な手順は次があります。  
  
1. 読み取り、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintQueue>現在の時刻がそれらの間がかどうかを判断します。  
  
2. 読み取り、<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>と<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>のプロパティ、<xref:System.Printing.PrintSystemJobInfo>現在の時刻がそれらの間がかどうかを判断します。  
  
 ただしこれらのプロパティがないという事実から<xref:System.DateTime>オブジェクト。 これらのプロパティは<xref:System.Int32>午前 0 時以降の分単位の数として 1 日の時間を表すオブジェクト。 さらに、this は午前 0 時では、現在のタイム ゾーンが午前 0 時 UTC (世界協定時刻) です。  
  
 最初のコード例は、静的メソッドを表示します。 **ReportQueueAndJobAvailability**、渡された、<xref:System.Printing.PrintSystemJobInfo>ジョブが現在の時刻に印刷できるかどうかを判断するヘルパー メソッドを呼び出すと、そうでない場合に印刷できる場合。 注意を<xref:System.Printing.PrintQueue>は、メソッドに渡されません。 これは、ため、<xref:System.Printing.PrintSystemJobInfo>でキューへの参照が含まれています、<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>プロパティ。  
  
 下位の方法には、オーバー ロードされた**ReportAvailabilityAtThisTime**いずれかのメソッド、<xref:System.Printing.PrintQueue>または<xref:System.Printing.PrintSystemJobInfo>をパラメーターとして。 **また**します。 以下は、これらのメソッドのすべてについて説明します。  
  
 **ReportQueueAndJobAvailability**かどうか、キューまたは印刷ジョブが使用可能なこの時点で確認するメソッドを開始します。 それらのいずれかが使用可能な場合は、それから、かどうかを使用できないキュー。 利用できないこのファクト テーブルとすると、キューが使用可能になるもう一度時間、メソッドが報告します。 ジョブを確認し、次回を報告が利用できない場合にまたがる場合に印刷できる場合。 最後に、ジョブが印刷できる最も早い時刻を報告します。 これは、次の 2 倍のそれ以降。  
  
-   印刷キューが次に利用できる時刻。  
  
-   印刷ジョブが次に利用可能な時間です。  
  
 、1 日の時間を報告するときに、<xref:System.DateTime.ToShortTimeString%2A>年、月、および日の出力からこのメソッドを抑制しますので、メソッドが呼び出されます。 特定の年、月、または日に印刷キューまたは印刷ジョブのいずれかの可用性を制限することはできません。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 2 つのオーバー ロード、 **ReportAvailabilityAtThisTime**メソッドにのみ、それらに渡された型を除いて同一ですが、<xref:System.Printing.PrintQueue>バージョンを次に示します。  
  
> [!NOTE]
>  メソッドの型を除いて同一ですが、サンプルはジェネリック メソッドを作成していない理由の質問を発生させます**ReportAvailabilityAtThisTime\<T >** します。 理由は、このようなメソッドを持つクラスに制限する必要がある、**に実行**と**UntilTimeOfDay**メソッドを呼び出すと、プロパティがジェネリック メソッドのみに制限できる、1 つのクラスと両方に共通する唯一のクラス<xref:System.Printing.PrintQueue>と<xref:System.Printing.PrintSystemJobInfo>ツリーは、継承の<xref:System.Printing.PrintSystemObject>がこのようなプロパティがありません。  
  
 **ReportAvailabilityAtThisTime**メソッド (次のコード例で表示) の初期化ではまず、 <xref:System.Boolean> sentinel 変数`true`します。 リセットされます`false`キューが使用できない場合は、します。  
  
 メソッドを次に、かどうかをチェック、開始し、"until"時間は同じです。 メソッドが返されには、キューが使用可能な常にいる場合は、`true`します。  
  
 メソッドが静的なを使用して、キューが使用できない場合、すべての時間、<xref:System.DateTime.UtcNow%2A>として現在の時刻を取得するプロパティを<xref:System.DateTime>オブジェクト。 (ために、現地時刻は必要ありません、<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティが UTC 時刻では自体です)。  
  
 ただし、これら 2 つのプロパティは<xref:System.DateTime>オブジェクト。 <xref:System.Int32>分後に UTC 深夜の数と時間を表す。 変換することがしなくて済むよう、<xref:System.DateTime>分の深夜の後にオブジェクト。 インストールが完了したら、メソッドは"now"かどうかを確認するキューの開始の間、および"until"回、false の場合は"now"sentinel が 2 つの時刻の間ではないと、sentinel を返すセットは、単純にチェックします。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **また**メソッド (次のコード例で表示) では、説明が簡単なために、Microsoft .NET Framework で導入されたすべてのメソッドは使用しません。 メソッドには 2 段階の変換タスク: これを現地時刻に変換しなければならないとその分の後に、午前 0 時を表す整数値を取得し、人間が判読できる時間に変換する必要があります。 これを行う、最初に作成、 <xref:System.DateTime> UTC と、しを使用して午前 0 時に設定されているオブジェクト、<xref:System.DateTime.AddMinutes%2A>メソッドに渡された分数を加算するメソッド。 返されます。 新しい<xref:System.DateTime>メソッドに渡された元の時刻を表現します。 <xref:System.DateTime.ToLocalTime%2A>メソッドからこの現地時刻に変換します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
