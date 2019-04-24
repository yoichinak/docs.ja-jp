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
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129507"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>マネージド HTML DOM (Document Object Model) の非公開メンバーへのアクセス
マネージ HTML ドキュメント オブジェクト モデル (DOM) と呼ばれるクラスが含まれています<xref:System.Windows.Forms.HtmlElement>プロパティ、メソッド、およびすべての HTML 要素が共通のイベントを公開します。 場合によっては、ただし、必要があります、マネージ インターフェイスを直接公開しないメンバーにアクセスします。 このトピックでは、非公開メンバーにアクセスするための 2 つの方法を調べて[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]と Web ページ内で定義されている VBScript 関数。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>管理インターフェイスを介して非公開メンバーへのアクセス  
 <xref:System.Windows.Forms.HtmlDocument> <xref:System.Windows.Forms.HtmlElement>非公開メンバーへのアクセスを有効にする 4 つのメソッドを提供します。 次の表は、種類とその対応するメソッドを示します。  
  
|メンバーの型|メソッド|  
|-----------------|-----------------|  
|プロパティ (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|メソッド|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 これらのメソッドを使用すると、適切な基になる型の要素があると見なされます。 リッスンするようにするとします、`Submit`のイベントを`FORM`HTML 要素をページにいくつかの事前処理を実行できるように、`FORM`の値は、ユーザーがそれらをサーバーに送信する前にします。 理想的には、定義、HTML を制御する場合は、`FORM`を一意に`ID`属性。  
  
```  
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
  
 このページの読み込み後、<xref:System.Windows.Forms.WebBrowser>コントロールを使用できます、<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>を取得するメソッド、`FORM`を使用して実行時に`form1`引数として。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>アンマネージ インターフェイスへのアクセス  
 各 DOM クラスによって公開されているアンマネージ コンポーネント オブジェクト モデル (COM) インターフェイスを使用してマネージ HTML DOM の非公開メンバーにアクセスすることもできます。 非公開メンバーに対して複数の呼び出しを行う必要がある場合、または非公開メンバーがマネージ HTML DOM によってラップされていないその他のアンマネージ インターフェイスを返す場合、これは推奨します。  
  
 次の表ではすべてのマネージ HTML DOM を通じて公開されるアンマネージ インターフェイス 使用状況とコード例については、各リンクをクリックします。  
  
|型|アンマネージ インターフェイス|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 これはサポートされていませんが、アプリケーションから HTML DOM のアンマネージ ライブラリ (MSHTML.dll) への参照を追加する COM インターフェイスを使用する最も簡単な方法です。 詳細については、次を参照してください。[サポート技術情報記事 934368](https://support.microsoft.com/kb/934368)します。  
  
## <a name="accessing-script-functions"></a>スクリプト関数へのアクセス  
 HTML ページなどのスクリプト言語を使用して、1 つまたは複数の関数を定義できます[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]または VBScript です。 これらの関数がの内側に配置する`SCRIPT` ページで、ページし、DOM のイベントに応答またはオンデマンドで実行できます  
  
 使用して HTML ページで定義する、スクリプト関数を呼び出すことができます、<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>メソッド。 この返される結果に変換するキャストを使用するには、スクリプト メソッドは HTML 要素を返す場合、<xref:System.Windows.Forms.HtmlElement>します。 詳細とコード例では、次を参照してください。<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>します。  
  
## <a name="see-also"></a>関連項目

- [マネージド HTML DOM (Document Object Model) の使用](using-the-managed-html-document-object-model.md)
