---
title: PrintPreviewControl コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012599"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PrintPreviewControl>を表示するために使用する[PrintDocument](printdocument-component-windows-forms.md)印刷時に表示されます。 このコントロールには、ボタンやその他のユーザー インターフェイスの要素がないため、通常は、独自の印刷プレビューのユーザー インターフェイスを作成する場合にのみ <xref:System.Windows.Forms.PrintPreviewControl> を使用します。 標準のユーザー インターフェイスを実行する場合に、使用、<xref:System.Windows.Forms.PrintPreviewDialog>制御; を参照してください[PrintPreviewDialog コントロールの概要](printpreviewdialog-control-overview-windows-forms.md)の概要について説明します。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールのキー プロパティは、<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>をプレビューするドキュメントを設定します。 ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。 印刷するドキュメントの作成の概要については、次を参照してください。 [PrintDocument コンポーネントの概要](printdocument-component-overview-windows-forms.md)と[Windows フォームにおける印刷のサポート](../advanced/windows-forms-print-support.md)します。 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティは、コントロールの水平および垂直を表示するページの数を決定します。 アンチエイリアシングをテキストが滑らかに使用するが、低速です。 表示することもできますが、これを使用する設定、<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>プロパティを`true`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog コントロールの概要](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl コントロール](printpreviewcontrol-control-windows-forms.md)
- [ダイアログ ボックス コントロールおよびコンポーネント](dialog-box-controls-and-components-windows-forms.md)
