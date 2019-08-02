---
title: MenuStrip コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733455"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip コントロールの概要 (Windows フォーム)
メニューは、共通のテーマによってグループ化されたコマンドを保持することによって、ユーザーに機能を公開します。  
  
 コントロール<xref:System.Windows.Forms.MenuStrip>は、.NET Framework のバージョン2.0 で導入されました。 <xref:System.Windows.Forms.MenuStrip>コントロールを使用すると、Microsoft Office にあるようなメニューを簡単に作成できます。  
  
 コントロール<xref:System.Windows.Forms.MenuStrip>では、マルチドキュメントインターフェイス (MDI) とメニューのマージ、ツールヒント、およびオーバーフローがサポートされています。 アクセスキー、ショートカットキー、チェックマーク、画像、および区分線を追加することで、メニューの使いやすさと読みやすさを向上させることができます。  
  
 コントロールは、コントロール<xref:System.Windows.Forms.MainMenu>に置き換えられ、機能が追加さ<xref:System.Windows.Forms.MainMenu>れます。ただし、コントロールは旧バージョンとの互換性を維持するために残されています。 <xref:System.Windows.Forms.MenuStrip>  
  
## <a name="ways-to-use-the-menustrip-control"></a>MenuStrip コントロールを使用する方法  
 コントロールを<xref:System.Windows.Forms.MenuStrip>使用して次の操作を行います。  
  
- テキストとイメージの順序付けと配置、ドラッグアンドドロップ操作、MDI、オーバーフロー、メニューコマンドにアクセスするための代替モードなど、高度なユーザーインターフェイスとレイアウト機能をサポートする、カスタマイズされた、一般的に使用されるメニューを作成します。  
  
- オペレーティングシステムの一般的な外観と動作をサポートします。  
  
- 他のコントロールのイベントを処理するのと同じ方法で、すべてのコンテナーと含まれる項目に対して一貫したイベントを処理します。  
  
 次の表は、および関連クラスの<xref:System.Windows.Forms.MenuStrip>いくつかの重要なプロパティを示しています。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|MDI 子フォームの<xref:System.Windows.Forms.ToolStripMenuItem>一覧を表示するために使用されるを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|MDI アプリケーションの親メニューと子メニューをマージする方法を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|MDI アプリケーションのメニュー内のマージされた項目の位置を取得または設定します。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|フォームが MDI 子フォームのコンテナーかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|にツールヒントを表示<xref:System.Windows.Forms.MenuStrip>するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<xref:System.Windows.Forms.MenuStrip> がオーバーフロー機能をサポートするかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|に関連付けられているショートカット<xref:System.Windows.Forms.ToolStripMenuItem>キーを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|に関連付けら<xref:System.Windows.Forms.ToolStripMenuItem>れているショートカットキーをの<xref:System.Windows.Forms.ToolStripMenuItem>横に表示するかどうかを示す値を取得または設定します。|  
  
 次の表は、重要<xref:System.Windows.Forms.MenuStrip>な関連クラスを示しています。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ContextMenuStrip>に表示される選択可能なオプションを表します。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|ショートカット メニューを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|ユーザーが<xref:System.Windows.Forms.ToolStripDropDownButton>または上位レベルのメニュー項目をクリックしたときに表示される一覧から1つの項目を選択できるようにするコントロールを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|クリックしたときに表示さ<xref:System.Windows.Forms.ToolStripItem>れるドロップダウン項目から派生したコントロールの基本機能を提供します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
