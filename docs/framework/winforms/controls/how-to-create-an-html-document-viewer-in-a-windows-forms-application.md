---
title: '方法: Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: a25d8bf413614ae71676335c0c8e672caadbf885
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717753"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>方法: Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成します。
使用することができます、<xref:System.Windows.Forms.WebBrowser>コントロールを表示し、インターネットの Web ブラウザーの完全な機能を提供することがなく HTML ドキュメントを印刷します。 これは、機能は、HTML の書式設定機能を活用することが信頼されていない Web コントロールや悪意のあるスクリプト コードを含む可能性のある任意の Web ページの読み込みにユーザーを作成したくない場合に便利です。 機能を制限したい場合があります、 <xref:System.Windows.Forms.WebBrowser> HTML 電子メール ビューアーとして使用するか、アプリケーションで HTML 形式のヘルプを提供するなど、この方法を制御します。  
  
### <a name="to-create-an-html-document-viewer"></a>HTML ドキュメントビューアーを作成するには  
  
1.  設定、<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>プロパティを`false`を防ぐために、<xref:System.Windows.Forms.WebBrowser>コントロールにドロップ ファイルを開けないようにします。  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  設定、<xref:System.Windows.Forms.WebBrowser.Url%2A>プロパティを表示する最初のファイルの場所。  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロール。  
  
-   
  `System` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [WebBrowser コントロールの概要](webbrowser-control-overview.md)
- [WebBrowser セキュリティ](webbrowser-security.md)
- [方法: WebBrowser コントロールで URL に移動します](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [方法: WebBrowser コントロールを使用して印刷します。](how-to-print-with-a-webbrowser-control.md)
