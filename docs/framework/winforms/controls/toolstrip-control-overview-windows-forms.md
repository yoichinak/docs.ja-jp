---
title: ToolStrip コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3e532b040d3c7859220b7f73958b63e7208b988c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009527"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ToolStrip>コントロールとその関連クラスは、ツールバー、ステータス バー、およびメニューにユーザー インターフェイス要素を結合するため、共通のフレームワークを提供します。 <xref:System.Windows.Forms.ToolStrip> コントロールでは、水平または垂直スペースを共有するツールバーの機能は、インプレース アクティブ化と編集、カスタム レイアウト、およびラフティング、豊富なデザイン時エクスペリエンスを提供します。  
  
 <xref:System.Windows.Forms.ToolStrip>が置換および以前のバージョンで制御する機能を追加<xref:System.Windows.Forms.ToolBar>必要な場合に、旧バージョンとの互換性と将来の使用のため保持されます。  
  
## <a name="features-of-the-toolstrip-controls"></a>ToolStrip コントロールの機能  
 使用して、<xref:System.Windows.Forms.ToolStrip>を制御します。  
  
- コンテナー間には、一般的なユーザー インターフェイスを提供します。  
  
- 簡単にカスタマイズされた作成、サポートするツールバーが一般的に使用されるユーザー インターフェイスとレイアウトの機能の詳細などのテキストとイメージ、ドロップダウン ボタン、およびコントロールのドッキング、ラフティング、ボタン、オーバーフロー ボタン、および実行時の並べ替えの<xref:System.Windows.Forms.ToolStrip>項目。  
  
- オーバーフローおよび実行時の項目の並べ替えをサポートします。 オーバーフロー機能がでそれらを表示する十分な空き領域がない場合に、ドロップダウン メニューに項目を移動、<xref:System.Windows.Forms.ToolStrip>します。  
  
- 標準的な外観と動作の一般的なレンダリング モデルにより、オペレーティング システムをサポートします。  
  
- 同様に他のコントロールのイベントを処理するには、すべてのコンテナーと含まれる項目を一貫してイベントを処理します。  
  
- いずれかから項目をドラッグ<xref:System.Windows.Forms.ToolStrip>別、または、<xref:System.Windows.Forms.ToolStrip>します。  
  
- ドロップダウン コントロールとユーザー インターフェイス型エディターを高度なレイアウトを作成、<xref:System.Windows.Forms.ToolStripDropDown>します。  
  
 使用して、<xref:System.Windows.Forms.ToolStripControlHost>クラスを他のコントロールを使用して、<xref:System.Windows.Forms.ToolStrip>行い、<xref:System.Windows.Forms.ToolStrip>それらの機能です。  
  
 機能を拡張しを使用して外観と動作を変更することができます、 <xref:System.Windows.Forms.ToolStripRenderer>、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、および<xref:System.Windows.Forms.ToolStripManager>と共に、<xref:System.Windows.Forms.ToolStripRenderMode>と<xref:System.Windows.Forms.ToolStripManagerRenderMode>列挙体。  
  
 <xref:System.Windows.Forms.ToolStrip>コントロール、構成可能かつ拡張可能なおよび多くのプロパティ、メソッド、および外観と動作をカスタマイズするイベントを提供します。 いくつかの重要なメンバーを次に示します。  
  
### <a name="important-toolstrip-members"></a>ToolStrip の重要なメンバー  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|取得または設定の親コンテナーの端を<xref:System.Windows.Forms.ToolStrip>にドッキングされます。|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<xref:System.Windows.Forms.ToolStrip> クラスがドラッグ アンド ドロップおよび項目の並べ替えをプライベートで処理するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|取得または設定を示す値が、どのように<xref:System.Windows.Forms.ToolStrip>その項目のレイアウトします。|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|取得または設定するかどうかを<xref:System.Windows.Forms.ToolStripItem>にアタッチされて、<xref:System.Windows.Forms.ToolStrip>または<xref:System.Windows.Forms.ToolStripOverflowButton>2 つの間で変動するか。|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|示す値を取得するかどうか、<xref:System.Windows.Forms.ToolStripItem>ドロップダウンからその他の項目を表示するときに、<xref:System.Windows.Forms.ToolStripItem>がクリックされました。|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|オーバーフローが有効な <xref:System.Windows.Forms.ToolStripItem> のオーバーフロー ボタンである <xref:System.Windows.Forms.ToolStrip> を取得します。|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|取得または設定します、<xref:System.Windows.Forms.ToolStripRenderer>の動作 (ルック アンド フィール) と外観をカスタマイズするために使用する<xref:System.Windows.Forms.ToolStrip>します。|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|取得または設定に適用される描画スタイル、<xref:System.Windows.Forms.ToolStrip>します。|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<xref:System.Windows.Forms.ToolStrip.Renderer%2A> プロパティが変更されたときに発生します。|  
  
 <xref:System.Windows.Forms.ToolStrip>コントロールの柔軟性は、多数のコンパニオン クラスを使用して実現されます。 最も注目に値するの一部を次に示します。  
  
### <a name="important-toolstrip-companion-classes"></a>ToolStrip の重要なコンパニオン クラス  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|置換および追加する機能、<xref:System.Windows.Forms.MainMenu>クラス。|  
|<xref:System.Windows.Forms.StatusStrip>|置換および追加する機能、<xref:System.Windows.Forms.StatusBar>クラス。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|置換および追加する機能、<xref:System.Windows.Forms.ContextMenu>クラス。|  
|<xref:System.Windows.Forms.ToolStripItem>|すべての要素のイベントおよびレイアウトを管理する基本クラスを抽象化する、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripControlHost>、または<xref:System.Windows.Forms.ToolStripDropDown>含めることができます。|  
|<xref:System.Windows.Forms.ToolStripContainer>|さまざまな方法でコントロールを配置するフォームの両側のパネルには、コンテナーを提供します。|  
|<xref:System.Windows.Forms.ToolStripRenderer>|描画機能を処理<xref:System.Windows.Forms.ToolStrip>オブジェクト。|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Microsoft Office スタイルの外観を提供します。|  
|<xref:System.Windows.Forms.ToolStripManager>|コントロール<xref:System.Windows.Forms.ToolStrip>レンダリングとラフティングとのマージ<xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、および<xref:System.Windows.Forms.ToolStripMenuItem>オブジェクト。|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|指定の倍数に適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional)<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|いずれかに適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional) を指定します<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。|  
|<xref:System.Windows.Forms.ToolStripControlHost>|具体的にはないその他のコントロールをホスト<xref:System.Windows.Forms.ToolStrip>コントロールを決定するが、<xref:System.Windows.Forms.ToolStrip>機能します。|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|指定するかどうかを<xref:System.Windows.Forms.ToolStripItem>、メイン レイアウトするのには、 <xref:System.Windows.Forms.ToolStrip>、オーバーフローに<xref:System.Windows.Forms.ToolStrip>、またはどちらもします。|  
  
 詳細については、次を参照してください。 [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)と[ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
