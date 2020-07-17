---
title: マネージド HTML DOM (Document Object Model) の非公開メンバーへのアクセス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988404"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>マネージド HTML DOM (Document Object Model) の非公開メンバーへのアクセス
マネージ html ドキュメントオブジェクトモデル (DOM) には、すべての<xref:System.Windows.Forms.HtmlElement> html 要素が共通するプロパティ、メソッド、およびイベントを公開するというクラスが含まれています。 ただし、マネージインターフェイスが直接公開しないメンバーにアクセスすることが必要になる場合があります。 このトピックでは、Web ページ内で定義されている JScript と VBScript 関数を含む、非公開メンバーにアクセスする2つの方法について説明します。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>マネージインターフェイスを使用した非公開メンバーへのアクセス  
 <xref:System.Windows.Forms.HtmlDocument>と<xref:System.Windows.Forms.HtmlElement>には、非公開メンバーへのアクセスを可能にする4つのメソッドが用意されています。 次の表は、型とそれらに対応するメソッドを示しています。  
  
|メンバーの型|メソッド|  
|-----------------|-----------------|  
|プロパティ (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|メソッド|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 これらのメソッドを使用する場合は、基になる適切な型の要素があることを前提としています。 たとえば、ユーザーがサーバーに送信する`Submit`前に、 `FORM` `FORM`の値に対していくつかの事前処理を実行できるように、HTML ページで要素のイベントをリッスンするとします。 理想的には、HTML を制御できる場合は、一意`FORM` `ID`の属性を持つようにを定義します。  
  
```html  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 このページを<xref:System.Windows.Forms.WebBrowser>コントロールに読み込んだ後、 <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>メソッドを使用して、 `FORM`を引数として使用`form1`してを実行時に取得できます。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>アンマネージインターフェイスへのアクセス  
 また、各 DOM クラスによって公開されているアンマネージコンポーネントオブジェクトモデル (COM) インターフェイスを使用して、マネージ HTML DOM の非公開メンバーにアクセスすることもできます。 これは、非公開メンバーに対して複数の呼び出しを行う必要がある場合、または非公開メンバーがマネージ HTML DOM によってラップされていない他のアンマネージインターフェイスを返す場合に推奨されます。  
  
 次の表は、マネージ HTML DOM を通じて公開されるすべてのアンマネージインターフェイスを示しています。 各リンクをクリックして、その使用法とコード例を説明します。  
  
|型|アンマネージインターフェイス|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 COM インターフェイスを使用する最も簡単な方法は、アプリケーションからアンマネージ HTML DOM library (MSHTML .dll) への参照を追加することです。ただし、この方法はサポートされていません。 詳細については、[サポート技術情報の記事 934368](https://support.microsoft.com/kb/934368)を参照してください。  
  
## <a name="accessing-script-functions"></a>スクリプト関数へのアクセス  
 HTML ページでは、JScript や VBScript などのスクリプト言語を使用して1つ以上の関数を定義できます。 これらの関数はページ内の`SCRIPT`ページ内に配置され、必要に応じて、または DOM のイベントに応答して実行できます。  
  
 HTML ページで定義したスクリプト関数は、 <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>メソッドを使用して呼び出すことができます。 スクリプトメソッドが HTML 要素を返す場合は、キャストを使用して、 <xref:System.Windows.Forms.HtmlElement>この戻り結果をに変換できます。 詳細とコード例について<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>は、「」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [マネージド HTML DOM (Document Object Model) の使用](using-the-managed-html-document-object-model.md)
