---
title: Windows フォームの概要
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 71bf50bdcf058e94981dc5df4731b5d32dcc2069
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487202"
---
# <a name="windows-forms-overview"></a>Windows フォームの概要

次の概要では、スマート クライアント アプリケーションの利点、Windows フォームのプログラミングの主な機能について説明し、Windows フォームを使用して今日の企業とエンドユーザーのニーズを満たすスマート クライアントを構築する方法を示します。

## <a name="windows-forms-and-smart-client-apps"></a>Windows フォームおよびスマート クライアント アプリ

 Windows フォームを使用して、スマート クライアントを開発します。 *スマート クライアント*は、配置と更新が容易で、インターネットに接続しているときも切断しているときも動作し、従来の Windows ベースのアプリケーションよりも安全な方法でローカル コンピューター上のリソースにアクセスできる、リッチなグラフィックスのアプリケーションです。

### <a name="build-rich-interactive-user-interfaces"></a>リッチで対話型ユーザー インターフェイスを構築します。

 Windows フォームは、一連の読み取りと書き込みをファイル システムなどの一般的なアプリケーション タスクを簡略化するマネージ ライブラリ、.NET framework のスマート クライアント テクノロジです。 Visual Studio などの開発環境を使用する場合は、ネットワーク経由でリモート コンピューターを情報を表示し、ユーザーからの入力を要求、通信する Windows フォームのスマート クライアント アプリケーションを作成できます。

 Windows フォームでは、"*フォーム*" はユーザーに情報を表示するビジュアル サーフェイスです。 通常は、コントロールをフォームに追加して、マウスのクリックやキーの押下などのユーザー アクションへの応答を開発することで、Windows フォーム アプリケーションを開発します。 "*コントロール*" は、データを表示したりデータ入力を受け入れたりする独立したユーザー インターフェイス (UI) 要素です。

 ユーザーがフォームまたはそのコントロールのいずれかにアクションを実行すると、そのアクションがイベントを生成します。 アプリケーションは、コードを使用してこれらのイベントに反応し、イベントが発生したときにそのイベントを処理します。 詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](creating-event-handlers-in-windows-forms.md)」を参照してください。

 Windows フォームには、テキスト ボックス、ボタン、ドロップダウン ボックス、ラジオ ボタン、Web ページなどを表示するコントロールなど、フォームに追加できるさまざまなコントロールが含まれています。 フォーム上で使用できるすべてのコントロールの一覧については、「[Windows フォームで使用するコントロール](./controls/controls-to-use-on-windows-forms.md)」を参照してください。 既存のコントロールがニーズを満たしていない場合に、Windows フォームは <xref:System.Windows.Forms.UserControl> クラスを使用した独自のカスタム コントロールの作成もサポートしています。

 Windows フォームには、Microsoft Office のようなハイエンド アプリケーションの機能をエミュレートする豊富な UI コントロールが用意されています。 <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.MenuStrip> コントロールを使用する場合、テキストとイメージを含むツールバーとメニューを作成したり、サブメニューを表示したり、テキスト ボックスやコンボ ボックスなど、その他のコントロールをホストしたりできます。

 ドラッグ アンド ドロップで**Windows フォーム デザイナー** Visual Studio で、Windows フォーム アプリケーションを簡単に作成できます。 コントロールをカーソルで選択して、フォームの任意の場所に追加するだけです。 デザイナーがグリッド線やスナップ線などのツールを提供するので、コントロールの調整が楽になります。 Visual Studio を使用するか、またはコマンドラインでコンパイルするかどうかを使用できます、 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel>と<xref:System.Windows.Forms.SplitContainer>短時間で高度なを作成するコントロールのフォーム レイアウト。

 最後に、独自のカスタム UI 要素を作成する必要がある場合は、<xref:System.Drawing> 名前空間に、線、円、およびその他の図形をフォーム上に直接表示するクラスが多数含まれています。

> [!NOTE]
> Windows フォーム コントロールは、アプリケーション ドメイン間でマーシャリングするよう設計されていません。 このため、<xref:System.MarshalByRefObject> の <xref:System.Windows.Controls.Control> 基本型で可能であるように見えても、Microsoft は、<xref:System.AppDomain> 境界間の Windows フォーム コントロールの引き渡しはサポートしていません。 複数のアプリケーション ドメインを持つ Windows フォーム アプリケーションは、Windows フォーム コントロールがアプリケーション ドメインの境界を越えて渡されない限りサポートされます。

#### <a name="create-forms-and-controls"></a>フォームとコントロールを作成します。

これらの機能を使用する方法の手順を追った説明については、次のヘルプ トピックを参照してください。

|説明|ヘルプ トピック|
|-----------------|----------------|
|フォーム上のコントロールを使用する|[方法: Windows フォームにコントロールを追加します。](./controls/how-to-add-controls-to-windows-forms.md)|
|<xref:System.Windows.Forms.ToolStrip> コントロールを使用する|[方法: デザイナーを使用して標準アイテムで基本的な ToolStrip を作成します。](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|<xref:System.Drawing> を使用してグラフィックスを作成する|[グラフィックス プログラミングについて](./advanced/getting-started-with-graphics-programming.md)|
|カスタム コントロールの作成|[方法: UserControl クラスを継承します。](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>表示および操作データ
 多くのアプリケーションは、データベース、XML ファイル、XML Web サービス、またはその他のデータ ソースからデータを表示する必要があります。 Windows フォームは、従来の行と列の形式である、表形式のデータを表示するために、<xref:System.Windows.Forms.DataGridView> コントロールという名前の柔軟なコントロールを提供しているため、すべてのデータが独自のセルを占有します。 <xref:System.Windows.Forms.DataGridView> を使用すると、個別のセルの外観のカスタマイズ、任意の列と行のその場でのロック、セルの内部の複雑なコントロールの表示や、その他の機能が可能になります。

 ネットワーク経由のデータ ソースへの接続は、Windows フォームのスマート クライアントを使用すればシンプルなタスクです。 <xref:System.Windows.Forms.BindingSource>コンポーネントが、データ ソースへの接続を表し、メソッド前または次のレコードに移動し、レコードの編集、変更を保存するときに、コントロールにバインド データを公開しますが、元のソースをバックアップします。 <xref:System.Windows.Forms.BindingNavigator> コントロールは、ユーザーがレコード間を移動する <xref:System.Windows.Forms.BindingSource> コンポーネントに対して、シンプルなインターフェイスを提供します。

 [データ ソース] ウィンドウを使用すると、データ バインド コントロールを簡単に作成できます。 ウィンドウには、プロジェクト内のデータベース、Web サービス、オブジェクトなどのデータ ソースが表示されます。 このウィンドウからプロジェクトのフォームに項目をドラッグして、データ バインド コントロールを作成できます。 また、[データ ソース] ウィンドウから既存のコントロールにオブジェクトをドラッグして、データに既存のコントロールをバインドすることもできます。

 Windows フォームで管理できる別の種類のデーデータ バインドは "*設定*" です。 ほとんどのスマート クライアント アプリケーションは、フォームの前回のサイズなどの実行時の状態に関する情報を保持し、保存されたファイルの既定の場所などのユーザー設定のデータを保持する必要があります。 アプリケーション設定機能は、クライアント コンピューターに両方の種類の設定を保存する簡単な方法を提供することで、こうした要件に対応します。 Visual Studio またはコード エディターを使用してこれらの設定を定義した後、設定が XML として永続化され、自動的に実行時にメモリに読み取る。

#### <a name="display-and-manipulate-data"></a>表示および操作データ

これらの機能を使用する方法の手順を追った説明については、次のヘルプ トピックを参照してください。

|説明|ヘルプ トピック|
|-----------------|----------------|
|<xref:System.Windows.Forms.BindingSource> コンポーネントを使用する|[方法: デザイナーを使用して、BindingSource コンポーネントを使用した Windows フォーム コントロールをバインドします。](./controls/bind-wf-controls-with-the-bindingsource.md)|
|ADO.NET データ ソースの操作|[方法: 並べ替えとフィルター処理で ADO.NET データを Windows フォーム BindingSource コンポーネント](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|[データ ソース] ウィンドウを使用する|[Visual Studio でのデータへの Windows フォーム コントロールのバインド](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|アプリケーション設定を使用する|[方法: アプリケーション設定を作成します。](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>クライアント コンピューターにアプリを展開します。

アプリケーションを作成した後、ユーザーにアプリケーションを送信して、独自のクライアント コンピューターにインストールして実行できるようにする必要があります。 ClickOnce テクノロジを使用する場合は、ほんの数回のクリックを使用して Visual Studio 内からアプリケーションを展開し、Web 上のアプリケーションを指す URL をユーザーに提供できます。 ClickOnce では、すべての要素と、アプリケーション内の依存関係を管理し、クライアント コンピューターのアプリケーションが正しくインストールされていることにより、します。

ClickOnce アプリケーションは、ユーザーがネットワークに接続されている場合にのみ実行するか、オンラインの両方を実行する構成され、オフラインにできます。 ClickOnce が、ユーザーのアプリケーションへのリンクを追加アプリケーションがオフラインの操作をサポートする必要がありますを指定すると**開始**メニュー。 ユーザーは、URL を使用せずにアプリケーションを開くことができます。

アプリケーションを更新するときに、新しい配置マニフェストとアプリケーションの新しいコピーを Web サーバーに発行します。 ClickOnce が使用可能な更新プログラムと、ユーザーのインストールのアップグレードがあることを検出します。古いアセンブリを更新するカスタム プログラミングは必要ありません。

#### <a name="deploy-clickonce-apps"></a>ClickOnce アプリを展開します。

ClickOnce に完全な概要については、次を参照してください。 [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment)します。 これらの機能を使用する方法の手順を追った説明については、次のヘルプ トピックを参照してください。

|説明|ヘルプ トピック|
|-----------------|----------------|
|ClickOnce を使用してアプリケーションを展開します。|[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [チュートリアル: ClickOnce アプリケーションを手動で配置する](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|ClickOnce 配置の更新|[方法: ClickOnce アプリケーションの更新プログラムを管理する](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|ClickOnce によるセキュリティを管理|[方法: [ClickOnce セキュリティ設定を有効にする]](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>その他のコントロールと機能

Windows フォームには、ダイアログ ボックスの作成、ヘルプやドキュメントの印刷や追加、アプリケーションの複数言語へのローカライズのサポートなど、一般的なタスクを高速で簡単に実装できる機能が他にも多数あります。 さらに、Windows フォームは、.NET Framework の堅牢なセキュリティ システムに依存します。 このシステムを使用することで、顧客により安全なアプリケーションをリリースできます。

#### <a name="implement-other-controls-and-features"></a>その他のコントロールと機能を実装します。

これらの機能を使用する方法の手順を追った説明については、次のヘルプ トピックを参照してください。

|説明|ヘルプ トピック|
|-----------------|----------------|
|フォームの内容を印刷する|[方法: Windows フォームでグラフィックスを印刷します。](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [方法: Windows フォームで複数ページのテキスト ファイルを印刷します。](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Windows フォームのセキュリティについての詳細|[Windows フォームのセキュリティの概要](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>関連項目

- [Windows フォームについて](getting-started-with-windows-forms.md)
- [新しい Windows フォームの作成](creating-a-new-windows-form.md)
- [ToolStrip コントロールの概要](./controls/toolstrip-control-overview-windows-forms.md)
- [DataGridView コントロールの概要](./controls/datagridview-control-overview-windows-forms.md)
- [BindingSource コンポーネントの概要](./controls/bindingsource-component-overview.md)
- [アプリケーション設定の概要](./advanced/application-settings-overview.md)
- [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)
