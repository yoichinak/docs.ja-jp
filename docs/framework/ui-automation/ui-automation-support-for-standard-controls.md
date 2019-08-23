---
title: UI オートメーションによる標準コントロールのサポート
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914225"
---
# <a name="ui-automation-support-for-standard-controls"></a>UI オートメーションによる標準コントロールのサポート
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]、および [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]フレームワーク向けに開発されたアプリケーションの標準コントロールに対する [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] サポートについて説明します。  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation コントロール  
 ユーザー操作に関する情報やサポートを提供するすべての [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロール要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を全面的にネイティブ サポートしています。 パネルなどのその他の要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]からは認識できません。  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Win32 コントロール  
 ほとんどの [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] コントロールは、UIAutomationClientsideProviders.dll のクライアント側プロバイダーによって [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] に公開されています。 このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。  
  
 完全なサポートは、ComCtrl32.dll のバージョン 6 ( [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] 以降で使用可能) のコントロールに対してのみ提供されています。  
  
 次のコントロールがサポートされています。  
  
|クラス名|コントロール型|  
|----------------|------------------|  
|ボタン|ボタン|  
|ボタン|RadioButton|  
|ボタン|グループ化|  
|ボタン|CheckBox|  
|ボタン|ハイパーリンク|  
|ボタン|SplitButton|  
|ボタン|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|編集|ドキュメント|  
|編集|編集|  
|SysLink|ハイパーリンク|  
|スタティック|テキスト|  
|スタティック|イメージ|  
|SysIPAddress32|カスタム|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|List|  
|ListBox|List|  
|ListBox|ListItem|  
|#32768|メニュー|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|ドキュメント。 注を参照。|  
|RichEdit20A|ドキュメント|  
|RichEdit20W|ドキュメント|  
|RichEdit50W|ドキュメント|  
|ScrollBar|スライダー|  
|msctls_trackbar32|スライダー|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|ボタン|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|区切り記号|  
|tooltips_class32|ヒント|  
|#32774|ヒント|  
|ReBarWindow32|ツール バー|  
|SysTreeView32|ツリー|  
|SysTreeView32|TreeItem|  
  
 **注** RichEdit コントロールは、 [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] に付属するバージョン (RichEd20.dll バージョン 3.1 以降、および MsftEdit.dll バージョン 4.1 以降) に対してのみサポートされます。  
  
 次のコントロールはサポートされていません。  
  
|クラス名|コントロール型|  
|----------------|------------------|  
|SysAnimate32|イメージ|  
|SysPager|Spinner|  
|SysDateTimePick32|カスタム|  
|SysMonthCal32|予定表|  
|MS_WINNOTE|ヒント|  
|VBBubble|ヒント|  
|ScrollBar (スタンドアロン コントロールとして使用される場合)|スライダー|  
|SuperGrid|カスタム|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Windows フォーム コントロール  
 Windows フォームコントロールは、、uiautomationclientsideproviders.dll [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]のクライアント側プロバイダーを介してに公開されます。 このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。  
  
 通常、コモンコントロールの[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]マネージラッパーである Windows フォームコントロールは、で[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]サポートされています。 次のコントロールがサポートされています。  
  
|クラス名|  
|----------------|  
|ボタン|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|group1|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|タイマー|  
|ToolBar|  
|ヒント|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Web ブラウザー|  
  
 次のコントロールは、Microsoft [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Active Accessibility のサポートを通じてのみに公開されます。 一部の機能が使用できないことがあります。  
  
|コントロール名|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|フォーム|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|パネル|  
|PictureBox|  
|PrintDocument|  
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|スプリッター|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール型](../../../docs/framework/ui-automation/ui-automation-control-types.md)
