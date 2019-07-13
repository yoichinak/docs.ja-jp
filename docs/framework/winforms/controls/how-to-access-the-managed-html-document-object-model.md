---
title: '方法: マネージド HTML DOM (Document Object Model) にアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 2a195dc6583d5a0a72bd08b66f8933f4002e879a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487275"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>方法: マネージド HTML DOM (Document Object Model) にアクセスする
マネージド HTML ドキュメント オブジェクト モデル (DOM) には、次の 2 種類のアプリケーションからアクセスできます。  
  
- マネージド <xref:System.Windows.Forms.WebBrowser> コントロールをホストする Windows フォーム アプリケーション (.exe)。 この 2 つのテクノロジは相互に補完します。つまり、<xref:System.Windows.Forms.WebBrowser> コントロールはユーザーに対してページを表示し、HTML DOM はドキュメントの論理構造体を表します。  
  
- Internet Explorer 内でホストされた Windows フォーム <xref:System.Windows.Forms.UserControl>。 <xref:System.Windows.Forms.UserControl> をホストするページを表す HTML DOM にアクセスして、ドキュメントの構造体を変更したり、モーダル ダイアログ ボックスを開いたりするなど、さまざまな操作を行うことができます。  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Windows フォーム アプリケーションから DOM にアクセスするには  
  
1. Windows フォーム アプリケーション内で <xref:System.Windows.Forms.WebBrowser> コントロールをホストし、<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントを監視します。 コントロールのホストとイベントの監視の詳細については、「[イベント](../../../standard/events/index.md)」を参照してください。  
  
2. <xref:System.Windows.Forms.HtmlDocument> コントロールの <xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティにアクセスして、現在のページの <xref:System.Windows.Forms.WebBrowser> を取得します。  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Internet Explorer でホストされた UserControl から DOM にアクセスするには  
  
1. <xref:System.Windows.Forms.UserControl> クラスのカスタム派生クラスを作成します。 詳細については、「[方法 :複合コントロールを作成](how-to-author-composite-controls.md)です。  
  
2. <xref:System.Windows.Forms.UserControl> の Load イベント ハンドラー内に次のコードを配置します。  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
1. <xref:System.Windows.Forms.WebBrowser> コントロールを通じて DOM を使用するときは、必ず <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントが発生するまで待機してから <xref:System.Windows.Forms.WebBrowser.Document%2A> コントロールの <xref:System.Windows.Forms.WebBrowser> プロパティにアクセスするようにします。 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントは、ドキュメント全体が読み込まれた後で発生します。それ以前に DOM を使用すると、アプリケーション内でランタイム例外が発生する恐れがあります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
  
1. アプリケーションまたは <xref:System.Windows.Forms.UserControl> がマネージド HTML DOM にアクセスするには、完全信頼が必要です。 ClickOnce を使用して Windows フォーム アプリケーションを展開する場合は、アクセス許可の昇格または信頼されたアプリケーション配置; を使用して完全な信頼を要求することができます。参照してください[ClickOnce アプリケーションのセキュリティで保護する](/visualstudio/deployment/securing-clickonce-applications)詳細についてはします。  
  
## <a name="see-also"></a>関連項目

- [マネージド HTML DOM (Document Object Model) の使用](using-the-managed-html-document-object-model.md)
