---
title: CheckBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 2a18327d9836d1dbbcd5d5d6e73f217637736d20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121794"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.CheckBox> コントロールは、特定の条件がオンかオフかを示します。 一般的に、はい/いいえ、または True/False の選択肢をユーザーに提示するために使用されます。 ユーザーが 1 つ以上選択可能な複数の選択肢を表示するために、チェック ボックス コントロールをグループの中で使用できます。  
  
 チェック ボックス コントロールは、各ユーザーによって行われた選択範囲を示すために使用がそのラジオ ボタン コントロールに似ています。 これらとはそのグループ内の 1 つだけのラジオ ボタンを一度に選択できます。 チェック ボックス コントロールで、ただし、任意の数のチェック ボックスを選択できます。  
  
 チェック ボックスは、単純データ バインディングを使用してデータベース内の要素に接続することがあります。 複数のチェック ボックスを使用してグループ化する可能性があります、<xref:System.Windows.Forms.GroupBox>コントロール。 これは、機能は、グループ化されたコントロールの周囲をまとめて移動して、フォーム デザイナーであるため視覚的な外観とユーザー インターフェイスのデザインに便利です。 詳細については、次を参照してください。 [Windows フォーム データ バインディング](../windows-forms-data-binding.md)と[GroupBox コントロール](groupbox-control-windows-forms.md)します。  
  
 <xref:System.Windows.Forms.CheckBox>コントロールに 2 つの重要なプロパティがある<xref:System.Windows.Forms.CheckBox.Checked%2A>と<xref:System.Windows.Forms.CheckBox.CheckState%2A>します。 <xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティは、どちらかを返します`true`または`false`します。 <xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティは、どちらかを返します<xref:System.Windows.Forms.CheckState.Checked>または<xref:System.Windows.Forms.CheckState.Unchecked>; 場合、<xref:System.Windows.Forms.CheckBox.ThreeState%2A>プロパティに設定されて`true`、<xref:System.Windows.Forms.CheckBox.CheckState%2A>を返すことも<xref:System.Windows.Forms.CheckState.Indeterminate>します。 中間の状態で淡色表示を示す、オプションは使用できません、ボックスが表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.CheckBox>
- [方法: Windows フォームの CheckBox コントロールでオプションを設定します。](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [方法: Windows フォーム CheckBox のクリックに応答します。](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox コントロール](checkbox-control-windows-forms.md)
