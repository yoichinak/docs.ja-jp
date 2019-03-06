---
title: '方法: XPS ファイルをプログラムにより印刷する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: c00a12000dd10ba32bd550186377547b3ef72d25
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372725"
---
# <a name="how-to-programmatically-print-xps-files"></a>方法: XPS ファイルをプログラムにより印刷する
1 つのオーバー ロードを使用することができます、<xref:System.Printing.PrintQueue.AddJob%2A>メソッドを印刷する[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]ファイルを開くことがなく、<xref:System.Windows.Controls.PrintDialog>や、原則として、任意[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]まったくです。  
  
 印刷することも[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]多くを使用してファイルを<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>と<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>のメソッド、<xref:System.Windows.Xps.XpsDocumentWriter>します。 この詳細については、「[XPS ドキュメントの印刷](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))」を参照してください。  
  
 印刷[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]を使用して、<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>または<xref:System.Windows.Controls.PrintDialog.PrintVisual%2A>のメソッド、<xref:System.Windows.Controls.PrintDialog>コントロール。 [印刷ダイアログ ボックスの呼び出し](how-to-invoke-a-print-dialog.md)に関するページをご覧ください。  
  
## <a name="example"></a>例  
 3 つのパラメーターを使用する主な手順<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッドは、次のとおりです。 詳細は、下記の例に示します。  
  
1.  プリンターが XPSDrv プリンターかどうかを確認します  (XPSDrv の詳細については、「[印刷の概要](printing-overview.md)」を参照してください)。  
  
2.  プリンターが XPSDrv プリンターでない場合は、スレッドのアパートメントをシングル スレッドに設定します。  
  
3.  プリント サーバーと印刷キューのオブジェクトをインスタンス化します。  
  
4.  ジョブ名、印刷するファイルを指定するメソッドを呼び出し、<xref:System.Boolean>プリンターが XPSDrv プリンターかどうかどうかを示すフラグします。  
  
 ディレクトリ内のすべての [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルをバッチ印刷する方法を次の例に示します。 アプリケーションは、ディレクトリ、3 つのパラメーターを指定するユーザーを要求が<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッドは必要ありません、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 このメソッドは、そのメソッドに渡すことができる [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイル名とパスが記述された任意のコード パスで使用できます。  
  
 3 つのパラメーター<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>のオーバー ロード<xref:System.Printing.PrintQueue.AddJob%2A>シングル スレッド アパートメントで実行する必要があるたびに、<xref:System.Boolean>パラメーターが`false`が XPSDrv 以外のプリンターが使用されている場合があります。 ただし、[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] の既定のアパートメントの状態は、マルチ スレッドです。 この例では XPSDrv 以外のプリンターを前提にしているため、この既定の状態を逆にする必要があります。  
  
 既定の状態を変更する方法は 2 つあります。 単に追加する方法の 1 つは、 <xref:System.STAThreadAttribute> (つまり、"`[System.STAThreadAttribute()]`") のアプリケーションの最初の行のすぐ上`Main`メソッド (通常は"`static void Main(string[] args)`")。 多くのアプリケーションが必要です、`Main`メソッドが 2 番目のメソッドがあるため、マルチ スレッド アパートメント状態をある: を呼び出して<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>アパートメント状態が に設定されている別のスレッドで<xref:System.Threading.ApartmentState.STA>で<xref:System.Threading.Thread.SetApartmentState%2A>します。 次の例では、この 2 番目の方法を使用します。  
  
 インスタンス化しての例では、開始、それに応じて、<xref:System.Threading.Thread>オブジェクトを渡す、 **PrintXPS**メソッドとして、<xref:System.Threading.ThreadStart>パラメーター。 (**PrintXPS** メソッドは、例の後半で定義されます)。次に、そのスレッドをシングル スレッド アパートメントに設定します。 それ以降の `Main` メソッドのコードは、この新しいスレッドを開始します。  
  
 この例の要点は、`static`**staticBatchXPSPrinter.PrintXPS** メソッド内にあります。 プリント サーバーとキューを作成すると、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルを含むディレクトリを指定するように求められます。 ディレクトリの存在との存在を検証した後\*.xps ファイルが、メソッドは、印刷キューにこのような各ファイルを追加します。 この例に渡しているために、プリンターが XPSDrv 以外の場合が前提としています。`false`の最後のパラメーターを<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッド。 このため、このメソッドはファイル内の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] マークアップを検証してから、そのマークアップをプリンターのページ記述言語に変換しようとします。 検証に失敗すると、例外がスローされます。 このコード例では、その例外をキャッチし、ユーザーに例外の発生を通知してから、次の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルの処理に進みます。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 XPSDrv プリンターを使用している場合は、最後のパラメーターを `true` に設定できます。 その場合、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] はプリンターのページ記述言語であるため、メソッドはファイルの検証や別のページ記述言語への変換を行わずにファイルをプリンターに送ります。 アプリケーションを変更するには特定デザイン時にするかどうか、アプリケーションで使用される XPSDrv プリンターでない場合、<xref:System.Printing.PrintQueue.IsXpsDevice%2A>プロパティとその検出内容に従って分岐します。  
  
 最初にあるので XPSDrv プリンターをいくつか使用可能なリリースの直後に[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]Microsoft .NET Framework では、XPSDrv 以外のプリンターが XPSDrv プリンターとして偽装するために必要があります。 そのためには、アプリケーションを実行しているコンピューターで、以下のレジストリ キーのファイルの一覧に Pipelineconfig.xml を追加します。  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>* \DependentFiles  
  
 ここで、*\<PseudoXPSPrinter* は任意の印刷キューです。 その後、コンピューターを再起動する必要があります。  
  
 このに渡すことにより`true`の最後のパラメーターとして<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>が例外を発生させることがなく *\<PseudoXPSPrinter >* XPSDrv プリンターではありません印刷されません。  
  
 **注**わかりやすくするため、上記の例ではのプレゼンスを使用して、 \*.xps 拡張機能は、ファイルのテストとして[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]します。 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルには、この拡張子を付ける必要はありません。 [isXPS.exe (isXPS 適合性ツール)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) は、ファイルが [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] かどうかをテストする 1 つの手段です。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [XPS ドキュメント](/windows/desktop/printdocs/documents)
- [XPS ドキュメントの印刷](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [マネージ コードとアンマネージ スレッド処理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS.exe (isXPS 適合性ツール)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
