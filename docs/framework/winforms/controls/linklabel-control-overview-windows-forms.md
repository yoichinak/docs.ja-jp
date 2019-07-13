---
title: LinkLabel コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 541467b0f1285d372e5f6d502d9d8f28c8c6333e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012959"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.LinkLabel>コントロールでは、Windows フォーム アプリケーションを Web スタイルのリンクを追加できます。 使用することができます、<xref:System.Windows.Forms.LinkLabel>使用できるすべてのコントロール、<xref:System.Windows.Forms.Label>の制御も設定できるは、テキストの一部として、ファイル、フォルダー、または Web ページへのリンク。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>LinkLabel コントロールで行うことができます。  
 すべてのプロパティ、メソッド、およびのイベントだけでなく、<xref:System.Windows.Forms.Label>コントロール、<xref:System.Windows.Forms.LinkLabel>コントロールのハイパーリンクとリンクの色のプロパティがあります。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティは、リンクをアクティブにするテキストの領域を設定します。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>、および<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>プロパティは、リンクの色を設定します。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>イベントは、リンクのテキストが選択されているときの動作を決定します。  
  
 最も簡単な使用、<xref:System.Windows.Forms.LinkLabel>コントロールを使用して、1 つのリンクを表示する、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティがすることができますを使用して複数のハイパーリンクを表示も、<xref:System.Windows.Forms.LinkLabel.Links%2A>プロパティ。 <xref:System.Windows.Forms.LinkLabel.Links%2A>プロパティでは、リンクのコレクションにアクセスすることができます。 内のデータを指定することも、<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>プロパティをそれぞれ個別<xref:System.Windows.Forms.LinkLabel.Link>オブジェクト。 値、<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>プロパティを表示するファイルの場所または Web サイトのアドレスの格納に使用できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.LinkLabel>
- [Label コントロールの概要](label-control-overview-windows-forms.md)
- [方法: オブジェクトへのリンクまたは Web ページと Windows フォーム LinkLabel コントロール](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [方法: Windows フォーム LinkLabel コントロールの外観を変更します。](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
