---
title: DomainUpDown コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: bfe3e7239f77c6f1a0d9bb46a96c704653b43364
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102857"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールが本質的には、テキスト ボックスの組み合わせで、一覧内を上下に移動するボタンのペア。 コントロールは、表示し、選択肢の一覧からテキスト文字列を設定します。 ユーザーは、一覧内を移動するボタンと下矢印をクリックすると、上下の矢印キーを押して、または、リスト内の項目に一致する文字列を入力して、文字列を選択できます。 このコントロールの用途の 1 つは、名のアルファベット順に並べ替えられたリストから項目を選択するためです。  
  
> [!NOTE]
>  一覧を並べ替えるには、設定、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティを`true`します。  
  
 このコントロールの機能は、リスト ボックスまたはコンボ ボックスによく似ていますが、非常に小さい領域を占めます。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールのプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>します。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティに文字列値を持つが、コントロールに表示されるオブジェクトの一覧が含まれています。 場合<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>に設定されている`false`コントロールは、ユーザーが型し、リスト内の値に一致するテキストを自動的に完了します。 場合<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>に設定されている`true`、過去の最後の項目スクロールをクリックすると、最初の項目の一覧で、またはその逆です。 コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>します。  
  
 このコントロールには、テキスト文字列のみが表示されます。 数値の値を表示するコントロールを実行する場合に、使用、<xref:System.Windows.Forms.NumericUpDown>コントロール。 詳細については、次を参照してください。 [NumericUpDown コントロールの概要](numericupdown-control-overview-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown コントロール](domainupdown-control-windows-forms.md)
