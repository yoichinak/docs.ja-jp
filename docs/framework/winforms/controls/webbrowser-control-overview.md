---
title: WebBrowser コントロールの概要
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: c75d0b348a2f3dd678f2bfb235bce2e4e227c4b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792133"
---
# <a name="webbrowser-control-overview"></a>WebBrowser コントロールの概要
<xref:System.Windows.Forms.WebBrowser>コントロールでは、WebBrowser ActiveX コントロールのマネージ ラッパーが用意されています。 マネージ ラッパーを使用して、Windows フォーム クライアント アプリケーションに Web ページを表示できます。 使用することができます、<xref:System.Windows.Forms.WebBrowser>アプリケーションか、Internet Explorer の Web 閲覧機能を複製するコントロールが既定の Internet Explorer の機能を無効にしてとして単純な HTML ドキュメント ビューアー コントロールを使用します。 DHTML ベースのユーザー インターフェイス要素をフォームに追加しにホストされているという事実を非表示にするコントロールを使用することもできます、<xref:System.Windows.Forms.WebBrowser>コントロール。 この方法では、Web コントロールと 1 つのアプリケーションでの Windows フォーム コントロールをシームレスに結合できます。  
  
## <a name="frequently-used-properties-methods-and-events"></a>よく使用されるプロパティ、メソッド、およびイベント  
 <xref:System.Windows.Forms.WebBrowser>コントロールがいくつかのプロパティ、メソッド、および Internet Explorer でのコントロールを実装するために使用できるイベント。 たとえば、使用することができます、 `Navigate` 、アドレス バーを実装するメソッドと`GoBack`、 `GoForward`、 `Stop`、および`Refresh`ツールバーにあるナビゲーション ボタンを実装するメソッド。 処理することができます、`Navigated`の値で、アドレス バーを更新するイベント、`Url`プロパティと値のタイトル バー、`DocumentTitle`プロパティ。  
  
 設定することができます、アプリケーション内で独自のページ コンテンツを生成する場合、`DocumentText`プロパティ。 現在の Web ページの内容を操作する HTML ドキュメント オブジェクト モデル (DOM) に慣れている場合もできる、`Document`プロパティ。 このプロパティを格納して、ファイル間を移動する代わりに、メモリ内のドキュメントを変更します。  
  
 `Document`プロパティでは Web ページのクライアント アプリケーション コードからコードをスクリプトで実装されるメソッドを呼び出すこともできます。 クライアント アプリケーションのコードには、スクリプト コードからアクセスするには、設定、`ObjectForScripting`プロパティ。 指定したオブジェクトとして、スクリプト コードでアクセスできる、`window.external`オブジェクト。  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティ|現在の Web ページの HTML ドキュメント オブジェクト モデル (DOM) への管理アクセスを提供するオブジェクトを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベント|Web ページの読み込みが完了すると発生します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティ|取得または HTML の現在の Web ページのコンテンツを設定します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> プロパティ|現在の Web ページのタイトルを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> メソッド|履歴に前のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> メソッド|履歴に次のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッド|指定した URL に移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> イベント|取り消されるアクションを有効にすると、ナビゲーションが開始する前に発生します。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> プロパティ|取得または Web ページのスクリプト コードは、アプリケーションとの通信に使用できるオブジェクトを設定します。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> メソッド|現在の Web ページを印刷します。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> メソッド|現在の Web ページを再読み込みします。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> メソッド|現在のナビゲーションを停止し、音声とアニメーションなどの動的なページ要素を停止します。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> プロパティ|取得または現在の Web ページの URL を設定します。 このプロパティを設定すると、新しい URL にコントロールが移動します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [方法: WebBrowser コントロールで URL に移動します](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [方法: WebBrowser コントロールを使用して印刷します。](how-to-print-with-a-webbrowser-control.md)
- [方法: Windows フォーム アプリケーションに Web ブラウザーの機能を追加します。](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [方法: Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成します。](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [方法: DHTML コードとクライアント アプリケーション コード間の双方向通信を実装します。](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser セキュリティ](webbrowser-security.md)
