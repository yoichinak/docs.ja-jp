---
title: .NET Framework のアクセシビリティの新機能
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bdb1bf5d7e32c2e05eb779eed16c311cbd3eae7
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212509"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework のアクセシビリティの新機能

.NET Framework では、ユーザーのためにアプリケーションのアクセシビリティ向上を目指しています。 ユーザー補助機能により、支援機能の利用者にとってアプリケーションがさらに使いやすくなります。 .NET Framework 4.7.1 以降、.NET Framework にはさまざまなアクセシビリティ拡張機能が含まれるようになりました。それを利用することで開発者はアクセシビリティを備えたアプリケーションを開発できます。

## <a name="accessibility-switches"></a>アクセシビリティのスイッチ

アプリのターゲットが .NET Framework 4.7 である場合、またはそれより前のバージョンがターゲットであっても実行環境が .NET Framework 4.7.1 以降である場合は、ユーザー補助機能を使用するようにアプリを構成できます。 また、アプリのターゲットが 4.7.1 .NET Framework 以降である場合は、従来の機能を使用するように (そして、ユーザー補助機能を利用しないように) アプリを構成することもできます。 ユーザー補助機能が含まれる .NET Framework の各バージョンには、バージョン固有のアクセシビリティ スイッチがあります。これを、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に追加します。 サポートされているスイッチは次のとおりです。

|Version|切り替え|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>アクセシビリティ拡張機能の利用

.NET Framework 4.7.1 以降を対象とするアプリケーションでは、この新しいユーザー補助機能が既定で有効になっています。 また、それより前のバージョンの .NET Framework がターゲットであっても、実行環境が .NET Framework 4.7.1 以降であるアプリケーションの場合は、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素にスイッチを追加し、値を `false` に設定することで、古いアクセシビリティ動作を利用しないことを (そして、それにより向上したアクセシビリティ拡張機能を利用することを) 選択できます。 .NET Framework 4.7.1 で導入されたアクセシビリティの機能強化を有効にする方法を次に示します。

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

新しいバージョンの .NET Framework のユーザー補助機能を選択する場合は、古いバージョンの .NET Framework の機能も明示的に選択する必要があります。 .NET Framework 4.7.1 と 4.7.2 両方のアクセシビリティ強化機能を利用するようにアプリを構成するには、次の [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素が必要です。

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>従来の動作に戻す

アプリケーションがバージョン 4.7.1 以降の .NET Framework をターゲットにしている場合、アプリケーションの構成ファイルの [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) セクションの [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素にスイッチを追加し、値を `true` に設定することで、アクセシビリティ機能を無効にできます。 たとえば、次の構成は、.NET Framework 4.7.2 で導入されたユーザー補助機能を無効にします。

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>.NET Framework 4.7.2 のアクセシビリティの新機能

.NET Framework 4.7.2 には、次の領域の新しいアクセシビリティ機能が含まれています。

- [Windows フォーム](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows フォーム

**ハイ コントラスト テーマでの OS で定義された色**

.NET Framework 4.7.2 以降、Windows フォームは、オペレーティング システムで定義されている色をハイ コントラスト テーマで使用します。 これは、次のコントロールに影響します。

- <xref:System.Windows.Forms.ToolStripDropDownButton> コントロールのドロップダウン矢印。

- <xref:System.Windows.Forms.ButtonBase.FlatStyle> が <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> または <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> に設定された、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.RadioButton>、および <xref:System.Windows.Forms.CheckBox> コントロール。 以前は、選択されたテキストと背景の色のコントラストが同じで、見分けるのが困難でした。

- <xref:System.Windows.Forms.Control.Enabled> プロパティが `false` に設定されている <xref:System.Windows.Forms.GroupBox> に含まれるコントロール。

- <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripComboBox>、<xref:System.Windows.Forms.ToolStripDropDownButton> コントロール。これらは、ハイ コントラスト モードでの明度コントラストの比率が高くなりました。

- <xref:System.Windows.Forms.DataGridViewLinkCell> の <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> プロパティ。

**ナレーターの機能強化**

.NET Framework 4.7.2 以降では、ナレーターのサポートが次のように強化されました。

- <xref:System.Windows.Forms.ToolStripMenuItem> のテキストを読み上げるときに、<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> プロパティの値を読み上げます。

- <xref:System.Windows.Forms.ToolStripMenuItem> の <xref:System.Windows.Forms.Control.Enabled> プロパティが `false` に設定されている場合、それを示します。

- <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> プロパティが `true` に設定されているとき、チェック ボックスの状態に関するフィードバックを提供します。

- ナレーター スキャン モードのフォーカス順序が、ClickOnce ダウンロード ダイアログ ウィンドウでのコントロールの視覚的な順序と一致します。

**DataGridView の機能強化**

.NET Framework 4.7.2 以降、<xref:System.Windows.Forms.DataGridView> コントロールには次のアクセシビリティの機能強化が導入されました。

- キーボードを使って行を並べ替えることができます。 ユーザーは、F3 キーを使って現在の列で並べ替えることができます。

- <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> が <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> に設定されていると、ユーザーが現在の行のセルを Tab で移動するとき、列ヘッダーの色が変わって現在の列を示します。

- <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> の <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> プロパティは、正しい親コントロールを返します。

**視覚的な手掛かりの向上**

- <xref:System.Windows.Forms.ButtonBase.Text> プロパティが空の <xref:System.Windows.Forms.RadioButton> および <xref:System.Windows.Forms.CheckBox> コントロールは、フォーカスを受け取るとフォーカス インジケーターを表示します。

**強化されたプロパティ グリッドのサポート**

- <xref:System.Windows.Forms.PropertyGrid> コントロールの子要素は、PropertyGrid 要素が有効になっている場合にのみ、<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> プロパティに対して `true` を返すようになりました。

- <xref:System.Windows.Forms.PropertyGrid> コントロールの子要素は、PropertyGrid 要素をユーザーが変更できる場合にのみ、<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> プロパティに対して `false` を返します。

**キーボード ナビゲーションの向上**

- <xref:System.Windows.Forms.ToolStripButton> コントロールは、<xref:System.Windows.Forms.ToolStripPanel.TabStop> プロパティが `true` に設定された <xref:System.Windows.Forms.ToolStripPanel> 内に含まれているときにフォーカスできます

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**CheckBox および RadioButton コントロールに対する変更**

.NET Framework 4.7.1 およびそれより前のバージョンでは、WPF の <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> および <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> コントロールのフォーカス ビジュアルに整合性がなく、クラシック テーマとハイ コントラスト テーマでは正しくありません。  これらの問題は、コントロールに内容が何も設定されていない場合に発生します。  これにより、テーマ間の遷移が混乱し、フォーカス ビジュアルが見にくくなることがあります。

.NET Framework 4.7.2 では、これらのビジュアルのテーマ間の整合性が向上し、クラシック モードとハイ コントラスト テーマでの視認性がよくなっています。

**WPF アプリケーションでホストされる WinForms コントロール**

.NET Framework 4.7.1 以前のバージョンの WPF アプリケーションでホストされている WinForms コントロールでは、そのレイヤーの最初または最後のコントロールが WPF <xref:System.Windows.Forms.Integration.ElementHost> コントロールの場合、ユーザーは Tab キーで WinForms レイヤーから外に移動できませんでした。 .NET Framework 4.7.2 では、ユーザーは Tab キーで WinForms レイヤーから外に移動できます。

ただし、WinForms レイヤーをエスケープしないフォーカスに依存する自動化アプリケーションは、意図したように機能しなくなる可能性があります。

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 のアクセシビリティの新機能

.NET Framework 4.7.1 には、次の領域の新しいアクセシビリティ機能が含まれています。

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows フォーム](#winforms471)

- [ASP.NET Web コントロール](#aspnet471)

- [.NET SDK Tools](#tools471)

- [Windows Workflow Foundation (WF) ワークフロー デザイナー](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**スクリーン リーダーの機能強化**

アクセシビリティ拡張機能を有効にすると、.NET Framework 4.7.1 は次の面でスクリーン リーダーの機能を強化します。

- .NET Framework 4.7 以前のバージョンでは、スクリーン リーダーが <xref:System.Windows.Controls.Expander> コントロールをボタンとして読み上げました。 .NET Framework 4.7.1 以降では、展開と折りたたみが可能なグループとして正しく読み上げられます。

- .NET Framework 4.7 以前のバージョンの場合、スクリーン リーダーが <xref:System.Windows.Controls.DataGridCell> コントロールを “カスタム” として読み上げました。 .NET Framework 4.7.1 以降では、データ グリッド セル (ローカライズされます) として正しく読み上げられます。

- .NET Framework 4.7.1 以降、スクリーン リーダーは編集可能な <xref:System.Windows.Controls.ComboBox> の名前を読み上げます。

- .NET Framework 4.7 以前のバージョンの場合、<xref:System.Windows.Controls.PasswordBox> コントロールが “ビューに項目がありません” として読み上げられたか、他の誤動作が発生しました。 この問題は .NET Framework 4.7.1 以降で修正されています。

**UIAutomation LiveRegion サポート**

ナレーターなどのスクリーン リーダーはアプリケーションの UI コンテンツをユーザーのために読み上げます。通常、フォーカスを合わせた UI コンテンツのテキストが読み上げられます。 ただし、UI 要素が変わり、フォーカスがなくなったとき、ユーザーに通知されず、重要な情報を逃すことがあります。 ライブ領域は、この問題の解決を目指しています。 開発者はこれを利用し、UI 要素が大幅に変更されたことをスクリーン リーダーやその他の UIAutomation クライアントに指示できます。 指示後、スクリーン リーダーでは、その変更をユーザーに通知する方法とタイミングが決定されます。

ライブ領域をサポートするために、次の API が WPF に追加されました。

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> フィールドと <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> フィールド。**LiveSetting** プロパティと **LiveRegionChanged** イベントを識別します。 XAML を利用して設定できます。

- **AutomationProperties.LiveSetting** 添付プロパティ。UI の変化がユーザーにとって重要であることをスクリーン リーダーに伝えます。

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> プロパティ。**AutomationProperties.LiveSetting** 添付プロパティを識別します。

- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を提供するようにオーバーライドできます。

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> メソッドと <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> メソッド。**LiveSetting** 値を取得し、設定します。

- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列挙。次の指定可能 **LiveSetting** 値を定義します。

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合でも、要素が通知を送信することはありません。
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素は非割り込み型の通知を送信します。

   - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>。 ライブ領域の内容が変更された場合、要素により割り込み通知が送信されます。

関心のある要素で **AutomationProperties.LiveSetting** プロパティを作成できます。次の例をご覧ください。

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

ライブ領域のデータが変化し、スクリーン リーダーに通知する必要があれば、次のサンプルのように、明示的にイベントを発生させます。

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**ハイ コントラスト**

.NET Framework 4.7.1 以降、さまざまな WPF コントロールでハイ コントラストが強化されました。 <xref:System.Windows.SystemParameters.HighContrast%2A> テーマが設定されているときにこれを確認できます。 次の設定があります。

- <xref:System.Windows.Controls.Expander> コントロール

    フォーカスを合わせたとき、<xref:System.Windows.Controls.Expander> コントロールが見やすくなりました。 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.RadioButton> コントロールのキーボードも見やすくなりました。 次に例を示します。

    前: 

    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善前)](media/expander-before.png)

    後: 

    ![フォーカスを合わせた Expander コントロール (アクセシビリティ機能改善後)](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロール

    <xref:System.Windows.Controls.CheckBox> コントロールと <xref:System.Windows.Controls.RadioButton> コントロールのテキストは、ハイ コントラスト テーマで選択されているとき、見やすくなりました。 次に例を示します。

    前: 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善前)](media/radio-button-before.png)

    後: 

    ![フォーカスを合わせたハイ コントラストのラジオ ボタン (アクセシビリティ機能改善後)](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> コントロール

    .NET Framework 4.7.1 以降、無効にした <xref:System.Windows.Controls.ComboBox> コントロールの枠線が無効にしたテキストと同じ色になります。 次に例を示します。

    前: 

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善前)](media/combo-disabled-before.png)

    後:   

     ![無効にした ComboBox の枠線とテキスト (アクセシビリティ機能改善後)](media/combo-disabled-after.png)

    また、無効にしているボタンにフォーカスを合わせたとき、正しいテーマ色が使用されます。

    前:

    ![ボタンのテーマ色 (アクセシビリティ機能改善前)](media/button-themes-before.png) 

    後: 

    ![ボタンのテーマ色 (アクセシビリティ機能改善後)](media/button-themes-after.png) 

    最後になりますが、.NET Framework 4.7 以前のバージョンでは、<xref:System.Windows.Controls.ComboBox> コントロールのスタイルを `Toolbar.ComboBoxStyleKey` に設定すると、ドロップダウンの矢印が見えなくなりました。 この問題は .NET Framework 4.7.1 以降で修正されています。 次に例を示します。

    前: 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善前)](media/comboboxstylekey-before.png) 

    後: 

    ![Toolbar.ComboBoxStyleKey (アクセシビリティ機能改善後)](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> コントロール

    .NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> コントロールの並べ替えインジケーターで正しいテーマ色が使われるようになりました。 次に例を示します。

    前: 

    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善前)](media/sort-indicator-before.png) 

    後:   

    ![並べ替えインジケーターの矢印 (アクセシビリティ機能改善後)](media/sort-indicator-after.png) 

    また、.NET Framework 4.7 以前のバージョンでは、ハイ コントラスト モードでカーソルを合わせたとき、既定のリンク スタイルが正しくない色に変化しました。 これは .NET Framework 4.7.1 以降で修正されています。 同様に、.NET Framework 4.7.1 以降、<xref:System.Windows.Controls.DataGrid> チェックボックス列でキーボード フォーカス フィードバックに既定の色が使用されます。

    前: 

    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善前)](media/default-link-style-before.png) 

    後:    

    ![DataGrid の既定のリンク スタイル (アクセシビリティ機能改善後)](media/default-link-style-after.png) 

.NET Framework 4.7.1 のアクセシビリティ機能の改善の詳細については、「[Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)」 (WPF のアクセシビリティ機能改善) を参照してください。

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Windows フォームのアクセシビリティ機能改善

.NET Framework 4.7.1 では、Windows フォーム (WinForms) のアクセシビリティが次の領域で変更されました。

**ハイ コントラスト モードの表示が改善されました**

.NET Framework 4.7.1 以降では、オペレーティング システムで利用できるハイ コントラスト モードを選択したとき、さまざまな WinForms コントロールの表示が改善されました。 Windows 10 では、ハイ コントラストのシステム色の一部で値が変わりました。Windows フォームは Windows 10 Win32 フレームワークに基づきます。 最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次の画像のように Windows 10 対応 OS 行のコメントを解除します。

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

ハイ コントラストの変更例:

- <xref:System.Windows.Forms.MenuStrip> 項目のチェックマークが見やすくなりました。

- 選択したとき、無効になっている <xref:System.Windows.Forms.MenuStrip> 項目が見やすくなりました。

- 選択した <xref:System.Windows.Forms.Button> コントロールのテキストが背景色に対して際立ち、見やすくなりました。

- 無効になっているテキストが読みやすくなりました。 次に例を示します。

    前:

    ![無効にしたテキスト (アクセシビリティ機能改善前)](media/wf-disabled-before.png) 

    後:

    ![無効にしたテキスト (アクセシビリティ機能改善後)](media/wf-disabled-after.png) 

- スレッド例外ダイアログのハイ コントラストが改善されました。

**ナレーター サポートが改善されました**

.NET Framework 4.7.1 の Windows フォームでは、ナレーターのアクセシビリティが次の面で改善されました。

- <xref:System.Windows.Forms.MonthCalendar> コントロールに、他の UI 自動化ツールと同様に、ナレーターからアクセスできます。

- <xref:System.Windows.Forms.CheckedListBox> コントロールは、項目のチェック状態が変わったとき、ナレーターに通知します。その結果、リスト アイテムの値を変えたことがユーザーに通知されます。

- <xref:System.Windows.Forms.DataGridViewCell> コントロールは正しい読み取り専用状態をナレーターに報告します。

- ナレーターが無効になっている <xref:System.Windows.Forms.ToolStripMenuItem> テキストを読み上げるようになりました。以前は、無効になっているメニュー項目はスキップされました。

**UIAutomation アクセシビリティ パターンのサポートが強化されました**

.NET Framework 4.7.1 以降、アクセシビリティ技術ツールの開発者は、一部の WinForms コントロールについて、API アクセシビリティの共通のパターンとプロパティを活用できます。 アクセシビリティ機能改善の例:

- <xref:System.Windows.Forms.ComboBox> と <xref:System.Windows.Forms.ToolStripSplitButton> が[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。

- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> が[切り替えパターン](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)対応になりました。

- <xref:System.Windows.Forms.ToolStripItem> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティと[展開/折りたたみパターン](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)対応になりました。

- <xref:System.Windows.Forms.NumericUpDown> コントロールと <xref:System.Windows.Forms.DomainUpDown> コントロールが <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> プロパティ対応になりました。

**プロパティ ブラウザーが使いやすくなりました**

.NET Framework 4.7.1 以降、Windows フォームは次の点で改善されました。

- さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。
- 不要なタブ ストップが減りました。
- コントロールの種類の報告機能が改善されました。
- ナレーターの動作が改善されました。

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>ASP.NET Web コントロール

.NET Framework 4.7.1 および Visual Studio 2017 15.3 以降では、ASP.NET Web コントロールによる Visual Studio のアクセシビリティ テクノロジの処理方法が向上しています。 主な変更点は以下のとおりです。

- **[詳細の表示]** ウィザードの **[フィールドの追加]** ダイアログや **ListView** ウィザードの **[ListView の構成]** ダイアログなど、コントロールで不足していた UI アクセシビリティ パターンを実装するための変更。

- **データ ページャー フィールド エディター**など、ハイ コントラスト モードでの表示を改善するための変更。

- DataPager コントロールの **[ページャーのフィールドを編集]** ウィザードの **[フィールド]** ダイアログ、**[ObjectContext の構成]** ダイアログ、**[データ ソースの構成]** ウィザードの **[データの選択の構成]** ダイアログなど、キーボードの操作性を改善するための変更。

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>.NET SDK Tools

[構成エディター ツール (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) および[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) が、さまざまなアクセシビリティの問題を修正して改善されています。 その問題のほとんどは、名前の未定義や、特定の UI の自動化パターンが正しく実装されていないといった軽微なものです。 このような問題は、多くのユーザーが認識しないものですが、スクリーン リーダーのような支援技術を使用するお客様はこれらの SDK ツールのアクセシビリティの強化を実感されるでしょう。

これらの機能強化により、キーボード フォーカスの順序など、以前のいくつかの動作が変更されます。

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) ワークフロー デザイナー

ワークフロー デザイナーでのアクセシビリティに関する変更は次のとおりです。

- 一部のコントロールで、タブ オーダーが左から右、上から下に変更されます。

  - <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの関連付けデータを設定するための関連付けの初期化ウィンドウ。

  - <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティのコンテンツ定義ウィンドウ。

- キーボードで利用できる機能が増えます:

  - アクティビティのプロパティを編集する際、プロパティ グループに初めてフォーカスを設定したときに、プロパティ グループをキーボードで折りたたむことができます。

  - 警告アイコンにキーボードでアクセスできます。

  - **[プロパティ]** ウィンドウの **[その他のプロパティ]** ボタンに、キーボードでアクセスできます。

  - キーボードを使って、ワークフロー デザイナーの **[引数]** および **[変数]** ウィンドウのヘッダー項目にアクセスできます。

- 次のような場合に、フォーカスのある項目の可視性が向上しました:

  - ワークフロー デザイナーおよびアクティビティ デザイナーで使われているデータ グリッドへの行の追加。

  - <xref:System.ServiceModel.Activities.ReceiveReply> および <xref:System.ServiceModel.Activities.SendReply> アクティビティ内のフィールド間の Tab 移動。

  - 変数または引数の既定値の設定

- スクリーン リーダーが正しく認識できるようになりました:

  - ワークフロー デザイナーで設定されたブレークポイント。

  - <xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision>、<xref:System.ServiceModel.Activities.CorrelationScope> アクティビティ。
  - <xref:System.ServiceModel.Activities.Receive> アクティビティの内容。

  - <xref:System.Activities.Statements.InvokeMethod> アクティビティのターゲットの種類。

  - <xref:System.Activities.Statements.TryCatch> アクティビティの [例外] コンボ ボックスと [Finally] セクション。

  - メッセージング アクティビティの [メッセージの種類] コンボ ボックス、[関連付け初期化子の追加] ウィンドウのスプリッター、[コンテンツ定義] ウィンドウで、および [CorrelatesOn の定義] ウィンドウ (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply>)。

  - ステート マシンの遷移と遷移先。

  - <xref:System.Activities.Statements.FlowDecision> アクティビティの注釈とコネクタ。

  - アクティビティのコンテキスト (右クリック) メニュー。

  - プロパティ グリッドの、プロパティ値エディター、[検索のクリア] ボタン、[カテゴリ別] および [アルファベット順] の並べ替えボタン、[式エディター] ダイアログ。

  - ワークフロー デザイナーのズーム パーセンテージ。

  - <xref:System.Activities.Statements.Parallel> および <xref:System.Activities.Statements.Pick> アクティビティの区切り記号。

  - <xref:System.Activities.Statements.InvokeDelegate> アクティビティ。

  - ディクショナリ アクティビティの [型の選択] ウィンドウ (`Microsoft.Activities.AddToDictionary<TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` など)。

  - [.NET 型の参照と選択] ウィンドウ。

  - ワークフロー デザイナーでの階層リンク。

- ハイ コントラスト テーマを選ぶと、要素間のコントラスト比の向上や、フォーカス要素に使われる選択ボックスの認識性の向上など、ワークフロー デザイナーとそのコントロールの表示について多くの点が向上していることがわかります。

## <a name="see-also"></a>関連項目

- [.NET Framework の新機能](whats-new.md)
