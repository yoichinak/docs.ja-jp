---
title: DomainUpDown コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704537"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown コントロール (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールのようを組み合わせたテキスト ボックスとボタンのペアのリストを上下に移動します。 コントロールは、表示し、選択肢の一覧からテキスト文字列を設定します。 ユーザーは、一覧内を移動するボタンと下矢印をクリックすると、上下の矢印キーを押して、または、リスト内の項目に一致する文字列を入力して、文字列を選択できます。 このコントロールの用途の 1 つは、名のアルファベット順に並べ替えられたリストから項目を選択するためです。 (一覧を並べ替えるには、設定、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティを`true`)。このコントロールの機能は、リスト ボックスまたはコンボ ボックスによく似ていますが、非常に小さい領域を占めます。  
  
 コントロールのプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>します。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティに文字列値を持つが、コントロールに表示されるオブジェクトの一覧が含まれています。 場合<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>に設定されている`false`コントロールは、ユーザーが型し、リスト内の値に一致するテキストを自動的に完了します。 場合<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>に設定されている`true`、過去の最後の項目スクロールをクリックすると、最初の項目の一覧で、またはその逆です。 コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>します。  
  
 このコントロールには、テキスト文字列のみが表示されます。 数値の値を表示するコントロールを実行する場合に、使用、<xref:System.Windows.Forms.NumericUpDown>コントロール。 詳細については、次を参照してください。 [NumericUpDown コントロール](numericupdown-control-windows-forms.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DomainUpDown コントロールの概要](domainupdown-control-overview-windows-forms.md)  
 一般的な概念が導入されています、<xref:System.Windows.Forms.DomainUpDown>コントロールを参照し、テキスト文字列の一覧から選択することができます。  
  
 [方法: プログラムで Windows フォーム DomainUpDown コントロールに項目を追加します。](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 テキスト文字列を指定する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コントロールを表示する必要があります。  
  
 [方法: Windows フォーム DomainUpDown コントロールから項目を削除します。](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 項目を削除する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コード内でコントロールできます。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.DomainUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクがあります.  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)  
 Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。
