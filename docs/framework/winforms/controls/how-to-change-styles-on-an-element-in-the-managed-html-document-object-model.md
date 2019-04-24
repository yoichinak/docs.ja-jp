---
title: '方法: マネージド HTML DOM (Document Object Model) の要素のスタイルを変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 804041991199dd2722e3a0f38800bafd8933bbab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333666"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>方法: マネージド HTML DOM (Document Object Model) の要素のスタイルを変更する

Html 形式でスタイルを使用すると、ドキュメントとその要素の外観を制御します。 <xref:System.Windows.Forms.HtmlDocument> <xref:System.Windows.Forms.HtmlElement>サポート<xref:System.Windows.Forms.HtmlElement.Style%2A>次の形式のスタイルの文字列を使用するプロパティ。

`name1:value1;...;nameN:valueN;`

ここでは、`DIV`フォントを Arial およびすべてのテキストを太字に設定するスタイル文字列を含む。

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

操作を使用したスタイルの問題、<xref:System.Windows.Forms.HtmlElement.Style%2A>プロパティが煩雑に追加し、文字列から個別のスタイル設定を削除することが検証されます。 たとえば、上にカーソルを置くときに、以前のテキストに斜体をレンダリングするための複雑な手順はなります、 `DIV`、斜体オフから離したときに、カーソルを取得し、`DIV`します。 この方法でスタイルの数が多いを操作する必要がある場合は、時間を問題になります。

次の手順には、HTML ドキュメントおよび要素のスタイルを簡単に操作に使用できるコードが含まれています。 プロシージャでは、新しいプロジェクトを作成し、コントロールをフォームに追加するなどの Windows フォームで基本的なタスクを実行する方法がわかっている必要があります。

### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Windows フォーム アプリケーションでスタイルの変更を処理するには

1. 新しい Windows フォーム プロジェクトを作成します。

2. 使用するプログラミング言語の適切な拡張機能で終わる新しいクラス ファイルを作成します。

3. コピー、`StyleGenerator`クラス ファイルにこのトピックの例のセクションのコードをクラスし、コードを保存します。

4. 次の HTML を Test.htm という名前のファイルに保存します。

    ```html
    <HTML>
        <BODY>

            <DIV style="font-face:arial;font-weight:bold;">
                Hello, world!
            </DIV><P>

            <DIV>
                Hello again, world!
            </DIV><P>

        </BODY>
    </HTML>
    ```

5. 追加、<xref:System.Windows.Forms.WebBrowser>という名前のコントロール`webBrowser1`プロジェクトのメイン フォームにします。

6. プロジェクトのコード ファイルに次のコードを追加します。

    > [!IMPORTANT]
    >  いることを確認、`webBrowser1_DocumentCompleted`のリスナーとしてイベント ハンドラーが構成されている、<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>イベント。 Visual Studio でのダブルクリック、<xref:System.Windows.Forms.WebBrowser>制御は、テキスト エディターで、リスナーをプログラムで構成します。  
  
     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7. プロジェクトを実行します。 最初の上にカーソルを実行`DIV`コードの効果を確認します。  
  
## <a name="example"></a>例  
 次のコード例の完全なコードを示しています、`StyleGenerator`クラスは、既存のスタイル値を解析するには、追加すると、変更、およびおよびサポートを削除するスタイル、要求された変更を新しいスタイルの値を返します。  
  
 [!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.HtmlElement>
