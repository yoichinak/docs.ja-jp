---
title: ToolStrip コントロールのアーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: e02b9daa40a5f8a2f8bfd8874d006550628a70b3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654718"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip コントロールのアーキテクチャ
<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>クラスは、ツールバー、ステータス、およびメニュー項目を表示するため、柔軟で拡張性の高いシステムを提供します。 これらのクラスがすべてに含まれる、<xref:System.Windows.Forms>名前空間と、通常、すべて"ToolStrip"プレフィックスを持つという名前 (など<xref:System.Windows.Forms.ToolStripOverflow>) または「ストリップ」サフィックスを持つ (など<xref:System.Windows.Forms.MenuStrip>)。  
  
## <a name="toolstrip"></a>ToolStrip  
 次のトピックについて説明します<xref:System.Windows.Forms.ToolStrip>とそこから派生するコントロール。  
  
 <xref:System.Windows.Forms.ToolStrip> 抽象基本クラスは、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.StatusStrip>、および<xref:System.Windows.Forms.ContextMenuStrip>します。 次のオブジェクト モデルの表示、<xref:System.Windows.Forms.ToolStrip>継承階層。  
  
 ![ToolStrip オブジェクト モデルを示す図。](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 すべての項目にアクセスすることができます、<xref:System.Windows.Forms.ToolStrip>を通じて、<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクション。 すべての項目にアクセスすることができます、<xref:System.Windows.Forms.ToolStripDropDownItem>を通じて、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>コレクション。 派生したクラスで<xref:System.Windows.Forms.ToolStrip>、使用することも、<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>現在表示されている項目のみにアクセスするプロパティ。 これらは、オーバーフロー メニューに現在含まれていない項目です。  
  
 次のものを両方でシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>ですべての向き。 デザイン時に既定で使用できますが、<xref:System.Windows.Forms.ToolStrip>コントロール。  
  
- <xref:System.Windows.Forms.ToolStripButton>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> 最上位のコンテナーを置き換える<xref:System.Windows.Forms.MainMenu>します。 また、キーを処理し、複数のドキュメント インターフェイス (MDI) の機能。 機能的には、<xref:System.Windows.Forms.ToolStripDropDownItem>と<xref:System.Windows.Forms.ToolStripMenuItem>と共に職場<xref:System.Windows.Forms.MenuStrip>から派生しているが、<xref:System.Windows.Forms.ToolStripItem>します。  
  
 次のものを両方でシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>ですべての向き。 デザイン時に既定で使用できますが、<xref:System.Windows.Forms.MenuStrip>コントロール。  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> 置換、<xref:System.Windows.Forms.StatusBar>コントロール。 特殊な機能<xref:System.Windows.Forms.StatusStrip>カスタム テーブル レイアウトを含める、フォームのサイズ変更や、グリップを移動のサポートと`Spring`プロパティを<xref:System.Windows.Forms.ToolStripStatusLabel>に使用可能な領域を自動的に入力します。  
  
 次のものを両方でシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>ですべての向き。 デザイン時に既定で使用できますが、<xref:System.Windows.Forms.StatusStrip>コントロール。  
  
- <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
- <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
- <xref:System.Windows.Forms.ToolStripSplitButton>  
  
- <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenu> が <xref:System.Windows.Forms.ContextMenuStrip> に置き換えられます。 関連付けることができます、<xref:System.Windows.Forms.ContextMenuStrip>任意のコントロールとマウスの右クリック自動的に表示されますコンテキスト メニュー (またはショートカット メニュー)。 表示することができます、<xref:System.Windows.Forms.ContextMenuStrip>を使用してプログラムで、<xref:System.Windows.Forms.ToolStripDropDown.Show%2A>メソッド。 <xref:System.Windows.Forms.ContextMenuStrip> キャンセル可能なサポート<xref:System.Windows.Forms.ToolStripDropDown.Opening>と<xref:System.Windows.Forms.ToolStripDropDown.Closing>動的母集団とクリックで複数のシナリオを処理するイベントです。 <xref:System.Windows.Forms.ContextMenuStrip> イメージ、メニュー項目のチェック状態、テキスト、アクセス キー、ショートカット、およびカスケード メニューをサポートしています。  
  
 次のものを両方でシームレスに動作する目的<xref:System.Windows.Forms.ToolStripSystemRenderer>と<xref:System.Windows.Forms.ToolStripProfessionalRenderer>ですべての向き。 デザイン時に既定で使用できますが、<xref:System.Windows.Forms.ContextMenuStrip>コントロール。  
  
- <xref:System.Windows.Forms.ToolStripMenuItem>  
  
- <xref:System.Windows.Forms.ToolStripSeparator>  
  
- <xref:System.Windows.Forms.ToolStripTextBox>  
  
- <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip のジェネリック機能  
 次のトピックは、機能とは汎用的に動作について説明します。、<xref:System.Windows.Forms.ToolStrip>とコントロールを派生します。  
  
#### <a name="painting"></a>描画  
 カスタム描画を行うことができます<xref:System.Windows.Forms.ToolStrip>いくつかの方法でコントロールできます。 その他の Windows フォーム コントロールと同様、<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>両方が、オーバーライド可能な`OnPaint`メソッドと`Paint`イベント。 通常の描画座標システムは、コントロールのクライアント領域を基準とはつまり、コントロールの左上隅には 0、0。 `Paint`イベントと`OnPaint`のメソッド、<xref:System.Windows.Forms.ToolStripItem>他のコントロールの描画イベントと同様に動作します。  
  
 <xref:System.Windows.Forms.ToolStrip>コントロールもを通じてコンテナー、アイテムのレンダリングにさらに細かくアクセスを提供、<xref:System.Windows.Forms.ToolStripRenderer>クラスで、背景、アイテムの背景、項目のイメージ、項目の矢印、項目のテキストの描画のオーバーライド可能なメソッドを持っているとの境界線と、<xref:System.Windows.Forms.ToolStrip>. これらのメソッドのイベント引数は、四角形、色、および必要に応じて調整できるテキスト形式などのいくつかのプロパティを公開します。  
  
 オーバーライドする通常の項目を描画する方法のいくつかの側面を調整する、<xref:System.Windows.Forms.ToolStripRenderer>します。  
  
 新しい項目を作成し、描画のすべての側面を制御する場合は、オーバーライド、`OnPaint`メソッド。 内から`OnPaint`からメソッドを使用して、<xref:System.Windows.Forms.ToolStripRenderer>します。  
  
 既定で、<xref:System.Windows.Forms.ToolStrip>は二重のバッファリング、活用、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>設定します。  
  
#### <a name="parenting"></a>親子関係  
 コンテナーの所有権およびペアレンティングの概念は複雑で<xref:System.Windows.Forms.ToolStrip>他の Windows フォームのコンテナー コントロールよりも制御します。 オーバーフロー、各地の複数のドロップダウン リストの項目の共有などの動的なシナリオをサポートする必要があります<xref:System.Windows.Forms.ToolStrip>、項目の生成をサポートして、<xref:System.Windows.Forms.ContextMenuStrip>コントロールから。  
  
 以下に親子関係に関連するメンバーし、その使用について説明します。  
  
- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> ドロップダウン リストの項目のソースである項目にアクセスします。 似ています<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>が返されたコントロールを返す代わりに、<xref:System.Windows.Forms.ToolStripItem>します。  
  
- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> どのコントロールが、ソースであることを決定の<xref:System.Windows.Forms.ContextMenuStrip>と複数のコントロールが同じ共有<xref:System.Windows.Forms.ContextMenuStrip>します。  
  
- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> 読み取り専用のアクセサーには、<xref:System.Windows.Forms.ToolStripItem.Parent%2A>プロパティ。 親は、親表します返された現在の点で、所有者とは異なります。<xref:System.Windows.Forms.ToolStrip>項目が表示される、オーバーフロー領域にする場合があります。  
  
- <xref:System.Windows.Forms.ToolStripItem.Owner%2A> 返します、<xref:System.Windows.Forms.ToolStrip>項目コレクション持つにはには、現在が含まれています。<xref:System.Windows.Forms.ToolStripItem>します。 これは最善の方法を参照する<xref:System.Windows.Forms.ToolStrip.ImageList%2A>またはその他のプロパティを最上位<xref:System.Windows.Forms.ToolStrip>オーバーフローを処理する特別なコードを記述することがなく。  
  
#### <a name="behavior-of-inherited-controls"></a>継承されたコントロールの動作  
 継承で使用するたびに、次のコントロールがロックされています。  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
- <xref:System.Windows.Forms.MenuStrip>  
  
- <xref:System.Windows.Forms.ContextMenuStrip>  
  
- <xref:System.Windows.Forms.StatusStrip>  
  
- <xref:System.Windows.Forms.ToolStripPanel> 内のパネルを含む、<xref:System.Windows.Forms.ToolStripContainer>とも個々<xref:System.Windows.Forms.ToolStripPanel>コントロール。  
  
 たとえば、前の一覧に 1 つまたは複数のコントロールを使用して、新しい Windows フォーム アプリケーションを作成します。 1 つまたは複数のコントロールへのアクセス修飾子を設定`public`または`protected`プロジェクトをビルドするとします。 最初のフォームから継承するフォームを追加し、継承されたコントロールを選択します。 コントロールが表示されます、アクセス修飾子がかのように動作してロックされた`private`します。  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>継承の ToolStripContainer サポート  
 <xref:System.Windows.Forms.ToolStripContainer>コントロールは、次の例のような限られた継承されたシナリオをサポートします。  
  
1. 新しい Windows フォーム アプリケーションを作成します。  
  
2. フォームに <xref:System.Windows.Forms.ToolStripContainer> を追加します。  
  
3. アクセス修飾子を設定、<xref:System.Windows.Forms.ToolStripContainer>に`public`または`protected`します。  
  
4. 任意の組み合わせを追加<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、および<xref:System.Windows.Forms.ContextMenuStrip>にコントロールを<xref:System.Windows.Forms.ToolStripPanel>のリージョン、<xref:System.Windows.Forms.ToolStripContainer>します。  
  
5. プロジェクトをビルドします。  
  
6. 最初のフォームから継承したフォームを追加します。  
  
7. 選択、継承された<xref:System.Windows.Forms.ToolStripContainer>形式にします。  
  
#### <a name="inherited-behavior-of-child-controls"></a>子コントロールの継承の動作  
 前の手順を完了すると、次の継承の動作が発生します。  
  
- デザイナーで、コントロールは、継承されたアイコンが表示されます。  
  
- <xref:System.Windows.Forms.ToolStripPanel>コントロールがロックされています。 選択するか、その内容を再配置することはできません。  
  
- コントロールを追加することができます、 <xref:System.Windows.Forms.ToolStripContentPanel>、コントロールを移動、およびの子コントロールにする、<xref:System.Windows.Forms.ToolStripContentPanel>します。  
  
- フォームをビルドした後、変更を永続化します。  
  
    > [!NOTE]
    >  すべてからアクセス修飾子を削除<xref:System.Windows.Forms.ToolStripPanel>の一部であるコントロール、<xref:System.Windows.Forms.ToolStripContainer>します。 アクセス修飾子、<xref:System.Windows.Forms.ToolStripContainer>コントロール全体を制御します。  
  
#### <a name="partial-trust"></a>部分信頼  
 制限事項`ToolStrip`部分信頼で s が無許可の人物またはサービスで使用される個人情報の不慮のエントリを防ぐために設計されています。 保護対策は次のとおりです。  
  
- `ToolStripDropDown` コントロールが必要です<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>内の項目を表示する、<xref:System.Windows.Forms.ToolStripControlHost>します。 など、両方の組み込みのコントロールに適用これ<xref:System.Windows.Forms.ToolStripTextBox>、<xref:System.Windows.Forms.ToolStripComboBox>と<xref:System.Windows.Forms.ToolStripProgressBar>ユーザーが作成したことも制御します。 この要件が満たされない場合、これらの項目は表示されません。 例外をスローすることはありません。  
  
- 設定、<xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A>プロパティを`false`は許可されていませんし、キャンセル可能な<xref:System.Windows.Forms.ToolStripDropDown.Closing>イベント パラメーターは無視されます。 ドロップダウン リストの項目を表示したまま複数のキーストロークを入力できなくなります。 この要件が満たされない場合、このような項目は表示されません。 例外をスローすることはありません。  
  
- 以外の部分信頼のコンテキストで発生した場合、多くのキー入力イベントの処理は発生しません<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>します。  
  
- アクセス キーがない場合に処理される<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>が付与されていません。  
  
#### <a name="usage"></a>使用法  
 次の使用パターンに関係がある<xref:System.Windows.Forms.ToolStrip>レイアウト、キーボード操作、およびエンドユーザーの動作。  
  
- 参加している、 <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip>内の位置を変更することができます、<xref:System.Windows.Forms.ToolStripPanel>および間で<xref:System.Windows.Forms.ToolStripPanel>秒。 `Dock`プロパティは無視される場合に、<xref:System.Windows.Forms.ToolStrip.Stretch%2A>プロパティは`false`のサイズ、<xref:System.Windows.Forms.ToolStrip>に項目を追加するにつれて、<xref:System.Windows.Forms.ToolStripPanel>します。 通常、<xref:System.Windows.Forms.ToolStrip>タブ オーダーに関与しません。  
  
- ドッキング  
  
     <xref:System.Windows.Forms.ToolStrip>位置は固定でコンテナーの一方の側に配置がドッキングされている全体の端の上のサイズを拡張します。 通常、<xref:System.Windows.Forms.ToolStrip>タブ オーダーに関与しません。  
  
- 絶対配置  
  
     <xref:System.Windows.Forms.ToolStrip>によってに置かれることで、他のコントロールと同様には、<xref:System.Windows.Forms.Control.Location%2A>プロパティが固定サイズでは、し、通常タブ オーダーに参加します。  
  
#### <a name="keyboard-interaction"></a>キーボードの相互作用  
  
##### <a name="access-keys"></a>アクセス キー  
 または、ALT キーと組み合わせることで、アクセス キーは、キーボードを使用してコントロールをアクティブ化する方法の 1 つです。 <xref:System.Windows.Forms.ToolStrip> 両方の明示的および暗黙的なアクセス キーをサポートしています。 明示的な定義は、アンパサンド (&) 文字、文字の前に使用します。 暗黙の型定義内の文字の順序に基づいて一致する項目を検索しようとするアルゴリズムを使用して、指定された`Text`プロパティ。  
  
##### <a name="shortcut-keys"></a>ショートカット キー  
 によって使用されるショートカット キー、<xref:System.Windows.Forms.MenuStrip>の組み合わせを使用して、<xref:System.Windows.Forms.Keys>列挙 (これは、特定の順序ではありません) のショートカット キーを定義します。 使用することも、<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>プロパティを「削除します」ではなく"Del"の表示などのテキストのみのショートカット キーの表示。  
  
##### <a name="navigation"></a>ナビゲーション  
 ALT キーをアクティブ化、<xref:System.Windows.Forms.MenuStrip>によって示される<xref:System.Windows.Forms.Form.MainMenuStrip%2A>します。 そこから、ctrl キーを押しながら TAB はの間で移動します。<xref:System.Windows.Forms.ToolStrip>内で制御`ToolStripPanel`秒。 TAB キーと、テンキー上方向キー内の項目の間を移動、<xref:System.Windows.Forms.ToolStrip>します。 特殊なアルゴリズムでは、オーバーフロー領域のナビゲーションを処理します。 Space キーを選択、 <xref:System.Windows.Forms.ToolStripButton>、 <xref:System.Windows.Forms.ToolStripDropDownButton>、または<xref:System.Windows.Forms.ToolStripSplitButton>します。  
  
##### <a name="focus-and-validation"></a>フォーカスと検証  
 ALT キーでアクティブになると、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ToolStrip>かかるし、フォーカスされているコントロールからフォーカスを外したのどちらも通常します。 内でホストされているコントロールがあるかどうか、<xref:System.Windows.Forms.MenuStrip>またはのドロップダウン、<xref:System.Windows.Forms.MenuStrip>ユーザーが TAB キーを押したときに、コントロールがフォーカスを取得します。 一般に、 <xref:System.Windows.Forms.Control.GotFocus>、 <xref:System.Windows.Forms.Control.LostFocus>、 <xref:System.Windows.Forms.Control.Enter>、および<xref:System.Windows.Forms.Control.Leave>のイベント<xref:System.Windows.Forms.MenuStrip>キーボードによって、アクティブ化されるときに発生しない可能性があります。 このような場合は、使用して、<xref:System.Windows.Forms.MenuStrip.MenuActivate>と<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>イベント代わりにします。  
  
 既定では、<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>は`false`します。 呼び出す<xref:System.Windows.Forms.ContainerControl.Validate%2A>明示的に検証を実行するフォーム。  
  
#### <a name="layout"></a>レイアウト  
 制御する<xref:System.Windows.Forms.ToolStrip>のメンバーのいずれかを選択してレイアウト<xref:System.Windows.Forms.ToolStripLayoutStyle>で、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>プロパティ。  
  
##### <a name="stack-layouts"></a>スタック レイアウト  
 スタックの両方の end にある他の横にある項目の配置には、<xref:System.Windows.Forms.ToolStrip>します。 次の一覧には、スタック レイアウトについて説明します。  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> が既定値です。 この設定により、<xref:System.Windows.Forms.ToolStrip>でに従ってで自動的にそのレイアウトを変更する、<xref:System.Windows.Forms.ToolStrip.Orientation%2A>をドラッグして、ドッキング シナリオを処理するプロパティ。  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> レンダリング、<xref:System.Windows.Forms.ToolStrip>互いの横にある項目を垂直方向にします。  
  
- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> レンダリング、<xref:System.Windows.Forms.ToolStrip>水平方向の横にある他の項目。  
  
##### <a name="other-features-of-stack-layouts"></a>スタック レイアウトの他の機能  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 最後の決定、<xref:System.Windows.Forms.ToolStrip>アイテムを配置します。  
  
 ときに項目に収まらない場合、 <xref:System.Windows.Forms.ToolStrip>、オーバーフロー ボタンが自動的に表示されます。 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>プロパティの設定が常に、必要に応じて、またはまったくオーバーフロー領域に項目が表示されるかどうかを判断します。  
  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目をメインに配置されたかどうかを確認するに<xref:System.Windows.Forms.ToolStrip>、オーバーフロー <xref:System.Windows.Forms.ToolStrip>、または、まったく現在は表示されていない場合。 なぜ項目は表示されません一般的な原因としては、項目が、メインに収まらなかった<xref:System.Windows.Forms.ToolStrip>とその<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>プロパティに設定されました<xref:System.Windows.Forms.ToolStripItemOverflow.Never>します。  
  
 <xref:System.Windows.Forms.ToolStrip>置くことで移動可能な<xref:System.Windows.Forms.ToolStripPanel>設定とその<xref:System.Windows.Forms.ToolStrip.GripStyle%2A>に<xref:System.Windows.Forms.ToolStripGripStyle.Visible>。  
  
##### <a name="other-layout-options"></a>その他のレイアウト オプション  
 その他のレイアウト オプションは<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>と<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>します。  
  
##### <a name="flow-layout"></a>フロー レイアウト  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> レイアウトの既定値は、 <xref:System.Windows.Forms.ContextMenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、および<xref:System.Windows.Forms.ToolStripOverflow>します。 似ています、<xref:System.Windows.Forms.FlowLayoutPanel>します。 機能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトは、次のとおり。  
  
- すべての機能の<xref:System.Windows.Forms.FlowLayoutPanel>によって公開される、<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティ。 キャストする必要があります、<xref:System.Windows.Forms.LayoutSettings>クラスを<xref:System.Windows.Forms.FlowLayoutSettings>クラス。  
  
- 使用することができます、<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>行内でアイテムを揃えるためのコード内のプロパティ。  
  
- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目をメインに配置されたかどうかを確認するに<xref:System.Windows.Forms.ToolStrip>当てはまりませんでしたか。  
  
- グリップは表示されませんし、そのため、<xref:System.Windows.Forms.ToolStrip>で<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>でレイアウト スタイルを<xref:System.Windows.Forms.ToolStripPanel>移動することはできません。  
  
- <xref:System.Windows.Forms.ToolStrip>オーバーフロー ボタンは表示されず、および<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>は無視されます。  
  
##### <a name="table-layout"></a>テーブル レイアウト  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> レイアウトの既定値は、<xref:System.Windows.Forms.StatusStrip>します。 似ています<xref:System.Windows.Forms.TableLayoutPanel>します。 機能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>レイアウトは、次のとおり。  
  
- すべての機能の<xref:System.Windows.Forms.TableLayoutPanel>によって公開される、<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>プロパティ。 キャストする必要があります、<xref:System.Windows.Forms.LayoutSettings>クラスを<xref:System.Windows.Forms.TableLayoutSettings>クラス。  
  
- 使用することができます、<xref:System.Windows.Forms.ToolStripItem.Dock%2A>と<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>表のセル内のアイテムを揃えるためのコード内のプロパティ。  
  
- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティは無視されます。  
  
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベントを調査できます、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>項目をメインに配置されたかどうかを確認するに<xref:System.Windows.Forms.ToolStrip>当てはまりませんでしたか。  
  
- グリップは表示されませんし、そのため、<xref:System.Windows.Forms.ToolStrip>で<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>でレイアウト スタイルを<xref:System.Windows.Forms.ToolStripPanel>移動することはできません。  
  
- <xref:System.Windows.Forms.ToolStrip>オーバーフロー ボタンは表示されず、および<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>は無視されます。  
  
## <a name="toolstripitem"></a>ToolStripItem  
 次のトピックについて説明します<xref:System.Windows.Forms.ToolStripItem>とそこから派生するコントロール。  
  
 <xref:System.Windows.Forms.ToolStripItem> すべての項目の抽象基本クラスには、<xref:System.Windows.Forms.ToolStrip>します。 次のオブジェクト モデルの表示、<xref:System.Windows.Forms.ToolStripItem>継承階層。  
  
 ![ToolStripItem オブジェクト モデルを示す図。](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> クラスから直接継承するか<xref:System.Windows.Forms.ToolStripItem>が間接的に継承または<xref:System.Windows.Forms.ToolStripItem>を通じて<xref:System.Windows.Forms.ToolStripControlHost>または<xref:System.Windows.Forms.ToolStripDropDownItem>します。  
  
 <xref:System.Windows.Forms.ToolStripItem> コントロールを含める必要があります、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.StatusStrip>、または<xref:System.Windows.Forms.ContextMenuStrip>フォームに直接追加することはできません。 さまざまなコンテナー クラスが適切なサブセットを格納するように設計<xref:System.Windows.Forms.ToolStripItem>コントロール。  
  
 次の表では、ストック<xref:System.Windows.Forms.ToolStripItem>コントロールと最適に表示するコンテナー。 いずれかが<xref:System.Windows.Forms.ToolStrip>項目は、いずれかでホストできる<xref:System.Windows.Forms.ToolStrip>-派生したコンテナーでは、これらの項目が、次のコンテナーで最適に表示するように設計。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> デザイナーのツールボックスには表示されません。  
  
|含まれるアイテム|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|はい|×|×|×|[はい]|  
|<xref:System.Windows.Forms.ToolStripComboBox>|はい|はい|[はい]|×|[はい]|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|[はい]|×|×|[はい]|はい|  
|<xref:System.Windows.Forms.ToolStripLabel>|[はい]|×|×|[はい]|はい|  
|<xref:System.Windows.Forms.ToolStripSeparator>|はい|はい|[はい]|×|[はい]|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|[はい]|×|×|[はい]|はい|  
|<xref:System.Windows.Forms.ToolStripTextBox>|はい|はい|[はい]|×|はい|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|×|[はい]|[はい]|×|×|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|×|×|×|はい|×|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|はい|×|×|はい|×|  
|<xref:System.Windows.Forms.ToolStripControlHost>|[はい]|[はい]|×|[はい]|[はい]|  
  
### <a name="toolstripbutton"></a>オブジェクト  
 <xref:System.Windows.Forms.ToolStripButton> ボタンの項目は、<xref:System.Windows.Forms.ToolStrip>します。 これを表示するにはさまざまな境界線のスタイル、およびを表し、操作状態をアクティブ化に使用できます。 既定でフォーカスを持つことを定義することもできます。  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel>ラベル機能を提供します<xref:System.Windows.Forms.ToolStrip>コントロール。 <xref:System.Windows.Forms.ToolStripLabel>は似ています、<xref:System.Windows.Forms.ToolStripButton>既定でフォーカスが移動をしないと、プッシュまたは強調表示されているとしてレンダリングされません。  
  
 <xref:System.Windows.Forms.ToolStripLabel> ホストされている項目としては、アクセス キーをサポートしています。  
  
 使用して、 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>と<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>プロパティを<xref:System.Windows.Forms.ToolStripLabel>でリンクの制御をサポートする、<xref:System.Windows.Forms.ToolStrip>します。  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> バージョンは、<xref:System.Windows.Forms.ToolStripLabel>内使用専用に設計された<xref:System.Windows.Forms.StatusStrip>します。 特殊な機能が含まれます<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>、 <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>、および<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>します。  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator>をツールバーまたはメニューで、印刷の向きに応じて、垂直方向または水平方向の行を追加します。 グループ化やメニューなどの項目の間に違いを提供します。  
  
 追加することができます、<xref:System.Windows.Forms.ToolStripSeparator>ドロップダウン リストから選択してデザイン時にします。 ただしも自動的に作成できます、<xref:System.Windows.Forms.ToolStripSeparator>デザイナー テンプレート ノードまたはハイフン (-) を入力して、<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>メソッド。  
  
### <a name="toolstripcontrolhost"></a>Toolstripcontrolhost を使用して  
 <xref:System.Windows.Forms.ToolStripControlHost> 抽象基本クラスは、 <xref:System.Windows.Forms.ToolStripComboBox>、 <xref:System.Windows.Forms.ToolStripTextBox>、および<xref:System.Windows.Forms.ToolStripProgressBar>します。 <xref:System.Windows.Forms.ToolStripControlHost> 2 つの方法で、カスタム コントロールを含む、他のコントロールをホストできます。  
  
- 構築、<xref:System.Windows.Forms.ToolStripControlHost>から派生するクラスを含む<xref:System.Windows.Forms.Control>します。 完全にホストされているコントロールとプロパティにアクセスするにキャストする必要があります、<xref:System.Windows.Forms.ToolStripControlHost.Control%2A>プロパティを実際にクラスを表します。  
  
- 拡張<xref:System.Windows.Forms.ToolStripControlHost>、継承されたクラスの既定のコンス トラクター内から派生したクラスを渡して基底クラスのコンス トラクターを呼び出すと<xref:System.Windows.Forms.Control>します。 このオプションを使用して、簡単にアクセスでの一般的なコントロール メソッドとプロパティをラップできます、<xref:System.Windows.Forms.ToolStrip>します。  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ComboBox>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>します。 ホストされるコントロールのプロパティとイベントのサブセットが公開される、<xref:System.Windows.Forms.ToolStripComboBox>レベルが、基になる<xref:System.Windows.Forms.ComboBox>コントロールがから完全にアクセスできる、<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>プロパティ。  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> <xref:System.Windows.Forms.TextBox>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>します。 ホストされるコントロールのプロパティとイベントのサブセットが公開される、<xref:System.Windows.Forms.ToolStripTextBox>レベルが、基になる<xref:System.Windows.Forms.TextBox>コントロールがから完全にアクセスできる、<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>プロパティ。  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> <xref:System.Windows.Forms.ProgressBar>でホストするために最適化された、<xref:System.Windows.Forms.ToolStrip>します。 ホストされるコントロールのプロパティとイベントのサブセットが公開される、<xref:System.Windows.Forms.ToolStripProgressBar>レベルが、基になる<xref:System.Windows.Forms.ProgressBar>コントロールがから完全にアクセスできる、<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>プロパティ。  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> 抽象基本クラスは、 <xref:System.Windows.Forms.ToolStripMenuItem>、 <xref:System.Windows.Forms.ToolStripDropDownButton>、および<xref:System.Windows.Forms.ToolStripSplitButton>項目を直接またはドロップダウン リストのコンテナーのホストの追加項目をホストすることができます。 これを行う、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>プロパティを<xref:System.Windows.Forms.ToolStripDropDown>と設定、<xref:System.Windows.Forms.ToolStrip.Items%2A>のプロパティ、<xref:System.Windows.Forms.ToolStripDropDown>します。 経由で直接これらのドロップダウン項目へのアクセス、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>プロパティ。  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.ToolStripDropDownItem>と連動する<xref:System.Windows.Forms.ToolStripDropDownMenu>と<xref:System.Windows.Forms.ContextMenuStrip>メニューの強調表示、レイアウト、および列の特別な構成を処理します。  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> 次のよう<xref:System.Windows.Forms.ToolStripButton>が、ユーザーがクリックしたとき、ドロップダウン領域を示しています。 設定して、下矢印を表示または非表示、<xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>プロパティ。 <xref:System.Windows.Forms.ToolStripDropDownButton> ホストを<xref:System.Windows.Forms.ToolStripOverflowButton>オーバーフローする項目を表示する、<xref:System.Windows.Forms.ToolStrip>します。  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> ボタンとドロップダウン ボタンの機能を結合します。  
  
 使用して、<xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>同期プロパティ、<xref:System.Windows.Forms.Control.Click>ボタンに表示する項目を選択したドロップダウン リスト項目のイベント。  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem ジェネリック機能  
 <xref:System.Windows.Forms.ToolStripItem> 次の汎用的な機能とコントロールを継承するためのオプションを提供します。  
  
- コア イベント  
  
- 画像処理  
  
- アラインメント  
  
- テキストとイメージの関係  
  
- 表示スタイル  
  
#### <a name="core-events"></a>コア イベント  
 <xref:System.Windows.Forms.ToolStripItem> コントロールは、独自の をクリックして、マウス、および描画イベントでは、受信され、前処理もいくつかのキーボードを実行できます。  
  
#### <a name="image-handling"></a>画像処理  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>、 <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>、および<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>プロパティは、画像処理のさまざまな側面に関連します。 内のイメージを使用して、<xref:System.Windows.Forms.ToolStrip>コントロール直接これらのプロパティを設定するか、実行時間 – 専用に設定して<xref:System.Windows.Forms.ToolStrip.ImageList%2A>プロパティ。  
  
 イメージのスケーリングは両方のプロパティの相互作用によって決定されます<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripItem>、次のようにします。  
  
- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> イメージの組み合わせによって決定される最終的なイメージの小数点以下桁数<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>設定と、コンテナーの<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>設定します。  
  
    - 場合<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>は`true`(既定値) と<xref:System.Windows.Forms.ToolStripItemImageScaling>は<xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>、イメージのスケーリングは行われません、および<xref:System.Windows.Forms.ToolStrip>サイズは最大のアイテムまたは所定の最小サイズの。  
  
    - 場合<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>は`false`と<xref:System.Windows.Forms.ToolStripItemImageScaling>は<xref:System.Windows.Forms.ToolStripItemImageScaling.None>、どちらのイメージも<xref:System.Windows.Forms.ToolStrip>スケーリングが発生します。  
  
#### <a name="alignment"></a>アラインメント  
 値、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティの最後の決定、<xref:System.Windows.Forms.ToolStrip>で項目が表示されます。 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティの場合にのみ動作のレイアウト スタイル、<xref:System.Windows.Forms.ToolStrip>スタック オーバーフローの値のいずれかに設定されます。  
  
 項目を上に配置されます、<xref:System.Windows.Forms.ToolStrip>項目のコレクション内の項目が表示される順序で。 プログラムで項目のレイアウトを変更するには、使用、<xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>コレクション内の項目を移動するメソッド。 このメソッドは、アイテムを移動しますが、複製はしません。  
  
#### <a name="text-and-image-relationship"></a>テキストとイメージのリレーションシップ  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>プロパティのテキストに対するイメージの相対的な位置を定義する、<xref:System.Windows.Forms.ToolStripItem>します。 イメージ、テキスト、またはその両方を持たないアイテムは特殊なケースとして扱われますように、<xref:System.Windows.Forms.ToolStripItem>不足している要素または要素の空白部分には表示されません。  
  
#### <a name="display-style"></a>表示スタイル  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 目的のみを表示するときに、項目のテキストとイメージのプロパティの値を設定することができます。 これは通常、別のコンテキストで同じ項目を表示するときにのみ表示スタイルを変更するのに使用されます。  
  
## <a name="accessory-classes"></a>アクセサリ クラス  
 さまざまなその他の機能を提供するクラスは次のとおりです。  
  
- <xref:System.Windows.Forms.ToolStripManager> サポート<xref:System.Windows.Forms.ToolStrip>-マージ、設定、およびレンダラー オプションなど、アプリケーション全体のタスクに関連します。  
  
- <xref:System.Windows.Forms.ToolStripRenderer> 特定のスタイルまたはテーマを適用することができます、<xref:System.Windows.Forms.ToolStrip>簡単にします。  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ペンとブラシの色の置き換え可能なテーブルに基づいて作成します (<xref:System.Windows.Forms.ProfessionalColorTable>)。  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer> システム カラーとフラットな visual スタイルを適用<xref:System.Windows.Forms.ToolStrip>アプリケーション。  
  
- <xref:System.Windows.Forms.ToolStripContainer> ような<xref:System.Windows.Forms.SplitContainer>します。 4 つの側がドッキングされたパネルを使用して (インスタンスの<xref:System.Windows.Forms.ToolStripPanel>) と 1 つの中央のパネル (インスタンスの<xref:System.Windows.Forms.ToolStripContentPanel>) 一般的な配置を作成します。 サイド パネルを削除することはできませんが、非表示にすることができます。 削除も、中央のパネルを非表示にします。 1 つまたは複数配置できます<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、または<xref:System.Windows.Forms.StatusStrip>サイド パネルのコントロールは、他のコントロールの中央のパネルを使用できます。 <xref:System.Windows.Forms.ToolStripContentPanel>に一貫した外観にフォームの本文をサポートするレンダラーを取得することもできます。 <xref:System.Windows.Forms.ToolStripContainer> マルチ ドキュメント インターフェイス (MDI) はサポートされません。  
  
- <xref:System.Windows.Forms.ToolStripPanel> 移動および配置するための領域を提供します<xref:System.Windows.Forms.ToolStrip>コントロール。 1 つだけのパネルを使用するには、そのために選択した場合と<xref:System.Windows.Forms.ToolStripPanel>は MDI のシナリオに適しています。  
  
## <a name="see-also"></a>関連項目

- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
- [MenuStrip コントロール](menustrip-control-windows-forms.md)
- [StatusStrip コントロール](statusstrip-control.md)
- [ContextMenuStrip コントロール](contextmenustrip-control.md)
- [BindingNavigator コントロール](bindingnavigator-control-windows-forms.md)
