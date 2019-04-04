---
title: Windows フォーム アプリケーションの基礎 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 99aa61d921217ab5638172a54697054e8421fd5c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972678"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows フォーム アプリケーションの基礎 (Visual Basic)
Visual Basic の重要な部分は、ユーザーのコンピューターでローカルに実行する Windows フォーム アプリケーションを作成する機能です。 Visual Studio を使用して、Windows フォームを使用すると、アプリケーションとユーザー インターフェイスを作成することができます。 クラスを Windows フォーム アプリケーションが構築された、<xref:System.Windows.Forms>名前空間。  
  
## <a name="designing-windows-forms-applications"></a>設計の Windows フォーム アプリケーション  
 Visual Studio では、Windows フォームと Windows サービス アプリケーションを作成できます。 詳細については、次のトピックを参照してください。  
  
-   [Windows フォームの概要](../../../framework/winforms/getting-started-with-windows-forms.md)します。 作成し、Windows フォームをプログラミングする方法についてを説明します。  
   
-   [Windows フォーム コントロール](../../../framework/winforms/controls/index.md)します。 Windows フォーム コントロールの使用の詳細を示すトピックのコレクションです。  
  
-   [Windows サービス アプリケーション](../../../framework/windows-services/index.md)します。 Windows サービスを作成する方法を説明するトピックを示します。  
  
## <a name="building-rich-interactive-user-interfaces"></a>リッチで対話型のユーザー インターフェイスの構築  
 Windows フォームのスマート クライアント コンポーネントは、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、読み取りと書き込みをファイル システムなどの一般的なアプリケーション タスクを有効にする管理対象のライブラリのセット。 Visual Studio などの開発環境を使用して、作成を情報を表示し、ユーザーからの入力を要求、通信する Windows フォーム アプリケーションをリモート コンピューターで、ネットワーク経由でします。  
  
 Windows フォームでは、フォームは、ユーザーに情報を表示するビジュアル サーフェイスです。 通常、Windows フォーム アプリケーションをビルドするには、コントロールをフォームに配置し、マウス クリックやキーの押下などのユーザー アクションに対する応答を開発します。 "*コントロール*" は、データを表示したりデータ入力を受け入れたりする独立したユーザー インターフェイス (UI) 要素です。  
  
### <a name="events"></a>イベント  
 ユーザーがフォームまたはそのコントロールの 1 つに、イベントが生成されます。 アプリケーションは、コードを使用してこれらのイベントに反応し、イベントが発生したときにそのイベントを処理します。 詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)」を参照してください。  
  
### <a name="controls"></a>コントロール  
 Windows フォームには、さまざまなフォームに配置できるコントロールが含まれています。 テキスト ボックス、ボタン、ドロップダウン ボックス、ラジオ ボタン、および Web ページを表示するコントロール。 フォーム上で使用できるすべてのコントロールの一覧については、「[Windows フォームで使用するコントロール](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。 既存のコントロールがニーズを満たしていない場合に、Windows フォームは <xref:System.Windows.Forms.UserControl> クラスを使用した独自のカスタム コントロールの作成もサポートしています。  
  
 Windows フォームには、Microsoft Office のようなハイエンド アプリケーションの機能をエミュレートする豊富な UI コントロールが用意されています。 使用して、<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.MenuStrip>コントロール、ツールバーとメニュー テキストとイメージを格納し、サブメニューの表示、テキスト ボックスやコンボ ボックスなどの他のコントロールをホストを作成できます。  
  
 Visual Studio のドラッグ アンド ドロップのフォーム デザイナー、Windows フォーム アプリケーションを簡単に作成できます。 単にカーソルをコントロールを選択し、フォームの希望の位置に配置します。 グリッド線と「スナップ線」などのツールがデザイナーによって、簡単にコントロールを配置します。 Visual Studio を使用するか、またはコマンドラインでコンパイルするかどうかを使用できます、 <xref:System.Windows.Forms.FlowLayoutPanel>、<xref:System.Windows.Forms.TableLayoutPanel>と<xref:System.Windows.Forms.SplitContainer>高度なを作成するコントロールは、最小限の時間と労力でレイアウトを形成します。  
  
### <a name="custom-ui-elements"></a>カスタムの UI 要素  
 最後に、独自のカスタム UI 要素を作成する必要があります、<xref:System.Drawing>名前空間には、すべての線、円、およびその他の図形をフォームに直接レンダリングする必要があるクラスが含まれています。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|解決方法|  
|--------|---------|  
|Visual Studio で新しい Windows フォーム アプリケーションを作成します。|[チュートリアル 1:ピクチャ ビューアーを作成します。](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|  
|フォーム上のコントロールを使用します。|[方法: Windows フォームにコントロールを追加します。](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|使用したグラフィックを作成します。 <xref:System.Drawing>|[グラフィックス プログラミングについて](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|カスタム コントロールを作成します。|[方法: UserControl クラスを継承します。](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>データの表示と操作  
 多くのアプリケーションは、データベース、XML ファイル、XML Web サービス、またはその他のデータ ソースからデータを表示する必要があります。 Windows フォームは、柔軟なコントロールと呼ばれる、<xref:System.Windows.Forms.DataGridView>のすべてのデータが独自のセルを占有するので、従来の行と列の形式で表形式のデータを表示するためのコントロール。 使用して<xref:System.Windows.Forms.DataGridView>個々 のセルの外観をカスタマイズ、任意の行と列のロックおよびその他の機能の 1 つのセル内で複雑なコントロールを表示することができます。  
  
 ネットワーク経由のデータ ソースへの接続は、Windows フォームのスマート クライアントを使用すればシンプルなタスクです。 <xref:System.Windows.Forms.BindingSource>コンポーネント、Visual Studio 2005 での Windows フォームを新規と[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)]データ ソースへの接続を表し、前後のレコードに移動し、レコードの編集、保存、コントロールにデータ バインディングのメソッドを公開します変更を元に戻します。 
  <xref:System.Windows.Forms.BindingNavigator> コントロールは、ユーザーがレコード間を移動する <xref:System.Windows.Forms.BindingSource> コンポーネントに対して、シンプルなインターフェイスを提供します。  
  
### <a name="data-bound-controls"></a>データ バインド コントロール  
 プロジェクトのデータベース、Web サービス、およびオブジェクトなどのデータ ソースを表示するデータ ソース ウィンドウを使用して簡単にデータ バインド コントロールを作成することができます。 このウィンドウからプロジェクトのフォームに項目をドラッグして、データ バインド コントロールを作成できます。 また、[データ ソース] ウィンドウから既存のコントロールにオブジェクトをドラッグして、データに既存のコントロールをバインドすることもできます。  
  
### <a name="settings"></a>設定  
 別の種類のデータ バインディングの Windows フォームで管理することができますが、設定します。 ほとんどのスマート クライアント アプリケーションは、フォームの前回のサイズなどのランタイム状態に関する情報を保持し、保存したファイルの既定の場所などのユーザー設定データを保持する必要があります。 アプリケーション設定機能には、クライアント コンピューターの両方の種類の設定を格納する簡単な方法を提供することでこれらの要件が対応します。 Visual Studio またはコード エディターを使用する定義と、これらの設定は XML として永続化し、自動的に実行時にメモリに読み取る。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|解決方法|  
|--------|---------|  
|使用して、<xref:System.Windows.Forms.BindingSource>コンポーネント|[方法: デザイナーを使用して、BindingSource コンポーネントを使用した Windows フォーム コントロールをバインドします。](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|使用[!INCLUDE[vstecado](~/includes/vstecado-md.md)]データ ソース|[方法: 並べ替えとフィルター処理で ADO.NET データを Windows フォーム BindingSource コンポーネント](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|データ ソース ウィンドウを使用します。|[チュートリアル: Windows フォームでデータの表示](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>クライアント コンピューターにアプリケーションを配置する  
 アプリケーションを作成するとする必要がありますに送信するユーザーをインストールして、自分のクライアント コンピューターで実行できます。 使用して、[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]テクノロジ、ほんの数回のクリックを使用して Visual Studio 内からアプリケーションを展開し、Web 上のアプリケーションを指す URL をユーザーに提供します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] すべての要素と、アプリケーションでの依存関係を管理し、により、アプリケーションがクライアント コンピューターに正しくインストールされているようになります。  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] アプリケーションは、ユーザーがネットワークに接続されている場合にのみ実行するか、オンラインとオフラインの両方で実行するかを構成することができます。 アプリケーションがオフラインの操作をサポートする必要がありますを指定すると[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]、ユーザーのアプリケーションにリンクを追加します。**開始**] メニューの [せず、URL を使用して開くことができるようにします。  
  
 アプリケーションを更新するときに、新しい配置マニフェストとアプリケーションの新しいコピーを Web サーバーに発行します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 検出が使用可能な更新プログラムがあることと、ユーザーのインストールをアップグレード古いアセンブリを更新するカスタム プログラミングは必要ありません。  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] の概要については、「[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|解決方法|  
|--------|---------|  
|アプリケーションをデプロイします。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [チュートリアル: ClickOnce アプリケーションを手動で配置する](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|更新プログラム、[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]展開|[方法: ClickOnce アプリケーションの更新プログラムを管理する](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|セキュリティを管理します。 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[方法: [ClickOnce セキュリティ設定を有効にする]](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>その他のコントロールおよび機能  
 Windows フォームには、ダイアログ ボックスの作成、ヘルプやドキュメントの印刷や追加、アプリケーションの複数言語へのローカライズのサポートなど、一般的なタスクを高速で簡単に実装できる機能が他にも多数あります。 さらに、Windows フォームは、の堅牢なセキュリティ システムに依存しています。、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]、をお客様により安全なアプリケーションをリリースできます。  
  
 これらの機能を使用する手順については、次のヘルプ トピックを参照してください。  
  
|目的|解決方法|  
|--------|---------|  
|フォームのコンテンツを印刷します。|[方法: Windows フォームでグラフィックスを印刷します。](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [方法: Windows フォームで複数ページのテキスト ファイルを印刷します。](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Windows フォームのセキュリティについての詳細|[Windows フォームのセキュリティの概要](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Windows フォームの概要](../../../framework/winforms/windows-forms-overview.md)
- [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)
