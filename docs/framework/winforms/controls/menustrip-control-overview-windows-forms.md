---
title: MenuStrip コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b72fcf75aeebc297d09cbaa9dbf00bb2370b1222
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625764"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip コントロールの概要 (Windows フォーム)
メニューは、共通のテーマでグループ化されているコマンドを保持して、ユーザーに機能を公開します。  
  
 <xref:System.Windows.Forms.MenuStrip>コントロールはこのバージョンの Visual Studio および .NET Framework で新しく導入されます。 コントロールで、Microsoft Office で見られるようなメニューを簡単に作成することができます。  
  
 <xref:System.Windows.Forms.MenuStrip>マルチ ドキュメント インターフェイス (MDI) とメニューのマージ、ツール ヒント、およびオーバーフロー コントロールをサポートしています。 アクセス キー、ショートカット キー、チェック マーク、イメージ、および区分線を追加することで、メニューの読みやすさと使いやすさを強化できます。  
  
 <xref:System.Windows.Forms.MenuStrip>コントロールが置換および機能を追加、<xref:System.Windows.Forms.MainMenu>制御します。 ただし、、<xref:System.Windows.Forms.MainMenu>を選択した場合、下位互換性と将来の使用のコントロールは保持されます。  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip コントロールを使用する方法  
 使用して、<xref:System.Windows.Forms.MenuStrip>を制御します。  
  
- 簡単にカスタマイズされた作成をサポートする、一般的に使用されるメニューなどの拡張ユーザー インターフェイスとレイアウト機能、テキストとイメージの並べ替えとアラインメント、ドラッグ アンド ドロップ操作、MDI、オーバーフロー、およびメニュー コマンドにアクセスするのに代替のモード。  
  
- オペレーティング システムの動作と標準的な外観をサポートします。  
  
- 同様に他のコントロールのイベントを処理するには、すべてのコンテナーと含まれる項目を一貫してイベントを処理します。  
  
 次の表には、いくつか特に重要なプロパティが表示されます。<xref:System.Windows.Forms.MenuStrip>および関連するクラス。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|取得または設定します、 <xref:System.Windows.Forms.ToolStripMenuItem> MDI 子フォームの一覧を表示するために使用されます。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|取得または子メニューが MDI アプリケーションで親メニューにマージされる方法を設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|取得または MDI アプリケーションでメニュー内でマージされた項目の位置を設定します。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|取得またはフォームが MDI 子フォームのコンテナーであるかどうかを示す値を設定します。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|取得または設定のツール ヒントを表示するかどうかを示す値、<xref:System.Windows.Forms.MenuStrip>します。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<xref:System.Windows.Forms.MenuStrip> がオーバーフロー機能をサポートするかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|取得または設定に関連付けられているショートカット キー、<xref:System.Windows.Forms.ToolStripMenuItem>します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|関連付けられたショートカット キーをかどうかを示す値を取得または設定、<xref:System.Windows.Forms.ToolStripMenuItem>横に表示する、<xref:System.Windows.Forms.ToolStripMenuItem>します。|  
  
 次の表は、重要な<xref:System.Windows.Forms.MenuStrip>コンパニオン クラス。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|表示される選択可能なオプションを表す、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ContextMenuStrip>します。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|ショートカット メニューを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|ユーザーは、ユーザーがクリックしたときに表示される一覧から 1 つの項目を選択できるようにするコントロール表します、<xref:System.Windows.Forms.ToolStripDropDownButton>または上位レベルのメニュー項目。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|派生したコントロールの基本的な機能を提供します<xref:System.Windows.Forms.ToolStripItem>クリックされたときにドロップダウン リストの項目を表示します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
