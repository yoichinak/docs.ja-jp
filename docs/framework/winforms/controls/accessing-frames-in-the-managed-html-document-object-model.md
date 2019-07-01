---
title: マネージド HTML DOM (Document Object Model) へのアクセス
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: 5a9864184e92c3c6bbcf6a613fd1092238181a93
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487298"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>マネージド HTML DOM (Document Object Model) へのアクセス
一部の HTML ドキュメントが帯で構成される*フレーム*、または独自の HTML ドキュメントを保持できる windows。 フレームを使用すると、ページ内に 1 つ以上の静的な部分 (ナビゲーション バーなど) があり、その他のフレームでは内容が常に変化するような HTML ページを簡単に作成できます。  
  
 HTML の作成者は、2 つの方法のいずれかでフレームを作成できます。  
  
- `FRAMESET` タグと `FRAME` タグを使用して、固定ウィンドウを作成する。  
  
 \- または -  
  
- `IFRAME` タグを使用して、実行時に移動できるフローティング ウィンドウを作成する。  
  
1. フレームは HTML ドキュメントを含むため、DOM (Document Object Model) においてフレームはウィンドウ要素およびフレーム要素の両方として表されます  
  
2. <xref:System.Windows.Forms.HtmlWindow> の Frames コレクションを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレームに対応するウィンドウ要素を取得できます。 これは、現在の URL、ドキュメント、サイズなど、フレームのすべての動的プロパティを表します。  
  
3. <xref:System.Windows.Forms.HtmlWindow> の <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> プロパティ、<xref:System.Windows.Forms.HtmlElement.Children%2A> コレクション、または <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> や <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> などのメソッドを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレーム要素を取得できます。 これは、元の HTML ファイルに指定されている URL を含む、フレームの静的プロパティを表します。  
  
## <a name="frames-and-security"></a>フレームとセキュリティ  
 マネージ HTML DOM と呼ばれるセキュリティ対策を実装しているという事実によってフレームへのアクセスは複雑になります*クロス フレーム スクリプティング セキュリティ*します。 異なるドメインに属する複数の `FRAME` を持つ `FRAMESET` がドキュメントに含まれる場合、これらの `FRAME` は相互にやり取りできません。 つまり、`FRAME`内の情報を Web サイトからコンテンツを表示しますがアクセスできないことを`FRAME`など、サード パーティのサイトをホストする`http://www.adatum.com/`。 このセキュリティは、<xref:System.Windows.Forms.HtmlWindow> クラスのレベルで実装されます 別の Web サイトをホストする `FRAME` に関する一般情報 (URL など) は取得できますが、Web サイトの <xref:System.Windows.Forms.HtmlWindow.Document%2A> へのアクセスや、ホストしている `FRAME` または `IFRAME` のサイズや位置の変更はできません。  
  
 この規則は、<xref:System.Windows.Forms.HtmlWindow.Open%2A> メソッドおよび <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> メソッドを使用して開くウィンドウにも適用されます。 開いたウィンドウが <xref:System.Windows.Forms.WebBrowser> コントロール内でホストされているページとは異なるドメインにある場合、そのウィンドウを移動したり、内容をチェックしたりできません。 このような制限は、<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Windows フォーム ベースのアプリケーションの配置に使用した Web サイトとは異なる Web サイトを表示する場合にも適用されます。 ClickOnce 配置テクノロジを使用して、Web サイト A からアプリケーションをインストールして、使用する場合、 <xref:System.Windows.Forms.WebBrowser> Web サイト B を表示することはできませんアクセス Web サイト B のデータをします。  
  
## <a name="see-also"></a>関連項目

- [\<フレーム > 要素](https://developer.mozilla.org/docs/Web/HTML/Element/frame)
- [マネージド HTML DOM (Document Object Model) の使用](using-the-managed-html-document-object-model.md)
