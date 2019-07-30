---
title: ToolStrip コントロールのアーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363828"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip コントロールのアーキテクチャ

クラス<xref:System.Windows.Forms.ToolStrip> と<xref:System.Windows.Forms.ToolStripItem>クラスは、ツールバー、状態、およびメニュー項目を表示するための柔軟で拡張可能なシステムを提供します。 これらのクラスはすべて、 <xref:System.Windows.Forms>名前空間に含まれており、通常は "ToolStrip" プレフィックス ( <xref:System.Windows.Forms.ToolStripOverflow>など) または "ストリップ<xref:System.Windows.Forms.MenuStrip>" サフィックス (など) を使用して名前が付けられます。

## <a name="toolstrip"></a>ToolStrip

次のトピックで<xref:System.Windows.Forms.ToolStrip>は、とそれから派生するコントロールについて説明します。

<xref:System.Windows.Forms.ToolStrip>は、 <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.StatusStrip>、、および<xref:System.Windows.Forms.ContextMenuStrip>の抽象基本クラスです。 次のオブジェクトモデルは、 <xref:System.Windows.Forms.ToolStrip>継承階層を示しています。

![ToolStrip オブジェクトモデルを示す図。](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

内のすべての項目にアクセスする<xref:System.Windows.Forms.ToolStrip>には<xref:System.Windows.Forms.ToolStrip.Items%2A> 、コレクションを使用します。 内のすべての項目にアクセスする<xref:System.Windows.Forms.ToolStripDropDownItem>には<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> 、コレクションを使用します。 から<xref:System.Windows.Forms.ToolStrip>派生したクラスでは、 <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>プロパティを使用して、現在表示されている項目のみにアクセスすることもできます。 これらの項目は、現在オーバーフローメニューに含まれていません。

次の項目は、すべての方向にと<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>の両方でシームレスに動作するように設計されています。 これらは、 <xref:System.Windows.Forms.ToolStrip>デザイン時にコントロールに対して既定で使用できます。

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>は、を置き換える<xref:System.Windows.Forms.MainMenu>トップレベルのコンテナーです。 また、主要な処理とマルチドキュメントインターフェイス (MDI) 機能も用意されています。 機能的<xref:System.Windows.Forms.ToolStripDropDownItem>に<xref:System.Windows.Forms.ToolStripMenuItem>は、と<xref:System.Windows.Forms.MenuStrip>共に動作しますが<xref:System.Windows.Forms.ToolStripItem>、から派生します。

次の項目は、すべての方向にと<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>の両方でシームレスに動作するように設計されています。 これらは、 <xref:System.Windows.Forms.MenuStrip>デザイン時にコントロールに対して既定で使用できます。

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip>コントロールを<xref:System.Windows.Forms.StatusBar>置き換えます。 の<xref:System.Windows.Forms.StatusStrip>特別な機能としては、カスタムテーブルレイアウト、フォームのサイズ変更と移動グリップの`Spring`サポート、プロパティがあり<xref:System.Windows.Forms.ToolStripStatusLabel>ます。これにより、は、使用可能な領域を自動的に埋めることができます。

次の項目は、すべての方向にと<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>の両方でシームレスに動作するように設計されています。 これらは、 <xref:System.Windows.Forms.StatusStrip>デザイン時にコントロールに対して既定で使用できます。

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenu> が <xref:System.Windows.Forms.ContextMenuStrip> に置き換えられます。 を<xref:System.Windows.Forms.ContextMenuStrip>任意のコントロールに関連付けることができ、右クリックするとコンテキストメニュー (またはショートカットメニュー) が自動的に表示されます。 メソッド<xref:System.Windows.Forms.ToolStripDropDown.Show%2A>を使用し<xref:System.Windows.Forms.ContextMenuStrip>て、をプログラムで表示できます。 <xref:System.Windows.Forms.ContextMenuStrip>動的な<xref:System.Windows.Forms.ToolStripDropDown.Opening>作成<xref:System.Windows.Forms.ToolStripDropDown.Closing>や複数クリックのシナリオを処理するためのキャンセル可能なイベントとイベントをサポートします。 <xref:System.Windows.Forms.ContextMenuStrip>イメージ、メニュー項目のチェック状態、テキスト、アクセスキー、ショートカット、およびカスケードメニューをサポートします。

次の項目は、すべての方向にと<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>の両方でシームレスに動作するように設計されています。 これらは、 <xref:System.Windows.Forms.ContextMenuStrip>デザイン時にコントロールに対して既定で使用できます。

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>ToolStrip 汎用機能

次のトピックでは、およびの<xref:System.Windows.Forms.ToolStrip>派生コントロールに共通する機能と動作について説明します。

#### <a name="painting"></a>画

コントロールで<xref:System.Windows.Forms.ToolStrip>は、いくつかの方法でカスタムの描画を行うことができます。 他の Windows フォームコントロールと同様に<xref:System.Windows.Forms.ToolStrip> 、 <xref:System.Windows.Forms.ToolStripItem>との両方`OnPaint`に、 `Paint`オーバーライド可能なメソッドとイベントがあります。 通常の描画と同様に、座標系はコントロールのクライアント領域を基準としています。つまり、コントロールの左上隅は0、0です。 の`Paint`イベントと`OnPaint` メソッド<xref:System.Windows.Forms.ToolStripItem>は、他のコントロール描画イベントと同様に動作します。

また<xref:System.Windows.Forms.ToolStrip> 、コントロールは、 <xref:System.Windows.Forms.ToolStripRenderer>クラスを介した項目とコンテナーのレンダリングにより詳細にアクセスできるようにします。これには、背景、項目の背景、項目の画像、項目の矢印、項目のテキスト、および境界線を描画するためのオーバーライド可能なメソッドがあります<xref:System.Windows.Forms.ToolStrip>。 これらのメソッドのイベント引数は、四角形、色、テキスト形式など、必要に応じて調整できるいくつかのプロパティを公開します。

項目を描画する方法のいくつかの側面だけを調整するには、 <xref:System.Windows.Forms.ToolStripRenderer>通常、をオーバーライドします。

新しい項目を作成しているときに、描画のすべての側面を制御する場合`OnPaint`は、メソッドをオーバーライドします。 内`OnPaint`から、の<xref:System.Windows.Forms.ToolStripRenderer>メソッドを使用できます。

既定<xref:System.Windows.Forms.ToolStrip>では、は、 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>設定を利用して、ダブルバッファリングされます。

#### <a name="parenting"></a>親子

コンテナーの所有権と親の概念は、他<xref:System.Windows.Forms.ToolStrip>の Windows フォームコンテナーコントロールよりもコントロールが複雑になります。 これは、オーバーフローなどの動的なシナリオをサポートし、複数<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ContextMenuStrip>の項目にわたるドロップダウン項目を共有し、コントロールからの生成をサポートするために必要です。

次の一覧では、親子関係に関連するメンバーとその使用方法について説明します。

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>ドロップダウン項目のソースである項目にアクセスします。 これはに<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>似てい<xref:System.Windows.Forms.ToolStripItem>ますが、コントロールを返すのではなく、を返します。

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>複数のコントロールが同じ<xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>を共有する場合に、のソースとなるコントロールを決定します。

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>は、 <xref:System.Windows.Forms.ToolStripItem.Parent%2A>プロパティに対する読み取り専用のアクセサーです。 親は、項目が表示されている現在のが返さ<xref:System.Windows.Forms.ToolStrip>れた現在のがオーバーフロー領域に存在する可能性があるという点で、所有者と異なります。

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>項目コレクションに現在<xref:System.Windows.Forms.ToolStripItem>のが含まれているを返します。 <xref:System.Windows.Forms.ToolStrip> これは、オーバーフローを処理する<xref:System.Windows.Forms.ToolStrip.ImageList%2A>特殊なコードを記述しなくて<xref:System.Windows.Forms.ToolStrip>も、トップレベルのプロパティを参照するための最適な方法です。

#### <a name="behavior-of-inherited-controls"></a>継承されたコントロールの動作

次のコントロールは、継承で使用されるたびにロックされます。

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>これには、の<xref:System.Windows.Forms.ToolStripContainer>パネルと、個別<xref:System.Windows.Forms.ToolStripPanel>のコントロールが含まれます。

たとえば、前の一覧の1つまたは複数のコントロールを使用して、新しい Windows フォームアプリケーションを作成します。 1つまたは複数のコントロールのアクセス修飾子`public`を`protected`またはに設定し、プロジェクトをビルドします。 最初のフォームから継承したフォームを追加し、継承されたコントロールを選択します。 コントロールがロックされ、アクセス修飾子が`private`のように動作します。

#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer の継承のサポート

コントロール<xref:System.Windows.Forms.ToolStripContainer>は、次の例のように、制限付きの継承されたシナリオをサポートします。

1. 新しい Windows フォーム アプリケーションを作成します。

2. フォームに <xref:System.Windows.Forms.ToolStripContainer> を追加します。

3. のアクセス修飾子<xref:System.Windows.Forms.ToolStripContainer>をまたは`protected`に`public`設定します。

4. <xref:System.Windows.Forms.ToolStrip>、、および<xref:System.Windows.Forms.ToolStripContainer> <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.MenuStrip>の各コントロールの任意の組み合わせをの領域に追加します。<xref:System.Windows.Forms.ContextMenuStrip>

5. プロジェクトをビルドします。

6. 最初のフォームから継承するフォームを追加します。

7. フォームで継承<xref:System.Windows.Forms.ToolStripContainer>されたを選択します。

#### <a name="inherited-behavior-of-child-controls"></a>子コントロールの継承された動作

前の手順を完了すると、次の継承された動作が行われます。

- デザイナーでは、コントロールが継承されたアイコンと共に表示されます。

- コントロール<xref:System.Windows.Forms.ToolStripPanel>はロックされています。コンテンツを選択または再配置することはできません。

- に<xref:System.Windows.Forms.ToolStripContentPanel>コントロールを追加したり、コントロールを移動したり、 <xref:System.Windows.Forms.ToolStripContentPanel>の子コントロールを作成したりすることができます。

- フォームをビルドした後も変更は保持されます。

  > [!NOTE]
  > <xref:System.Windows.Forms.ToolStripPanel> に<xref:System.Windows.Forms.ToolStripContainer>含まれるすべてのコントロールからアクセス修飾子を削除します。 の<xref:System.Windows.Forms.ToolStripContainer>アクセス修飾子は、コントロール全体を制御します。

#### <a name="partial-trust"></a>部分信頼

部分信頼に`ToolStrip`おけるの制限は、承認されていない人物やサービスによって使用される個人情報が誤って入力されないように設計されています。 保護対策は次のとおりです。

- `ToolStripDropDown`コントロールで<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>は、 <xref:System.Windows.Forms.ToolStripControlHost>に項目を表示する必要があります。 これは<xref:System.Windows.Forms.ToolStripTextBox>、、、 <xref:System.Windows.Forms.ToolStripProgressBar>などの<xref:System.Windows.Forms.ToolStripComboBox>組み込みコントロールと、ユーザーが作成したコントロールの両方に適用されます。 この要件が満たされていない場合、これらの項目は表示されません。 例外をスローすることはありません。

- プロパティをに設定`false`することはできません。 <xref:System.Windows.Forms.ToolStripDropDown.Closing>また、キャンセル可能なイベントパラメーターは無視されます。 <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> これにより、ドロップダウン項目を終了せずに複数のキーストロークを入力することはできません。 この要件が満たされていない場合、このような項目は表示されません。 例外をスローすることはありません。

- 以外<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>の部分信頼コンテキストで発生した場合、多くのキーストローク処理イベントは発生しません。

- が付与されてい<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>ない場合、アクセスキーは処理されません。

#### <a name="usage"></a>使用法

次の使用パターンは、レイアウト、 <xref:System.Windows.Forms.ToolStrip>キーボード操作、およびエンドユーザーの動作に影響します。

- に参加<xref:System.Windows.Forms.ToolStripPanel>

  は、との<xref:System.Windows.Forms.ToolStripPanel>間<xref:System.Windows.Forms.ToolStripPanel>で再配置できます。<xref:System.Windows.Forms.ToolStrip> `false` <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>プロパティは無視され、 <xref:System.Windows.Forms.ToolStrip.Stretch%2A>プロパティがの場合は、項目がに追加されたときにのサイズが大きくなります。 `Dock` 通常、は<xref:System.Windows.Forms.ToolStrip>タブオーダーには参加しません。

- ドッキング

  は<xref:System.Windows.Forms.ToolStrip> 、固定された位置にあるコンテナーの1つの側に配置され、そのサイズはドッキングされるエッジ全体で拡大されます。 通常、は<xref:System.Windows.Forms.ToolStrip>タブオーダーには参加しません。

- 絶対配置

  は他のコントロールと同じように、 <xref:System.Windows.Forms.Control.Location%2A>プロパティによって配置され、固定サイズであり、通常はタブオーダーに含まれます。 <xref:System.Windows.Forms.ToolStrip>

#### <a name="keyboard-interaction"></a>キーボード操作

##### <a name="access-keys"></a>アクセスキー

ALT キーと組み合わせて、またはその後、アクセスキーは、キーボードを使用してコントロールをアクティブ化するための1つの方法です。 <xref:System.Windows.Forms.ToolStrip>明示的および暗黙的なアクセスキーの両方をサポートします。 明示的な定義では、文字の前にアンパサンド (&) 文字を使用します。 暗黙の定義では、特定のプロパティの文字の順序に基づいて一致する項目の検索`Text`を試みるアルゴリズムが使用されます。

##### <a name="shortcut-keys"></a>ショートカット キー

によって<xref:System.Windows.Forms.MenuStrip>使用されるショートカットキーでは<xref:System.Windows.Forms.Keys> 、(順序固有ではない) 列挙型の組み合わせを使用して、ショートカットキーを定義します。 また、 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>プロパティを使用して、ショートカットキーをテキストのみで表示することもできます。たとえば、"delete" の代わりに "del" を表示することもできます。

##### <a name="navigation"></a>ナビゲーション

ALT キーは、 <xref:System.Windows.Forms.MenuStrip>が指す<xref:System.Windows.Forms.Form.MainMenuStrip%2A>をアクティブにします。 そこから、CTRL キーを押しながら<xref:System.Windows.Forms.ToolStrip> TAB キー `ToolStripPanel`を押すと、内のコントロール間を移動できます。 テンキーの TAB キーと方向キーは、内の項目間を<xref:System.Windows.Forms.ToolStrip>移動します。 特殊なアルゴリズムは、オーバーフロー領域でのナビゲーションを処理します。 Space キーを<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripDropDownButton>押すと、 <xref:System.Windows.Forms.ToolStripSplitButton>、、またはが選択されます。

##### <a name="focus-and-validation"></a>フォーカスと検証

ALT キー <xref:System.Windows.Forms.MenuStrip>でアクティブにした場合、 <xref:System.Windows.Forms.ToolStrip>またはは通常、フォーカスを持つコントロールからフォーカスを取得したり削除したりすることはありません。 の<xref:System.Windows.Forms.MenuStrip>またはドロップダウン<xref:System.Windows.Forms.MenuStrip>内でホストされているコントロールがある場合、ユーザーが TAB キーを押したときにコントロールのフォーカスが得られます。 一般<xref:System.Windows.Forms.Control.GotFocus> <xref:System.Windows.Forms.Control.Leave>に、の<xref:System.Windows.Forms.Control.LostFocus>、、 <xref:System.Windows.Forms.Control.Enter>、の<xref:System.Windows.Forms.MenuStrip>各イベントは、キーボードによってアクティブ化されるときに発生しない可能性があります。 このような場合は、 <xref:System.Windows.Forms.MenuStrip.MenuActivate>イベント<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>とイベントを代わりに使用します。

既定では<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> 、 `false`はです。 検証<xref:System.Windows.Forms.ContainerControl.Validate%2A>を実行するには、フォームで明示的にを呼び出します。

#### <a name="layout"></a>レイアウト

プロパティを<xref:System.Windows.Forms.ToolStrip>使用<xref:System.Windows.Forms.ToolStripLayoutStyle>してのメンバーの1つを選択することによって、レイアウトを制御します。 <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>

##### <a name="stack-layouts"></a>スタックレイアウト

スタックとは、 <xref:System.Windows.Forms.ToolStrip>の両端にある項目の横に配置することです。 次の一覧では、スタックレイアウトについて説明します。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> が既定値です。 この設定により<xref:System.Windows.Forms.ToolStrip> 、は、ドラッグアンドドッキングのシナリオを<xref:System.Windows.Forms.ToolStrip.Orientation%2A>処理するために、プロパティに従って自動的にレイアウトを変更します。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>項目を<xref:System.Windows.Forms.ToolStrip>縦に並べて表示します。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>項目を<xref:System.Windows.Forms.ToolStrip>水平方向に横に並べて表示します。

##### <a name="other-features-of-stack-layouts"></a>スタックレイアウトのその他の機能

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>項目の位置<xref:System.Windows.Forms.ToolStrip>を示すの末尾を決定します。

項目が<xref:System.Windows.Forms.ToolStrip>内に収まらない場合は、オーバーフローボタンが自動的に表示されます。 プロパティ<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>の設定は、項目が常にオーバーフロー領域に表示されるか、必要に応じて表示されるか、または行わないかを決定します。

イベントでは、 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>プロパティを調べて、項目がメイン<xref:System.Windows.Forms.ToolStrip>に配置されたか、オーバーフロー <xref:System.Windows.Forms.ToolStrip>したか、または項目が現在まったく表示されていないかどうかを確認できます。 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 項目が表示されない一般的な理由として、項目がメイン<xref:System.Windows.Forms.ToolStrip>に合わなかったことと、その<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>プロパティ<xref:System.Windows.Forms.ToolStripItemOverflow.Never>がに設定されていることが挙げられます。

に移動<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>し、 <xref:System.Windows.Forms.ToolStrip.GripStyle%2A>をに<xref:System.Windows.Forms.ToolStripGripStyle.Visible>設定して、移動可能にします。

##### <a name="other-layout-options"></a>その他のレイアウトオプション

その他のレイアウトオプション<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>は<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>、とです。

##### <a name="flow-layout"></a>フロー レイアウト

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトは、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、、 <xref:System.Windows.Forms.ContextMenuStrip>および<xref:System.Windows.Forms.ToolStripOverflow>の既定の設定です。 これはに<xref:System.Windows.Forms.FlowLayoutPanel>似ています。 レイアウトの<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>機能は次のとおりです。

- の<xref:System.Windows.Forms.FlowLayoutPanel>すべての機能は、 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティによって公開されます。 <xref:System.Windows.Forms.LayoutSettings> クラス<xref:System.Windows.Forms.FlowLayoutSettings>をクラスにキャストする必要があります。

- コードでプロパティ<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>プロパティを使用して、行内の項目を揃えることができます。

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。

- イベントでは、 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>プロパティを調べて、項目がメイン<xref:System.Windows.Forms.ToolStrip>に配置されたか、または一致していないかを判断できます。 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- グリップはレンダリングされないため、内<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>の<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトスタイルのは移動できません。

- オーバーフローボタンはレンダリング<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>されず、は無視されます。 <xref:System.Windows.Forms.ToolStrip>

##### <a name="table-layout"></a>テーブル レイアウト

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>レイアウトがの<xref:System.Windows.Forms.StatusStrip>既定値です。 これはに<xref:System.Windows.Forms.TableLayoutPanel>似ています。 レイアウトの<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>機能は次のとおりです。

- の<xref:System.Windows.Forms.TableLayoutPanel>すべての機能は、 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティによって公開されます。 <xref:System.Windows.Forms.LayoutSettings> クラス<xref:System.Windows.Forms.TableLayoutSettings>をクラスにキャストする必要があります。

- コードでプロパティ<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>プロパティを使用して、テーブルセル内のアイテムを配置できます。

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。

- イベントでは、 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>プロパティを調べて、項目がメイン<xref:System.Windows.Forms.ToolStrip>に配置されたか、または一致していないかを判断できます。 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- グリップはレンダリングされないため、内<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>の<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>レイアウトスタイルのは移動できません。

- オーバーフローボタンはレンダリング<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>されず、は無視されます。 <xref:System.Windows.Forms.ToolStrip>

## <a name="toolstripitem"></a>ToolStripItem

次のトピックで<xref:System.Windows.Forms.ToolStripItem>は、とそれから派生するコントロールについて説明します。

<xref:System.Windows.Forms.ToolStripItem>は、に<xref:System.Windows.Forms.ToolStrip>入るすべての項目の抽象基本クラスです。 次のオブジェクトモデルは、 <xref:System.Windows.Forms.ToolStripItem>継承階層を示しています。

![ToolStripItem オブジェクトモデルを示す図。](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>クラスは<xref:System.Windows.Forms.ToolStripItem>、から直接継承されるか、 <xref:System.Windows.Forms.ToolStripControlHost>また<xref:System.Windows.Forms.ToolStripItem>は<xref:System.Windows.Forms.ToolStripDropDownItem>から間接的に継承されます。

<xref:System.Windows.Forms.ToolStripItem><xref:System.Windows.Forms.ToolStrip>コントロールは<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> 、、、、またはに含まれている必要があります。フォームに直接追加することはできません。 <xref:System.Windows.Forms.StatusStrip> さまざまなコンテナークラスは、コントロールの<xref:System.Windows.Forms.ToolStripItem>適切なサブセットを含むように設計されています。

次の表に、ストック<xref:System.Windows.Forms.ToolStripItem>コントロールと、それらが最適なコンテナーを示します。 任意の<xref:System.Windows.Forms.ToolStrip>項目を派生した任意のコンテナーでホストできますが、これらの項目は次のコンテナーで最適に表示されるように設計されています。 <xref:System.Windows.Forms.ToolStrip>

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>デザイナーのツールボックスには表示されません。

|含まれている項目|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|[はい]|いいえ|いいえ|いいえ|はい|
|<xref:System.Windows.Forms.ToolStripComboBox>|はい|はい|[はい]|×|はい|
|<xref:System.Windows.Forms.ToolStripSplitButton>|[はい]|いいえ|いいえ|はい|はい|
|<xref:System.Windows.Forms.ToolStripLabel>|[はい]|いいえ|いいえ|はい|はい|
|<xref:System.Windows.Forms.ToolStripSeparator>|はい|はい|[はい]|×|はい|
|<xref:System.Windows.Forms.ToolStripDropDownButton>|[はい]|いいえ|いいえ|はい|はい|
|<xref:System.Windows.Forms.ToolStripTextBox>|はい|はい|[はい]|×|はい|
|<xref:System.Windows.Forms.ToolStripMenuItem>|×|はい|[はい]|いいえ|いいえ|
|<xref:System.Windows.Forms.ToolStripStatusLabel>|いいえ|いいえ|いいえ|はい|×|
|<xref:System.Windows.Forms.ToolStripProgressBar>|はい|いいえ|いいえ|はい|×|
|<xref:System.Windows.Forms.ToolStripControlHost>|はい|[はい]|×|はい|[はい]|

### <a name="toolstripbutton"></a>ToolStripButton

<xref:System.Windows.Forms.ToolStripButton>は、の<xref:System.Windows.Forms.ToolStrip>ボタン項目です。 さまざまな境界線スタイルを使用して表示することができ、それを使用して操作状態を表したり、アクティブ化したりすることができます。 既定でフォーカスを設定するように定義することもできます。

### <a name="toolstriplabel"></a>ToolStripLabel

は<xref:System.Windows.Forms.ToolStripLabel> 、コントロールにラベル<xref:System.Windows.Forms.ToolStrip>機能を提供します。 <xref:System.Windows.Forms.ToolStripLabel>は、<xref:System.Windows.Forms.ToolStripButton>既定ではフォーカスが得られず、プッシュまたは強調表示されないに似ています。

<xref:System.Windows.Forms.ToolStripLabel>ホストされた項目として、アクセスキーをサポートします。

<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> <xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStrip>で、 、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>、およびの各プロパティを使用して、のリンクコントロールをサポートします。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>は、専用に<xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.StatusStrip>設計されたのバージョンです。 特別な機能に<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>は<xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>、、 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>、およびがあります。

### <a name="toolstripseparator"></a>ToolStripSeparator

は<xref:System.Windows.Forms.ToolStripSeparator> 、向きに応じて、ツールバーまたはメニューに垂直または水平の線を追加します。 メニュー上の項目など、項目のグループ化や区別を行います。

デザイン時にを<xref:System.Windows.Forms.ToolStripSeparator>追加するには、ドロップダウンリストからを選択します。 ただし、デザイナーテンプレートノードまたは<xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>メソッドのいずれかでハイフン (-) を入力して、を自動的に作成することもできます。

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>は、 <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripTextBox>、、および<xref:System.Windows.Forms.ToolStripProgressBar>の抽象基本クラスです。 <xref:System.Windows.Forms.ToolStripControlHost>では、次の2つの方法で、カスタムコントロールを含む他のコントロールをホストできます。

- <xref:System.Windows.Forms.ToolStripControlHost> から<xref:System.Windows.Forms.Control>派生したクラスを使用して、を構築します。 ホストされるコントロールとプロパティに完全にアクセスするには<xref:System.Windows.Forms.ToolStripControlHost.Control%2A> 、そのプロパティを表す実際のクラスにキャストする必要があります。

- を<xref:System.Windows.Forms.ToolStripControlHost>拡張し、継承されたクラスのパラメーターなしのコンストラクターで、から<xref:System.Windows.Forms.Control>派生したクラスを渡す基本クラスのコンストラクターを呼び出します。 このオプションを使用すると、に簡単にアクセスできるように、 <xref:System.Windows.Forms.ToolStrip>一般的なコントロールメソッドとプロパティをラップできます。

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>は、 <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStrip>でホストするために最適化されたです。 ホストされるコントロールのプロパティとイベントのサブセットは<xref:System.Windows.Forms.ToolStripComboBox>レベルで公開されますが、基になる<xref:System.Windows.Forms.ComboBox>コントロールに<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>はプロパティを使用して完全にアクセスできます。

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>は、 <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ToolStrip>でホストするために最適化されたです。 ホストされるコントロールのプロパティとイベントのサブセットは<xref:System.Windows.Forms.ToolStripTextBox>レベルで公開されますが、基になる<xref:System.Windows.Forms.TextBox>コントロールに<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>はプロパティを使用して完全にアクセスできます。

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>は、 <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ToolStrip>でホストするために最適化されたです。 ホストされるコントロールのプロパティとイベントのサブセットは<xref:System.Windows.Forms.ToolStripProgressBar>レベルで公開されますが、基になる<xref:System.Windows.Forms.ProgressBar>コントロールに<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>はプロパティを使用して完全にアクセスできます。

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>は、 <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripDropDownButton>、、および<xref:System.Windows.Forms.ToolStripSplitButton>の抽象基本クラスであり、項目を直接ホストすることも、ドロップダウンコンテナーで追加の項目をホストすることもできます。 これを行うには、 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>プロパティを<xref:System.Windows.Forms.ToolStripDropDown>に設定し、 <xref:System.Windows.Forms.ToolStrip.Items%2A> <xref:System.Windows.Forms.ToolStripDropDown>のプロパティを設定します。 プロパティを使用して、 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>これらのドロップダウン項目に直接アクセスします。

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>は、 <xref:System.Windows.Forms.ToolStripDropDownMenu> および<xref:System.Windows.Forms.ContextMenuStrip>で動作し、メニューの特別な強調表示、レイアウト、および列の配置を処理するです。 <xref:System.Windows.Forms.ToolStripDropDownItem>

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>はの<xref:System.Windows.Forms.ToolStripButton>ように見えますが、ユーザーがクリックするとドロップダウン領域が表示されます。 <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>プロパティを設定して、ドロップダウン矢印を表示または非表示にします。 <xref:System.Windows.Forms.ToolStripDropDownButton><xref:System.Windows.Forms.ToolStripOverflowButton> を<xref:System.Windows.Forms.ToolStrip>オーバーフローする項目を表示するをホストします。

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>ボタンとドロップダウンボタンの機能を組み合わせます。

プロパティを使用して、 <xref:System.Windows.Forms.Control.Click>選択したドロップダウン項目のイベントと、ボタンに表示されている項目を同期します。 <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>

### <a name="toolstripitem-generic-features"></a>ToolStripItem 汎用機能

<xref:System.Windows.Forms.ToolStripItem>には、コントロールを継承するための次の一般的な機能とオプションが用意されています。

- コアイベント

- イメージの処理

- アラインメント

- テキストとイメージの関係

- 表示スタイル

#### <a name="core-events"></a>コアイベント

<xref:System.Windows.Forms.ToolStripItem>コントロールは、独自のクリック、マウス、および描画イベントを受け取り、一部のキーボード前処理も実行できます。

#### <a name="image-handling"></a>イメージの処理

<xref:System.Windows.Forms.ToolStripItem.Image%2A> 、<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>、 、<xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>、およびの各プロパティは、イメージ処理のさまざまな側面に関連します。<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> コントロール内の<xref:System.Windows.Forms.ToolStrip>イメージを使用するには、これらのプロパティを直接設定するか<xref:System.Windows.Forms.ToolStrip.ImageList%2A> 、実行時のみのプロパティを設定します。

イメージのスケーリングは、次のように、と<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripItem>の両方のプロパティの相互作用によって決定されます。

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>は、イメージの<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>設定とコンテナーの<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>設定の組み合わせによって決定される最終的なイメージの小数点以下桁数です。

  - が<xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit> (既定値<xref:System.Windows.Forms.ToolStrip> ) であり、がである場合、イメージのスケーリングは行われず、サイズは最大の項目のサイズまたは指定された最小サイズになります。<xref:System.Windows.Forms.ToolStripItemImageScaling> `true`

  - が<xref:System.Windows.Forms.ToolStrip.AutoSize%2A> で`false` <xref:System.Windows.Forms.ToolStripItemImageScaling.None> <xref:System.Windows.Forms.ToolStrip> 、がの場合、イメージもスケーリングも実行されません。 <xref:System.Windows.Forms.ToolStripItemImageScaling>

#### <a name="alignment"></a>アラインメント

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティの値によって、 <xref:System.Windows.Forms.ToolStrip>項目が表示されるの末尾が決まります。 プロパティ<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>は、 <xref:System.Windows.Forms.ToolStrip>のレイアウトスタイルがスタックオーバーフローの値のいずれかに設定されている場合にのみ機能します。

項目は、 <xref:System.Windows.Forms.ToolStrip>項目コレクション内で項目が表示される順序でに配置されます。 項目のレイアウトをプログラムで変更するには、 <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>メソッドを使用してコレクション内の項目を移動します。 このメソッドは項目を移動しますが、重複しません。

#### <a name="text-and-image-relationship"></a>テキストとイメージの関係

プロパティ<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>は、のテキスト<xref:System.Windows.Forms.ToolStripItem>に対するイメージの相対的な配置を定義します。 イメージ、テキスト、またはその両方を持たない項目は特殊なケースとし<xref:System.Windows.Forms.ToolStripItem>て扱われるので、によって欠落している要素の空白の位置が表示されません。

#### <a name="display-style"></a>表示スタイル

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>項目のテキストとイメージのプロパティの値を設定し、必要なものだけを表示することができます。 これは通常、別のコンテキストで同じ項目を表示するときに、表示スタイルのみを変更するために使用されます。

## <a name="accessory-classes"></a>アクセサリクラス

その他のさまざまな機能を提供するクラスは次のとおりです。

- <xref:System.Windows.Forms.ToolStripManager>マージ<xref:System.Windows.Forms.ToolStrip>、設定、レンダラーオプションなど、アプリケーション全体に関連するタスクをサポートします。

- <xref:System.Windows.Forms.ToolStripRenderer>では、 <xref:System.Windows.Forms.ToolStrip>特定のスタイルまたはテーマを簡単に適用できます。

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>置き換え可能なカラーテーブル (<xref:System.Windows.Forms.ProfessionalColorTable>) に基づいて、ペンとブラシを作成します。

- <xref:System.Windows.Forms.ToolStripSystemRenderer>アプリケーションに<xref:System.Windows.Forms.ToolStrip>システムカラーとフラットな視覚スタイルを適用します。

- <xref:System.Windows.Forms.ToolStripContainer>はに<xref:System.Windows.Forms.SplitContainer>似ています。 この例では、4つのドッキング<xref:System.Windows.Forms.ToolStripPanel>されたサイドパネル (のインスタンス) <xref:System.Windows.Forms.ToolStripContentPanel>と1つの中央のパネル (のインスタンス) を使用して、一般的な配置を作成します。 サイドパネルを削除することはできませんが、非表示にすることはできます。 中央のパネルを削除したり非表示にしたりすることはできません。 サイドパネルには、1 <xref:System.Windows.Forms.ToolStrip>つ<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.StatusStrip>複数のコントロールを配置できます。また、中央のパネルを使用して他のコントロールを配置することもできます。 また<xref:System.Windows.Forms.ToolStripContentPanel> 、では、フォームの本文に対するレンダラーサポートを一貫した外観で利用することもできます。 <xref:System.Windows.Forms.ToolStripContainer>では、マルチドキュメントインターフェイス (MDI) はサポートされていません。

- <xref:System.Windows.Forms.ToolStripPanel>コントロールを移動および整列<xref:System.Windows.Forms.ToolStrip>するための領域を提供します。 パネルは1つしか使用できません。選択する<xref:System.Windows.Forms.ToolStripPanel>と、MDI シナリオで適切に動作します。

## <a name="see-also"></a>関連項目

- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
- [MenuStrip コントロール](menustrip-control-windows-forms.md)
- [StatusStrip コントロール](statusstrip-control.md)
- [ContextMenuStrip コントロール](contextmenustrip-control.md)
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
