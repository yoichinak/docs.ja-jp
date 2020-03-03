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
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947811"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>方法: 現在、印刷ジョブが印刷可能であるかどうかを検出する
印刷キューは、1日24時間利用できるとは限りません。 開始時刻と終了時刻のプロパティがあり、特定の時間帯に使用できないように設定できます。 この機能を使用すると、たとえば、午後5時以降に特定の部門を排他的に使用するようにプリンターを予約することができます。 この部門では、他の部署が使用するものとは異なるキューを使用します。 他の部門のキューは、午後5時から使用不可になるように設定されますが、優先される部署のキューは常に使用可能になるように設定できます。  
  
 さらに、印刷ジョブ自体は、指定された期間内にのみ印刷できるように設定できます。  
  
 Microsoft .NET <xref:System.Printing.PrintQueue> Framework <xref:System.Printing.PrintSystemJobInfo>の api で公開されているクラスとクラスは、特定の印刷ジョブを現在の時刻に特定のキューに出力できるかどうかをリモートで確認する手段を提供します。  
  
## <a name="example"></a>例  
 次の例は、印刷ジョブに関する問題を診断できるサンプルです。  
  
 この種の関数には、次の2つの主要な手順があります。  
  
1. のプロパティと<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティを読み取って、現在の時刻が両者の間にあるかどうかを確認します。<xref:System.Printing.PrintQueue> <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
  
2. のプロパティと<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>プロパティを読み取って、現在の時刻が両者の間にあるかどうかを確認します。<xref:System.Printing.PrintSystemJobInfo> <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>  
  
 ただし、これらのプロパティがオブジェクトではない<xref:System.DateTime>という事実から、複雑な問題が発生します。 代わりに、午前<xref:System.Int32> 0 時からの時間を表すオブジェクトです。 さらに、現在のタイムゾーンでは午前0時ではなく、UTC (世界協定時刻) になります。  
  
 1つ目のコード例では、に渡された静的なメソッド**reportqueueandjobavailability**を示しています。このメソッドは、 <xref:System.Printing.PrintSystemJobInfo>ジョブを現在の時刻に印刷できるかどうかを判断するために、また、印刷可能な場合にはそのジョブを印刷できるかどうかを判断するためにヘルパーメソッドを <xref:System.Printing.PrintQueue>がメソッドに渡されないことに注意してください。 これは、に<xref:System.Printing.PrintSystemJobInfo> <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>プロパティのキューへの参照が含まれているためです。  
  
 下位メソッドに<xref:System.Printing.PrintQueue>は、パラメーターとしてまたはを<xref:System.Printing.PrintSystemJobInfo>受け取ることができる、オーバーロードされた**ReportAvailabilityAtThisTime**メソッドが含まれています。 TimeConverter もあります。 **ConvertToLocalHumanReadableTime**です。 これらのすべての方法については、以下で説明します。  
  
 **Reportqueueandjobavailability**メソッドは、キューまたは印刷ジョブが現時点で使用できないかどうかを確認することから始まります。 これらのいずれかが使用できない場合は、キューが使用できないかどうかを確認します。 使用できない場合は、メソッドによって、このファクトと、キューが再び使用可能になるまでの時間が報告されます。 次にジョブを確認し、使用できない場合は、次に印刷できる時間帯を報告します。 最後に、このメソッドは、ジョブが印刷できる最も早い時刻を報告します。 これは、次の2回の後に発生します。  
  
- 印刷キューが次に使用可能になる時刻。  
  
- 印刷ジョブが次に使用可能になる時刻。  
  
 時間をレポートする場合、 <xref:System.DateTime.ToShortTimeString%2A>このメソッドは、出力からの年、月、および日を抑制するため、メソッドも呼び出されます。 印刷キューまたは印刷ジョブの可用性を、特定の年、月、または日に制限することはできません。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 **ReportAvailabilityAtThisTime**メソッドの2つのオーバーロードは、渡される型を除いて同じです。そのため<xref:System.Printing.PrintQueue> 、次のバージョンのみが表示されます。  
  
> [!NOTE]
> メソッドが同じであるという事実は、型を除いて、このサンプルではジェネリックメソッド **\<ReportAvailabilityAtThisTime T >** が作成されないという問題が発生します。 その理由は、このようなメソッドは、メソッドが呼び出す**starttimeofday**プロパティと1対1の**timeofday**プロパティを持つクラスに制限する必要がありますが、ジェネリックメソッドは、単一のクラスにのみ制限でき、両方に共通する唯一のクラスに限定されます。継承ツリーのと<xref:System.Printing.PrintSystemJobInfo>には<xref:System.Printing.PrintSystemObject> 、そのようなプロパティはありません。 <xref:System.Printing.PrintQueue>  
  
 **ReportAvailabilityAtThisTime**メソッド (下のコード例を参照) は、 <xref:System.Boolean> sentinel 変数をに初期化する`true`ことから始まります。 キューが使用できない`false`場合は、にリセットされます。  
  
 次に、メソッドは、start と "until" の時刻が同じかどうかを確認します。 これらの値がの場合、キューは常に使用可能な`true`ので、メソッドはを返します。  
  
 キューが常に利用できない場合、メソッドは静的<xref:System.DateTime.UtcNow%2A>プロパティを使用し<xref:System.DateTime>て現在の時刻をオブジェクトとして取得します。 (プロパティ<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>と<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>プロパティは UTC 時刻であるため、現地時間は必要ありません)。  
  
 ただし、これら2つのプロパティ<xref:System.DateTime>はオブジェクトではありません。 これらの<xref:System.Int32>値は、時刻を UTC から午前0時までの分数として表現しています。 そのため、 <xref:System.DateTime>オブジェクトを午前0時から分単位に変換する必要があります。 この処理が完了すると、メソッドは単に "now" がキューの先頭と "until" の間にあるかどうかを確認し、"now" が2回の間にない場合は sentinel を false に設定し、sentinel を返します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter**メソッド (下記のコード例を参照) は Microsoft .NET Framework で導入されたメソッドを使用しないため、説明は簡単です。 メソッドには、2回の変換タスクがあります。これは、午前0時から午前0時を表す整数値を取得し、それを人間が判読できる時刻に変換し、現地時刻に変換する必要があります。 これを実現するには、 <xref:System.DateTime>最初に UTC の午前0時に設定された<xref:System.DateTime.AddMinutes%2A>オブジェクトを作成し、メソッドを使用して、メソッドに渡された分を追加します。 これは、メソッド<xref:System.DateTime>に渡された元の時刻を表す新しいを返します。 次<xref:System.DateTime.ToLocalTime%2A>に、メソッドはこれを現地時刻に変換します。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
