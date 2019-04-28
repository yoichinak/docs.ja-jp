---
title: Windows フォームの MenuStrip コントロールへのメニュー項目のマージ
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: dbe1c0325499e7b925d504fc80f9034f9e387475
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936358"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Windows フォームの MenuStrip コントロールへのメニュー項目のマージ
マルチ ドキュメント インターフェイス (MDI) アプリケーションがある場合は、親フォームのメニューにメニュー項目や子フォームの全体のメニューをマージできます。  
  
 このトピックでは、MDI アプリケーションでメニュー項目のマージに関連付けられている基本的な概念について説明します。  
  
## <a name="general-concepts"></a>一般的な概念  
 マージ手順には、ターゲットとソース管理の両方が含まれます。  
  
- ターゲットが、<xref:System.Windows.Forms.MenuStrip>メニュー項目のマージ先のメインまたは MDI 親フォームのコントロール。  
  
- ソースが、 <xref:System.Windows.Forms.MenuStrip> [ターゲット] メニューにマージするメニュー項目を含む MDI 子フォームのコントロール。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティは、現在の MDI のタイトルが表示されます - ドロップダウン リストを持つ親フォームの MDI 子メニュー項目を識別します。 現在開いている MDI 子フォームを通常に一覧表示など、**ウィンドウ**メニュー。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A>からメニュー項目を取得するプロパティを識別、<xref:System.Windows.Forms.MenuStrip>の MDI 子フォーム。  
  
 メニュー項目は、手動または自動マージできます。 両方のメソッドに対して同じ方法でのメニュー項目のマージが、マージが「手動マージ」と「自動マージ」セクションでは、このトピックの後半で説明したように、異なるアクティブ化します。 手動および自動マージの各マージ操作は、[次へ] のマージ操作に影響します。  
  
 <xref:System.Windows.Forms.MenuStrip> 1 つのメニュー アイテムを移動するマージ<xref:System.Windows.Forms.ToolStrip>を別の場合と同様に、複製ではなく<xref:System.Windows.Forms.MainMenu>します。  
  
## <a name="mergeaction-values"></a>MergeAction 値  
 ソースのメニュー項目にマージ操作を設定する<xref:System.Windows.Forms.MenuStrip>を使用して、<xref:System.Windows.Forms.MergeAction>プロパティ。  
  
 次の表では、使用できるマージ処理の意味と一般的な使用について説明します。  
  
|MergeAction 値|説明|一般的な用途|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(既定値)ターゲット項目のコレクションの末尾には、元の項目を追加します。|プログラムの一部がアクティブになると、メニューの末尾にメニュー項目を追加します。|  
|<xref:System.Windows.Forms.MergeAction.Insert>|指定された場所では、ターゲット項目のコレクションに元の項目を追加、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>ソース アイテムのプロパティで設定します。|プログラムの一部がアクティブの場合は、中間またはメニューの先頭にメニュー項目を追加します。<br /><br /> 場合の値<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>は両方のメニュー項目を追加する逆の順序で。 設定<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>適切に元の順序を保持します。|  
|<xref:System.Windows.Forms.MergeAction.Replace>|一致するテキストを検索またはを使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>値の場合、テキスト一致するものが検出され、一致する対象のメニュー項目をソースのメニュー項目に置き換えます。|ターゲットのメニュー項目を別の処理を実行するのと同じ名前のソースのメニュー項目に置き換えます。|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|一致するテキストを検索またはを使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>値の場合、テキスト一致するものが検出され、元のドロップダウン リストのすべての項目をターゲットに追加します。|メニュー構造を構築挿入またはサブメニューの場合にメニュー項目を追加またはサブメニューのメニュー項目を削除します。 主に、MDI 子からメニュー項目を追加するなど、 <xref:System.Windows.Forms.MenuStrip>**名前を付けて保存**メニュー。<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> 操作を行わずにメニュー構造をナビゲートすることができます。 それ以降の項目を評価する方法を提供します。|  
|<xref:System.Windows.Forms.MergeAction.Remove>|一致するテキストを検索またはを使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>値の場合、テキスト一致するものが検出され、ターゲットから項目を削除します。|ターゲットからメニュー項目を削除する<xref:System.Windows.Forms.MenuStrip>します。|  
  
## <a name="manual-merging"></a>手動マージ  
 のみ<xref:System.Windows.Forms.MenuStrip>コントロールが自動マージに参加します。 などの他のコントロールの項目を組み合わせて<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.StatusStrip>コントロール、する必要があります手動でマージを呼び出すことによって、<xref:System.Windows.Forms.ToolStripManager.Merge%2A>と<xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A>必要に応じて、コード内のメソッド。  
  
## <a name="automatic-merging"></a>自動マージ  
 ソース形式をアクティブ化して、MDI アプリケーションの自動マージを使用することができます。 使用する、 <xref:System.Windows.Forms.MenuStrip> MDI アプリケーションでは、次のように設定します。、<xref:System.Windows.Forms.Form.MainMenuStrip%2A>プロパティ、ターゲットを<xref:System.Windows.Forms.MenuStrip>ソースに対して実行するアクションをマージできるように<xref:System.Windows.Forms.MenuStrip>ターゲットに反映されます<xref:System.Windows.Forms.MenuStrip>します。  
  
 アクティブ化して自動マージをトリガーすることができます、 <xref:System.Windows.Forms.MenuStrip> MDI ソース。 ソースの起動時に<xref:System.Windows.Forms.MenuStrip>MDI ターゲットにマージされます。 新しいフォームがアクティブになったときに、マージが最後のフォームで元に戻すで、新しいフォームにトリガーします。 設定してこの動作を制御することができます、<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>プロパティそれぞれで、必要に応じて<xref:System.Windows.Forms.ToolStripItem>を設定したり、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>プロパティをそれぞれ<xref:System.Windows.Forms.MenuStrip>。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip コントロール](menustrip-control-windows-forms.md)
- [方法: MenuStrip を MDI ウィンドウ リストを作成します。](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [方法: メニューの自動マージ MDI アプリケーションを設定します。](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
