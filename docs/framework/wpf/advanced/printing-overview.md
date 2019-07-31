---
title: 印刷の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 4f8fd92105bd5ae09e0c1daa2e0db48b74cde77c
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68672039"
---
# <a name="printing-overview"></a>印刷の概要
Microsoft .NET Framework を使用すると、Windows Presentation Foundation (WPF) を使用するアプリケーション開発者は、豊富な新しい印刷および印刷システム管理 Api を利用できます。 また、[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] によって、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーションを作成する開発者と、アンマネージ コードを使用する開発者も、これらの印刷システム拡張機能の一部を使用できます。 この新しい機能の中核となるのが、新しい [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ファイル形式と [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 印刷パスです。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>XPS について  
 XPS は、電子ドキュメント形式、スプールファイル形式、およびページ記述言語です。 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]、[!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]、その他の業界標を使用してクロス プラットフォームのドキュメントを作成する OpenDocument 形式の 1 つです。 XPS は、デジタルドキュメントの作成、共有、印刷、表示、アーカイブを行うプロセスを簡略化します。 XPS の詳細については、「 [Xps ドキュメント](/windows/desktop/printdocs/documents)」を参照してください。  
  
 を使用して xps ベースのコンテンツを[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]印刷するいくつかの方法については、「[プログラムによる xps ファイルの印刷](how-to-programmatically-print-xps-files.md)」をご利用ください。 このトピックに含まれるコンテンツの確認中にこれらのサンプルを参照すると、役に立つ場合があります。 (アンマネージコードの開発者は、 [MXDC_ESCAPE 関数](/windows/desktop/printdocs/mxdc-escape)のドキュメントを参照する必要があります。 Windows フォーム開発者は、完全な<xref:System.Drawing.Printing> [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]印刷パスをサポートしていない名前空間の API を使用する必要がありますが、ハイブリッドの GDI から XPS への印刷パスがサポートされています。 以下の**印刷パスのアーキテクチャ**をご覧ください。)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>XPS 印刷パス  
 XML Paper Specification (XPS) の印刷パスは、Windows [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]アプリケーションでの印刷の処理方法を再定義する新機能です。 は[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] 、ドキュメントのプレゼンテーション言語 (RTF など)、印刷スプーラの形式 (WMF など)、およびページ記述言語 (PCL や Postscript など) を置き換えることができるため、新しい印刷パスでは、アプリケーションパブリケーションからの XPS 形式を印刷ドライバーまたはデバイスでの最終処理。  
  
 Xps 印刷パスは xps プリンタードライバーモデル (XPSDrv) に基づいて構築されています。これにより[!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] 、印刷、カラーサポートの向上、および大幅に改善された印刷パフォーマンスなど、開発者にとっていくつかの利点が得られます。 (XPSDrv の詳細については、 [Windows Driver Kit のドキュメント](/windows-hardware/drivers/)を参照してください)。  
  
 XPS ドキュメントの印刷スプーラの操作は、基本的に以前のバージョンの Windows と同じです。 ただし、既存の GDI 印刷パスに加えて XPS 印刷パスをサポートするように強化されています。 新しい印刷パスは、ネイティブで XPS スプールファイルを使用します。 以前のバージョンの用に記述されたユーザー [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]モードのプリンタードライバーは引き続き機能しますが、xps 印刷パスを使用するには xps プリンタードライバー (XPSDrv) が必要です。  
  
 XPS 印刷パスの利点は、次のとおりです。  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] の印刷のサポート。  
  
- 高度なカラー プロファイルのネイティブ サポート (1 チャンネルあたり 32 ビット (bpc)、CMYK、名前付きの色、n インクなど)、および透明度とグラデーションのネイティブ サポート。  
  
- .NET Framework と[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ベースの両方のアプリケーションの印刷パフォーマンスが向上しました。  
  
- 業界標準の XPS 形式。  
  
 基本的な印刷シナリオでは、ユーザーインターフェイス、構成、およびジョブの送信用の1つのエントリポイントで、シンプルで直感的な API を使用できます。 高度なシナリオ用に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] のカスタマイズ (または [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がまったくない)、同期または非同期の印刷、および一括印刷の機能のサポートが追加されました。 いずれのオプションでも、完全または部分的な信頼モードでの印刷のサポートを提供します。  
  
 XPS は、拡張性を考慮して設計されています。 機能拡張フレームワークを使用することにより、機能をモジュール方式で XPS に追加できます。 拡張機能は、次のとおりです。  
  
- 印刷スキーマ。 パブリックのスキーマは定期的に更新され、デバイスの機能を迅速に拡張することができます。 (下記の「**PrintTicket と PrintCapabilities**」をご覧ください。)  
  
- 拡張可能なフィルター パイプライン。 XPS プリンタードライバー (XPSDrv) フィルターパイプラインは、XPS ドキュメントの直接およびスケーラブルな印刷を有効にするように設計されています。 詳細については、「 [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers)」を参照してください。 
  
### <a name="print-path-architecture"></a>印刷パスのアーキテクチャ  
 と .NET Framework [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]の両方のアプリケーションで xps [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]がサポートされますが、Windows フォームアプリケーションでは、xps プリンタードライバー (XPSDrv) 用の xps 形式のコンテンツを作成するために、GDI から xps への変換を使用します。 これらのアプリケーションは XPS 印刷パスを使用する必要がなく、拡張メタファイル (EMF) ベースの印刷を引き続き使用できます。 ただし、ほとんどの XPS 機能と拡張機能は、XPS 印刷パスを対象とするアプリケーションでのみ使用できます。  
  
 および Windows フォームアプリケーションで[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] XPSDrv ベースのプリンターを使用できるようにするために、xps プリンタードライバー (XPSDrv) は、GDI から xps 形式への変換をサポートしています。 XPSDrv モデルでは、 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]アプリケーションがドキュメントを印刷[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]できるように、XPS から GDI 形式のコンバーターも提供されています。 アプリケーション[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の場合、XPS 形式から GDI 形式への変換は、書き込み<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>操作の対象<xref:System.Windows.Xps.XpsDocumentWriter>の印刷キューに XPSDrv ドライバーがない場合は常に、クラスのメソッド<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>とメソッドによって自動的に行われます。 (Windows フォームアプリケーションはドキュメント[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]を印刷できません。)  
  
 次の図は、印刷サブシステムを示し、によっ[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]て提供される部分と、ソフトウェアとハードウェアのベンダーによって定義される部分を定義しています。  
  
 ![スクリーンショットは XPS 印刷システムを示しています。](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>XPS の基本的な印刷  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]基本 API と高度な API の両方を定義します。 広範な印刷のカスタマイズや完全な XPS 機能セットへのアクセスを必要としないアプリケーションでは、基本的な印刷サポートを利用できます。 基本的な印刷サポートは、最小構成を必要とし、使い慣れた [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を特長とする印刷ダイアログ コントロールを介して公開されます。 この簡略化された印刷モデルを使用して、多くの XPS 機能を使用できます。  
  
#### <a name="printdialog"></a>PrintDialog  
 コントロール<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>は、、構成、および XPS [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ジョブを送信するための1つのエントリポイントを提供します。 コントロールのインスタンス化と使用方法については、「[方法 : 印刷ダイアログ ボックスを呼び出す](how-to-invoke-a-print-dialog.md)」をご覧ください。  
  
### <a name="advanced-xps-printing"></a>高度な XPS の印刷  
 XPS 機能の完全なセットにアクセスするには、高度な印刷 API を使用する必要があります。 いくつかの関連する API については、以下で詳しく説明します。 XPS 印刷パス api の完全な一覧については<xref:System.Windows.Xps> 、 <xref:System.Printing> 「」および「名前空間の参照」を参照してください。  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket と PrintCapabilities  
 クラス<xref:System.Printing.PrintTicket> と<xref:System.Printing.PrintCapabilities>クラスは、XPS の高度な機能の基盤です。 いずれの種類のオブジェクトも、照合順序、両面印刷、ホチキス止めなど、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 形式の印刷向け機能の構造になっています。これらの構造は、印刷スキーマによって定義されます。 <xref:System.Printing.PrintTicket> は、プリンターに印刷ジョブの処理方法を指示します。 <xref:System.Printing.PrintCapabilities> クラスは、プリンターの機能を定義します。 プリンターの機能のクエリを実行すると、プリンターのサポート機能を最大限に活用する <xref:System.Printing.PrintTicket> を作成できます。 同様に、サポートされていない機能を回避できます。  
  
 次の例は、プリンターの <xref:System.Printing.PrintCapabilities> でクエリを実行する方法と、コードを使用した <xref:System.Printing.PrintTicket> の作成方法を示しています。  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer と PrintQueue  
 <xref:System.Printing.PrintServer> クラスはネットワーク プリント サーバーを表し、<xref:System.Printing.PrintQueue> クラスはプリンターとそれに関連付けられた出力ジョブのキューを表します。 これらの Api を一緒に使用することで、サーバーの印刷ジョブを高度に管理できます。 <xref:System.Printing.PrintServer>、またはその派生クラスのいずれかを使用すると、<xref:System.Printing.PrintQueue> を管理できます。 新しい印刷ジョブをキューに挿入するには、<xref:System.Printing.PrintQueue.AddJob%2A> メソッドを使用します。  
  
 次の例は、コードを使用して <xref:System.Printing.LocalPrintServer> を作成し、既定の <xref:System.Printing.PrintQueue> にアクセスする方法を示しています。  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 とメソッドを含むは、XPS ドキュメントをに<xref:System.Printing.PrintQueue>書き込むために使用されます。 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> <xref:System.Windows.Xps.XpsDocumentWriter> <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> たとえば、 <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29>メソッドは、XPS ドキュメントを出力し<xref:System.Printing.PrintTicket> 、同期的に出力するために使用されます。 メソッド<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>は、XPS ドキュメントを出力し<xref:System.Printing.PrintTicket> 、非同期的に出力するために使用されます。  
  
 次の例は、コードを使用して <xref:System.Windows.Xps.XpsDocumentWriter> を作成する方法を示しています。  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 さらに <xref:System.Printing.PrintQueue.AddJob%2A> メソッドは印刷方法を提供します。 「[方法 : XPS ファイルをプログラムにより印刷する](how-to-programmatically-print-xps-files.md)」をご覧ください。 詳細について。  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>GDI 印刷パス  
 アプリケーションでは xps 印刷[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]パスがネイティブにサポートされていますが、Windows フォームアプリケーションも一部の xps 機能を利用できます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] XPS プリンタードライバー (XPSDrv) は、GDI ベースの出力を XPS 形式に変換できます。 高度なシナリオでは、 [MICROSOFT XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)を使用して、コンテンツのカスタム変換がサポートされます。 同様に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、アプリケーションで<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>は、 <xref:System.Windows.Xps.XpsDocumentWriter>クラスのメソッドまたは<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>メソッドのいずれかを呼び出し、XpsDrv 以外のプリンターをターゲットの印刷キューとして指定することによって、GDI 印刷パスに出力することもできます。  

XPS の機能やサポートを必要としないアプリケーションでは、現在の GDI 印刷パスは変更されません。  
  
- GDI 印刷パスおよびさまざまな XPS 変換オプションに関するその他の参照情報については、「 [MICROSOFT Xps Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) 」および「 [XPSDrv プリンタードライバー](/windows-hardware/drivers/print/xpsdrv-printer-drivers)」を参照してください。  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>XPSDrv ドライバー モデル  
 Xps 印刷パスを使用すると、xps 対応のプリンターまたはドライバーに印刷するときに、ネイティブの印刷スプール形式として XPS を使用することでスプーラの効率性が向上します。 簡略化されたスプールプロセスにより、ドキュメントをスプールする前に、EMF データファイルなどの中間スプールファイルを生成する必要がなくなります。 スプールファイルのサイズを小さくすることで、XPS の印刷パスを使用してネットワークトラフィックを削減し、印刷のパフォーマンスを向上させることができます。  
  
 EMF は、アプリケーションの出力を、レンダリングサービスの GDI への一連の呼び出しとして表すクローズ形式です。 EMF とは異なり、XPS スプール形式は、XPS ベースのプリンタードライバー (XPSDrv) に出力するときに、さらに解釈する必要なく、実際のドキュメントを表します。 ドライバーは、その形式のデータを直接操作できます。 この機能により、EMF ファイルおよび GDI ベースの印刷ドライバーを使用するときに必要なデータと色空間の変換が不要になります。  
  
 通常は、XPS プリンタードライバー (XPSDrv) を対象とする XPS ドキュメントを EMF と同等のものと比較すると、スプールファイルのサイズが小さくなります。ただし、例外があります。  
  
- ベクター グラフィックが非常に複雑で、複数の階層があるか、非効率的に記述されている場合、同じグラフィックスのビットマップ形式のバージョンよりもサイズが大きくなることがあります。  
  
- 画面表示の目的で、XPS ファイルにはデバイス フォントおよびコンピューター ベースのフォントが埋め込まれます。一方、GDI のスプール ファイルにはデバイス フォントは埋め込まれません。 しかし、両方の種類のフォントがサブセット化されているため (下記参照)、プリンター ドライバーは、ファイルをプリンターに送信する前にデバイス フォントを削除することができます。  
  
 スプール サイズの削減は、いくつかのメカニズムを通じて行われます。  
  
- **フォントのサブセット化**。 実際のドキュメント内で使用されている文字だけが XPS ファイルに格納されます。  
  
- **高度なグラフィックスのサポート**。 透過性とグラデーションのプリミティブのネイティブ サポートにより、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ドキュメントの内容のラスタライズを回避できます。  
  
- **共通リソースの識別**。 複数回使用するリソース (会社のロゴを表す画像など) は共有リソースとして扱われ、一度だけ読み込まれます。  
  
- **ZIP 圧縮**。 すべての XPS ドキュメントで ZIP 圧縮を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [方法トピック](printing-how-to-topics.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [XPS ドキュメント](/windows/desktop/printdocs/documents)
- [ドキュメントのシリアル化および保存](document-serialization-and-storage.md)
- [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
