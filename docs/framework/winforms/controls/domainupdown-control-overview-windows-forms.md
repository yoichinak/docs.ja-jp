---
title: DomainUpDown コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965301"
---
# <a name="domainupdown-control-overview-windows-forms"></a>DomainUpDown コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールは、基本的には、テキストボックスと、リストを上または下に移動するためのボタンの組み合わせで構成されます。 コントロールは、選択肢の一覧からテキスト文字列を表示して設定します。 ユーザーは上下のボタンをクリックして一覧内を移動し、上下の方向キーを押すか、リスト内の項目に一致する文字列を入力することで、文字列を選択できます。 このコントロールの1つの使用方法は、アルファベット順に並べ替えられた名前のリストから項目を選択することです。  
  
> [!NOTE]
> リストを並べ替えるには、 <xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティをに`true`設定します。  
  
 このコントロールの機能は、リストボックスまたはコンボボックスとよく似ていますが、スペースが非常に小さくなります。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールの主要なプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>です。 プロパティ<xref:System.Windows.Forms.DomainUpDown.Items%2A>は、テキスト値がコントロールに表示されるオブジェクトのリストを格納します。 が<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> に`false`設定されている場合、コントロールは、ユーザーが入力してリスト内の値と照合するテキストを自動的に完了します。 が<xref:System.Windows.Forms.DomainUpDown.Wrap%2A> に`true`設定されている場合、最後の項目を超えてスクロールすると、リストの最初の項目に移動します。逆の場合も同様です。 コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>です。  
  
 このコントロールは、テキスト文字列のみを表示します。 数値を表示するコントロールが必要な場合は、 <xref:System.Windows.Forms.NumericUpDown>コントロールを使用します。 詳細については、「 [NumericUpDown Control の概要](numericupdown-control-overview-windows-forms.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DomainUpDown>
- [DomainUpDown コントロール](domainupdown-control-windows-forms.md)
