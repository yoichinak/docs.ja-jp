---
title: PrintDocument コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198635"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument コンポーネントの概要 (Windows フォーム)
Windows フォーム [PrintDocument](printdocument-component-windows-forms.md) コンポーネントを使用して、印刷対象を示すプロパティを設定し、Windows ベースのアプリケーション内でドキュメントを印刷できます。 このコンポーネントは、ドキュメント印刷のあらゆる側面を制御するために、[PrintDialog](printdialog-component-windows-forms.md) コンポーネントと組み合わせて使用できます。  
  
## <a name="working-with-the-printdocument-component"></a>PrintDocument コンポーネントの操作  
 2 つの主なシナリオを含む、<xref:System.Drawing.Printing.PrintDocument>コンポーネントします。  
  
-   簡易印刷ジョブ (個々のテキスト ファイルを印刷する場合など)。 追加すると、このような場合、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを Windows フォーム内のファイルを印刷するプログラミング ロジックを追加し、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラー。 プログラミング ロジック、<xref:System.Drawing.Printing.PrintDocument.Print%2A>ドキュメントを印刷する方法。 このメソッドは、送信、<xref:System.Drawing.Graphics>に含まれる、オブジェクト、<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>のプロパティ、<xref:System.Drawing.Printing.PrintPageEventArgs>プリンターへのクラス。 使用してテキスト ドキュメントを印刷する方法を示す例については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[方法。Windows フォームで複数ページのテキスト ファイルを印刷](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)します。  
  
-   より複雑な印刷ジョブ (作成した印刷ロジックを再利用する場合など)。 このような場合は、新しいコンポーネントを派生させる、<xref:System.Drawing.Printing.PrintDocument>コンポーネントと上書き (を参照してください[オーバーライド](~/docs/visual-basic/language-reference/modifiers/overrides.md)Visual basic または[オーバーライド](~/docs/csharp/language-reference/keywords/override.md)のC#)、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント。  
  
 フォームに追加されたとき、<xref:System.Drawing.Printing.PrintDocument>コンポーネント、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows フォームにおける印刷のサポート](../advanced/windows-forms-print-support.md)
- [PrintDocument コンポーネント](printdocument-component-windows-forms.md)
