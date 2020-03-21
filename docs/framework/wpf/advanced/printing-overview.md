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
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187208"
---
# <a name="printing-overview"></a>印刷の概要
Microsoft .NET Framework を使用すると、Windows プレゼンテーション ファンデーション (WPF) を使用するアプリケーション開発者は、印刷および印刷システム管理 API の豊富な新しいセットを持っています。 Windows Vista では、これらの印刷システムの機能強化の一部は、Windows フォーム アプリケーションを作成する開発者やアンマネージ コードを使用する開発者にも利用できます。 この新機能の中核となるのは、新しい XML 用紙仕様 (XPS) ファイル形式と XPS 印刷パスです。  
  
 このトピックの内容は次のとおりです。  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>XPS について  
 XPS は、電子ドキュメント形式、スプール ファイル形式、およびページ記述言語です。 XML、オープンパッケージング規則 (OPC)、およびその他の業界標準を使用してクロスプラットフォームドキュメントを作成するオープンドキュメント形式です。 XPS により、デジタルドキュメントの作成、共有、印刷、表示、アーカイブのプロセスが簡素化されます。 XPS の詳細については[、XPS ドキュメント](/windows/desktop/printdocs/documents)を参照してください。  
  
 WPF を使用して XPS ベースのコンテンツを印刷する方法については、「[プログラムで XPS ファイルを印刷](how-to-programmatically-print-xps-files.md)する」で説明します。 このトピックに含まれるコンテンツの確認中にこれらのサンプルを参照すると、役に立つ場合があります。 (アンマネージ コード開発者は[、 MXDC_ESCAPE関数](/windows/desktop/printdocs/mxdc-escape)のドキュメントを参照してください。 Windows フォーム開発者は、完全な<xref:System.Drawing.Printing>XPS 印刷パスをサポートしていないが、ハイブリッド GDI から XPS への印刷パスをサポートしている名前空間で API を使用する必要があります。 以下の**印刷パスのアーキテクチャ**をご覧ください。)  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>XPS 印刷パス  
 XML 用紙仕様 (XPS) 印刷パスは、Windows アプリケーションでの印刷の処理方法を再定義する新しい Windows 機能です。 XPS はドキュメントのプレゼンテーション言語 (RTF など)、印刷スプーラ形式 (WMF など)、およびページ記述言語 (PCL や Postscript など) を置き換えることができます。新しい印刷パスは、アプリケーションの公開から印刷ドライバまたはデバイスの最終処理までの XPS 形式を維持します。  
  
 XPS 印刷パスは XPS プリンター ドライバー モデル (XPSDrv) に基づいて構築されており、"WYSIWYG) 印刷、色のサポートの向上、および大幅な向上などの開発者にさまざまな利点があります。 (XPSDrv の詳細については[、Windows ドライバー キットのドキュメントを参照してください](/windows-hardware/drivers/)。  
  
 XPS ドキュメントの印刷スプーラの動作は、以前のバージョンの Windows と基本的に同じです。 ただし、既存の GDI 印刷パスに加えて、XPS 印刷パスをサポートするように拡張されています。 新しい印刷パスは、XPS スプール ファイルをネイティブに使用します。 以前のバージョンの Windows 用に作成されたユーザー モードプリンター ドライバーは引き続き動作しますが、XPS プリンター ドライバー (XPSDrv) は XPS 印刷パスを使用するために必要です。  
  
 XPS 印刷パスの利点は、次のような大きな意味を持ちます。  
  
- WYSIWYG 印刷サポート  
  
- 高度なカラー プロファイルのネイティブ サポート (1 チャンネルあたり 32 ビット (bpc)、CMYK、名前付きの色、n インクなど)、および透明度とグラデーションのネイティブ サポート。  
  
- .NET Framework ベースと Win32 ベースのアプリケーションの両方の印刷パフォーマンスが向上しました。  
  
- 業界標準の XPS 形式。  
  
 基本的な印刷シナリオでは、シンプルで直感的な API を使用して、ユーザー インターフェイス、構成、およびジョブの送信を 1 つのエントリ ポイントで使用できます。 高度なシナリオ用に、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] のカスタマイズ (または [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がまったくない)、同期または非同期の印刷、および一括印刷の機能のサポートが追加されました。 いずれのオプションでも、完全または部分的な信頼モードでの印刷のサポートを提供します。  
  
 XPS は、拡張性を考慮して設計されています。 機能拡張フレームワークを使用すると、機能と機能をモジュール式で XPS に追加できます。 拡張機能は、次のとおりです。  
  
- 印刷スキーマ。 パブリックのスキーマは定期的に更新され、デバイスの機能を迅速に拡張することができます。 (下記の「**PrintTicket と PrintCapabilities**」をご覧ください。)  
  
- 拡張可能なフィルター パイプライン。 XPS プリンター ドライバー (XPSDrv) フィルター パイプラインは、XPS ドキュメントの直接印刷とスケーラブルな印刷の両方を有効にするように設計されています。 詳しくは、[XPSDrv プリンター ドライバーに関するページ](/windows-hardware/drivers/print/xpsdrv-printer-drivers)をご覧ください。
  
### <a name="print-path-architecture"></a>印刷パスのアーキテクチャ  
 Win32 アプリケーションと .NET Framework アプリケーションの両方が XPS をサポートしていますが、Win32 アプリケーションと Windows フォーム アプリケーションでは、XPS プリンター ドライバー (XPSDrv) 用の XPS 形式のコンテンツを作成するために GDI から XPS への変換が使用されます。 これらのアプリケーションは、XPS 印刷パスを使用する必要はありませんし、拡張メタファイル (EMF) ベースの印刷を引き続き使用できます。 ただし、ほとんどの XPS 機能と拡張機能は、XPS 印刷パスを対象とするアプリケーションでのみ使用できます。  
  
 Win32 および Windows フォーム アプリケーションで XPSDrv ベースのプリンタを使用できるようにするために、XPS プリンター ドライバー (XPSDrv) は GDI から XPS 形式への変換をサポートしています。 XPSDrv モデルには、XPS から GDI 形式へのコンバータも用意されているので、Win32 アプリケーションは XPS ドキュメントを印刷できます。 WPF アプリケーションの場合、書き込み操作のターゲット印刷キューに<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>XPSDrv<xref:System.Windows.Xps.XpsDocumentWriter>ドライバが存在しない場合は、クラスのメソッドと<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>メソッドによって XPS から GDI 形式への変換が自動的に行われます。 (Windows フォーム アプリケーションは XPS ドキュメントを印刷できません)。  
  
 次の図は、印刷サブシステムを示し、Microsoft が提供する部分と、ソフトウェアベンダとハードウェア ベンダによって定義された部分を定義しています。  
  
 ![スクリーンショットは、XPS 印刷システムを示しています。](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>XPS の基本的な印刷  
 WPF では、基本的な API と高度な API の両方を定義します。 広範な印刷のカスタマイズや完全な XPS 機能セットへのアクセスを必要としないアプリケーションでは、基本的な印刷サポートが利用可能です。 基本的な印刷サポートは、最小構成を必要とし、使い慣れた [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を特長とする印刷ダイアログ コントロールを介して公開されます。 この簡略化された印刷モデルを使用して、多くの XPS 機能を利用できます。  
  
#### <a name="printdialog"></a>PrintDialog  
 この<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>コントロールは、構成、および[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]XPS ジョブのサブミッションに対して単一のエントリ ポイントを提供します。 コントロールのインスタンス化と使用方法については、「[方法 : 印刷ダイアログ ボックスを呼び出す](how-to-invoke-a-print-dialog.md)」をご覧ください。  
  
### <a name="advanced-xps-printing"></a>高度な XPS の印刷  
 XPS 機能の完全なセットにアクセスするには、高度な印刷 API を使用する必要があります。 関連する API の詳細については、以下で詳しく説明します。 XPS 印刷パス API の完全な一覧については<xref:System.Windows.Xps>、<xref:System.Printing>および 名前空間のリファレンスを参照してください。  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket と PrintCapabilities  
 クラス<xref:System.Printing.PrintTicket>と<xref:System.Printing.PrintCapabilities>クラスは、高度な XPS 機能の基礎です。 どちらのオブジェクトも、照合、両面印刷、ホチキス止めなどの印刷指向の機能の XML 形式の構造です。これらの構造体は、印刷スキーマによって定義されます。 <xref:System.Printing.PrintTicket> は、プリンターに印刷ジョブの処理方法を指示します。 <xref:System.Printing.PrintCapabilities> クラスは、プリンターの機能を定義します。 プリンターの機能のクエリを実行すると、プリンターのサポート機能を最大限に活用する <xref:System.Printing.PrintTicket> を作成できます。 同様に、サポートされていない機能を回避できます。  
  
 次の例は、プリンターの <xref:System.Printing.PrintCapabilities> でクエリを実行する方法と、コードを使用した <xref:System.Printing.PrintTicket> の作成方法を示しています。  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer と PrintQueue  
 <xref:System.Printing.PrintServer> クラスはネットワーク プリント サーバーを表し、<xref:System.Printing.PrintQueue> クラスはプリンターとそれに関連付けられた出力ジョブのキューを表します。 これらの API を組み合わせることで、サーバーの印刷ジョブの高度な管理が可能になります。 <xref:System.Printing.PrintServer>、またはその派生クラスのいずれかを使用すると、<xref:System.Printing.PrintQueue> を管理できます。 新しい印刷ジョブをキューに挿入するには、<xref:System.Printing.PrintQueue.AddJob%2A> メソッドを使用します。  
  
 次の例は、コードを使用して <xref:System.Printing.LocalPrintServer> を作成し、既定の <xref:System.Printing.PrintQueue> にアクセスする方法を示しています。  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 多<xref:System.Windows.Xps.XpsDocumentWriter>くの<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>メソッドと メソッド<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>を持つ 、 は、 XPS<xref:System.Printing.PrintQueue>ドキュメントを に書き込むために使用されます。 たとえば、この<xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29>メソッドは、XPS ドキュメントを<xref:System.Printing.PrintTicket>同期的に出力するために使用されます。 この<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>メソッドは、XPS ドキュメント<xref:System.Printing.PrintTicket>を非同期で出力するために使用されます。  
  
 次の例は、コードを使用して <xref:System.Windows.Xps.XpsDocumentWriter> を作成する方法を示しています。  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 さらに <xref:System.Printing.PrintQueue.AddJob%2A> メソッドは印刷方法を提供します。 「[方法 : XPS ファイルをプログラムにより印刷する](how-to-programmatically-print-xps-files.md)」をご覧ください。 を参照してください。  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>GDI 印刷パス  
 WPF アプリケーションは、ネイティブで XPS 印刷パスをサポートしていますが、Win32 および Windows フォーム アプリケーションは、いくつかの XPS 機能を利用することもできます。 XPS プリンター ドライバー (XPSDrv) は、Xps 形式に GDI ベースの出力を変換できます。 高度なシナリオでは[、Microsoft XPS ドキュメント コンバータ (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)を使用してコンテンツのカスタム変換がサポートされています。 同様に、WPF アプリケーションは、<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A><xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A><xref:System.Windows.Xps.XpsDocumentWriter>クラスの or メソッドのいずれかを呼び出し、非 XpsDrv プリンターをターゲット印刷キューとして指定することで、GDI 印刷パスに出力することもできます。  

XPS の機能やサポートを必要としないアプリケーションの場合、現在の GDI 印刷パスは変更されません。  
  
- GDI の印刷パスとさまざまな XPS 変換オプションに関するその他の参考資料については[、Microsoft XPS ドキュメント コンバータ (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)および[XPSDrv プリンタ ドライバ](/windows-hardware/drivers/print/xpsdrv-printer-drivers)を参照してください。  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>XPSDrv ドライバー モデル  
 XPS 印刷パスは、XPS 対応のプリンターまたはドライバーに印刷するときに、ネイティブ印刷スプール形式として XPS を使用することにより、スプーラの効率を向上させます。 単純化されたスプール処理により、文書がスプールされる前に、EMF データ・ファイルなどの中間スプール・ファイルを生成する必要がなくなります。 スプール ファイル のサイズを小さくすることで、XPS 印刷パスを使用すると、ネットワーク トラフィックを削減し、印刷パフォーマンスを向上させることができます。  
  
 EMF は、アプリケーション出力をレンダリング サービス用の GDI への一連の呼び出しとして表す閉じた形式です。 EMF とは異なり、XPS スプール形式は、XPS ベースのプリンター ドライバー (XPSDrv) に出力するときに、それ以上の解釈を必要とせずに実際のドキュメントを表します。 ドライバーは、その形式のデータを直接操作できます。 この機能により、EMF ファイルと GDI ベースの印刷ドライバーを使用する場合に必要なデータと色空間の変換が不要になります。  
  
 通常、XPS プリンター ドライバー (XPSDrv) を対象とする XPS ドキュメントを使用すると、スプール ファイルのサイズが小さくなります。ただし、次の例外があります。  
  
- ベクター グラフィックが非常に複雑で、複数の階層があるか、非効率的に記述されている場合、同じグラフィックスのビットマップ形式のバージョンよりもサイズが大きくなることがあります。  
  
- 画面表示の目的で、XPS ファイルにはデバイス フォントおよびコンピューター ベースのフォントが埋め込まれます。一方、GDI のスプール ファイルにはデバイス フォントは埋め込まれません。 しかし、両方の種類のフォントがサブセット化されているため (下記参照)、プリンター ドライバーは、ファイルをプリンターに送信する前にデバイス フォントを削除することができます。  
  
 スプール サイズの削減は、いくつかのメカニズムを通じて行われます。  
  
- **フォントのサブセット化**。 実際のドキュメント内で使用されている文字のみが XPS ファイルに格納されます。  
  
- **高度なグラフィックスのサポート**。 透過性とグラデーション プリミティブのネイティブ サポートにより、XPS ドキュメント内のコンテンツのラスタライズが回避されます。  
  
- **共通リソースの識別**。 複数回使用するリソース (会社のロゴを表す画像など) は共有リソースとして扱われ、一度だけ読み込まれます。  
  
- **ZIP 圧縮**: すべての XPS ドキュメントでは、ZIP 圧縮が使用されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [ハウツートピック](printing-how-to-topics.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [XPS ドキュメント](/windows/desktop/printdocs/documents)
- [ドキュメントのシリアル化と保存](document-serialization-and-storage.md)
- [マイクロソフト XPS ドキュメント コンバータ (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
