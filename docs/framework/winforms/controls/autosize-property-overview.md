---
title: AutoSize プロパティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: 6d5c4a22f186ddc5811c4a4d5e79776decea9e50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954298"
---
# <a name="autosize-property-overview"></a>AutoSize プロパティの概要
<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティによって指定された値を取得するために必要な場合は、そのサイズを変更するコントロールを使用する、<xref:System.Windows.Forms.Control.PreferredSize%2A>プロパティ。 設定して、特定のコントロールのサイズ変更動作を調整する、`AutoSizeMode`プロパティ。  
  
## <a name="autosize-behavior"></a>AutoSize 動作  
 一部のコントロールのみをサポート、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。 さらに、一部のコントロールをサポートする、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティをサポートしても、`AutoSizeMode`プロパティ。  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A>プロパティは、特定のコントロール型との値によって、若干異なる動作を生成、`AutoSizeMode`プロパティが存在する場合は、プロパティ。 次の表では、常に有効な動作について説明し、それぞれの簡単な説明を提供します。  
  
|常に真の動作|説明|  
|--------------------------|-----------------|  
|自動サイズ変更、実行時の機能です。|つまり、ことはありません拡大または縮小のコントロールとし、それ以上の効果がありません。|  
|コントロールの値のサイズが変更された場合、<xref:System.Windows.Forms.Control.Location%2A>プロパティは常に定数です。|コントロールの内容が拡大、右方向と下方向に、コントロールが大きくなります。 コントロールは、左側には拡張されません。|  
|<xref:System.Windows.Forms.Control.Dock%2A>と<xref:System.Windows.Forms.Control.Anchor%2A>プロパティがときに受け入れられます<xref:System.Windows.Forms.Control.AutoSize%2A>は`true`します。|コントロールの値<xref:System.Windows.Forms.Control.Location%2A>プロパティは、適切な値に調整されます。<br /><br /> **注**、<xref:System.Windows.Forms.Label>コントロールがこの規則の例外。 ドッキングされた値を設定すると<xref:System.Windows.Forms.Label>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`、<xref:System.Windows.Forms.Label>コントロールは変化しません。|  
|コントロールの<xref:System.Windows.Forms.Control.MaximumSize%2A>と<xref:System.Windows.Forms.Control.MinimumSize%2A>プロパティは常に受け入れの値に関係なくその<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。|<xref:System.Windows.Forms.Control.MaximumSize%2A>と<xref:System.Windows.Forms.Control.MinimumSize%2A>プロパティを受けないこと、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。|  
|既定で設定される最小サイズはありません。|つまり、コントロールの下の圧縮が設定されている場合<xref:System.Windows.Forms.Control.AutoSize%2A>内容の値を持たないとその<xref:System.Windows.Forms.Control.Size%2A>プロパティは、0, 0。 ここでは、コントロールは、ポイントに圧縮し、すぐに表示されません。|  
|コントロールが実装していない場合、<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッド、<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッドに割り当てられている最後の値を返します、<xref:System.Windows.Forms.Control.Size%2A>プロパティ。|つまり、その設定<xref:System.Windows.Forms.Control.AutoSize%2A>に`true`効果はありません。|  
|内のコントロール、<xref:System.Windows.Forms.TableLayoutPanel>セルまでのセルに収まるように縮小では常にその<xref:System.Windows.Forms.Control.MinimumSize%2A>に到達します。|このサイズは、最大サイズとして適用されます。 これには、セルの一部であるときに、大文字と小文字ではありません、<xref:System.Windows.Forms.SizeType.AutoSize>行または列。|  
  
## <a name="autosizemode-property"></a>AutoSizeMode プロパティ  
 `AutoSizeMode`プロパティは、既定のきめの細かい制御を提供します。<xref:System.Windows.Forms.Control.AutoSize%2A>動作します。 `AutoSizeMode`プロパティは、どのようにそのコンテンツへのコントロール サイズ自体を指定します。 コンテンツはなどのテキストをする可能性があります、<xref:System.Windows.Forms.Button>コントロールまたはコンテナーの子コントロール。  
  
 次の表は、<xref:System.Windows.Forms.AutoSizeMode>設定と動作の説明をそれぞれの設定を引き起こします。  
  
|AutoSizeMode 設定|動作|  
|--------------------------|--------------|  
|GrowAndShrink|コントロールは、拡大または縮小の内容を囲むようにします。<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A>と<xref:System.Windows.Forms.Control.MaximumSize%2A>の現在の値が、値が受け入れられます、<xref:System.Windows.Forms.Control.Size%2A>プロパティは無視されます。<br /><br /> これは、同じ動作をコントロールとして、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティと いいえ`AutoSizeMode`プロパティ。|  
|GrowOnly|コントロールのその内容を囲むように必要に応じて拡大します、はによって指定された値未満に圧縮されません、<xref:System.Windows.Forms.Control.Size%2A>プロパティ。<br /><br /> これは、`AutoSizeMode` の既定値です。|  
  
## <a name="controls-that-support-the-autosize-property"></a>AutoSize プロパティをサポートするコントロール  
 次の表に、サポートするコントロール、<xref:System.Windows.Forms.Control.AutoSize%2A>と`AutoSizeMode`プロパティ。  
  
|自動サイズ調整のサポート|コントロール型|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティがサポートされています。<br />-いいえ`AutoSizeMode`プロパティ。|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox>ベース)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティがサポートされています。<br />-   `AutoSizeMode` プロパティがサポートされています。|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-いいえ<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティ。|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>デザイン環境での自動サイズ調整  
 次の表からの値に基づいて、デザイン時にコントロールのサイズ変更動作が説明その<xref:System.Windows.Forms.Control.AutoSize%2A>と`AutoSizeMode`プロパティ。  
  
 上書き、<xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A>プロパティを特定のコントロールがユーザー サイズ変更可能な状態かどうかを判断します。 次の表では、「できない」ことを意味<xref:System.Windows.Forms.Design.SelectionRules.Moveable>のみ、「できる」ことを意味<xref:System.Windows.Forms.Design.SelectionRules.AllSizeable>と<xref:System.Windows.Forms.Design.SelectionRules.Moveable>します。  
  
|自動サイズ調整の設定|デザイン時のサイズ変更のジェスチャ|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-いいえ`AutoSizeMode`プロパティ。|ユーザーは、次のコントロールを除く、デザイン時にコントロールのサイズを変更ことはできません。<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|ユーザーは、デザイン時にコントロールのサイズを変更できません。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|ユーザーは、デザイン時にコントロールのサイズを変更できます。 ときに、<xref:System.Windows.Forms.Control.Size%2A>プロパティが設定されており、ユーザーは、コントロールのサイズを増加のみ実行できます。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`、または<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを非表示にします。|ユーザーは、デザイン時にコントロールのサイズを変更できます。|  
  
> [!NOTE]
>  Windows フォーム デザイナーの影の生産性を最大化する、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを<xref:System.Windows.Forms.Form>クラス。 デザイン時に、フォームにいなくても動作、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティに設定されて`false`その実際の設定に関係なく、します。 時に、特別な宿泊施設は行われません、および<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティが適用されるプロパティの設定で指定されました。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.PreferredSize%2A>
- <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
