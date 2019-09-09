---
title: PrintDocument コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928995"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument コンポーネントの概要 (Windows フォーム)

Windows フォーム [PrintDocument](printdocument-component-windows-forms.md) コンポーネントを使用して、印刷対象を示すプロパティを設定し、Windows ベースのアプリケーション内でドキュメントを印刷できます。 このコンポーネントは、ドキュメント印刷のあらゆる側面を制御するために、[PrintDialog](printdialog-component-windows-forms.md) コンポーネントと組み合わせて使用できます。

## <a name="working-with-the-printdocument-component"></a>PrintDocument コンポーネントの操作

コンポーネントに<xref:System.Drawing.Printing.PrintDocument>関連する主なシナリオは、次の2つです。

- 簡易印刷ジョブ (個々のテキスト ファイルを印刷する場合など)。 このような場合は、 <xref:System.Drawing.Printing.PrintDocument>コンポーネントを Windows フォームに追加し、 <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントハンドラーでファイルを出力するプログラミングロジックを追加します。 プログラミングロジックは、ドキュメントを印刷<xref:System.Drawing.Printing.PrintDocument.Print%2A>するメソッドとなする必要があります。 このメソッドは、 <xref:System.Drawing.Graphics> <xref:System.Drawing.Printing.PrintPageEventArgs>クラスの<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>プロパティに含まれるオブジェクトをプリンターに送信します。 <xref:System.Drawing.Printing.PrintDocument>コンポーネントを使用してテキストドキュメントを印刷する方法を示す例につい[ては、「方法:Windows フォーム](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)で複数ページのテキストファイルを印刷します。

- より複雑な印刷ジョブ (作成した印刷ロジックを再利用する場合など)。 この<xref:System.Drawing.Printing.PrintDocument>ような場合は、コンポーネントから新しいコンポーネントを派生させ、 <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベントのオーバーライド (Visual Basic または[オーバーライド](../../../csharp/language-reference/keywords/override.md)[のオーバーライドを参照](../../../visual-basic/language-reference/modifiers/overrides.md) C#) を行います。

フォームに追加されると、 <xref:System.Drawing.Printing.PrintDocument> Visual Studio の Windows フォームデザイナーの下部にあるトレイにコンポーネントが表示されます。

## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows フォームにおける印刷のサポート](../advanced/windows-forms-print-support.md)
- [PrintDocument コンポーネント](printdocument-component-windows-forms.md)
