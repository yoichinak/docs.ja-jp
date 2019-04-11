---
title: さまざまなカスタム コントロール
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: 765befcf88247e4b2101b13c4937352ba4b070fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170706"
---
# <a name="varieties-of-custom-controls"></a>さまざまなカスタム コントロール
.NET Framework を使用して、新しいコントロールを開発し、実装できます。 継承によって、使い慣れたユーザー コントロールや既存のコントロールの機能を拡張できます。 また、独自の描画を実行するカスタム コントロールを作成することもできます。  
  
 作成するコントロールの種類を決めるときに、判断に迷うことがあります。 このトピックでは、継承できる各種コントロールの違いを示し、プロジェクトに合わせて特定の種類のコントロールを選択する方法について説明します。  
  
> [!NOTE]
>  Web フォームで使用するコントロールを作成する方法については、「[カスタム ASP.NET サーバー コントロールの開発](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))」を参照してください。  
  
## <a name="base-control-class"></a>基本コントロール クラス  
 <xref:System.Windows.Forms.Control>クラスは、Windows フォーム コントロールの基本クラス。 このクラスは、Windows フォーム アプリケーションでのビジュアル表示に必要なインフラストラクチャを提供します。  
  
 <xref:System.Windows.Forms.Control>クラスは、Windows フォーム アプリケーションでのビジュアル表示を提供する、次のタスクを実行します。  
  
-   ウィンドウ ハンドルを公開する。  
  
-   メッセージ ルーティングを管理する。  
  
-   マウス イベントとキーボード イベント、および他のさまざまなユーザー インターフェイス イベントを提供する。  
  
-   高度なレイアウト機能を提供する。  
  
-   ビジュアルの表示に固有の多くのプロパティを含む<xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Height%2A>、および<xref:System.Windows.Forms.Control.Width%2A>します。  
  
-   Windows フォーム コントロールが Microsoft® ActiveX® コントロールとして機能するために必要なセキュリティとスレッドのサポートを提供する。  
  
 インフラストラクチャの大部分は基本クラスによって提供されるため、独自の Windows フォーム コントロールを比較的簡単に開発できます。  
  
## <a name="kinds-of-controls"></a>コントロールの種類  
 Windows フォームは、*複合*、*拡張*、*カスタム*の 3 種類のユーザー定義コントロールをサポートします。 以下のセクションでは、各種コントロールについて説明し、プロジェクトで使用する種類を選択する際の推奨事項を示します。  
  
### <a name="composite-controls"></a>複合コントロール  
 複合コントロールは、共通のコンテナーにカプセル化された Windows フォーム コントロールのコレクションです。 この種のコントロールは、*ユーザー コントロール*とも呼ばれます。 含まれているコントロールは、*内在コントロール*と呼ばれます。  
  
 複合コントロールは、含まれている各 Windows フォーム コントロールに関連する固有の機能をすべて保持し、それらのプロパティを選択的に公開してバインドできます。 また、開発者側での追加作業を必要としない多数の既定のキーボード処理機能も提供します。  
  
 たとえば、データベースの顧客の住所データを表示する複合コントロールを作成できます。 このコントロールを含めることができます、<xref:System.Windows.Forms.DataGridView>データベース フィールドを表示するコントロールを<xref:System.Windows.Forms.BindingSource>データ ソースへのバインドを処理するために、<xref:System.Windows.Forms.BindingNavigator>レコード間を移動するコントロール。 データ バインディング プロパティを選択的に公開したり、コントロール全体をパッケージ化してアプリケーション間で再利用したりできます。 この種の複合コントロールの例は、次を参照してください。[方法。Windows フォーム コントロールに属性を適用](how-to-apply-attributes-in-windows-forms-controls.md)します。  
  
 派生する複合コントロールを作成する、<xref:System.Windows.Forms.UserControl>クラス。 <xref:System.Windows.Forms.UserControl>基底クラスが子コントロールを子コントロールをグループとして機能できるようにキーボード ルーティングを提供します。 詳細については、「[複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)」を参照してください。  
  
 **推奨事項**  
  
 次の場合に、<xref:System.Windows.Forms.UserControl> クラスから継承します。  
  
-   いくつかの Windows フォーム コントロールの機能を再利用可能な 1 つの単位に結合します。  
  
### <a name="extended-controls"></a>拡張コントロール  
 既存の Windows フォーム コントロールから継承されたコントロールを派生できます。 この方法では、Windows フォーム コントロールの固有の機能をすべて保持し、カスタム プロパティやカスタム メソッドなどの機能を追加してその機能を拡張できます。 この方法を使用して、基本コントロールの描画ロジックをオーバーライドし、そのユーザー インターフェイスの外観を変更して拡張できます。  
  
 派生したコントロールを作成するなど、<xref:System.Windows.Forms.Button>何回、ユーザーを追跡するコントロールがクリックしました。  
  
 一部のコントロールで追加することできますもカスタムの外観をコントロールのグラフィカル ユーザー インターフェイスをオーバーライドすることで、<xref:System.Windows.Forms.Control.OnPaint%2A>基本クラスのメソッド。 拡張ボタンのクリックを追跡する、オーバーライドすることができます、<xref:System.Windows.Forms.Control.OnPaint%2A>の基本実装を呼び出すメソッドを<xref:System.Windows.Forms.Control.OnPaint%2A>、しの一角にクリック回数を描画、<xref:System.Windows.Forms.Button>コントロールのクライアント領域。  
  
 **推奨事項**  
  
 次の場合に、Windows フォーム コントロールから継承します。  
  
-   必要とする機能のほとんどが、既存の Windows フォーム コントロールと同じです。  
  
-   カスタムのグラフィカル ユーザー インターフェイスが不要な場合、または既存のコントロールの新しいグラフィカル ユーザー インターフェイスをデザインする場合。  
  
### <a name="custom-controls"></a>カスタム コントロール  
 継承することによって実質的に最初から作成するコントロールを作成する別の方法は、<xref:System.Windows.Forms.Control>します。 <xref:System.Windows.Forms.Control>クラスはすべてのマウスやキーボード イベントを処理などのコントロールに必要な基本的な機能がないコントロール固有の機能やグラフィカル インターフェイスを提供します。  
  
 継承することによって、コントロールの作成、<xref:System.Windows.Forms.Control>クラスは、さらに多くの配慮と労力よりから継承する必要があります。<xref:System.Windows.Forms.UserControl>または既存の Windows フォーム コントロール。 多くの実装が開発者に委ねられるため、作成されるコントロールは、複合コントロールや拡張コントロールよりも柔軟性に優れ、ニーズに合わせてコントロールを調整できます。  
  
 カスタム コントロールを実装するにはコードを記述する必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>必要がありますすべての機能に固有のコードと同様に、コントロールのイベント。 オーバーライドすることも、<xref:System.Windows.Forms.Control.WndProc%2A>直接メソッドとハンドルの windows メッセージ。 これはコントロールを作成する最も強力な方法ですが、この手法を効果的に使用するには、Microsoft Win32® API を十分に理解している必要があります。  
  
 カスタム コントロールの例として、アナログ時計の外観と動作を複製した時計コントロールがあります。 応答を移動する時計の針がカスタム描画が呼び出される<xref:System.Windows.Forms.Timer.Tick>内部からのイベント<xref:System.Windows.Forms.Timer>コンポーネント。 詳細については、「[方法 :単純な Windows フォーム コントロールを開発](how-to-develop-a-simple-windows-forms-control.md)します。  
  
 **推奨事項**  
  
 次の場合に、<xref:System.Windows.Forms.Control> クラスから継承します。  
  
-   コントロールのカスタムのグラフィカル表現を提供します。  
  
-   標準コントロールでは使用できないカスタムの機能を実装する必要があります。  
  
### <a name="activex-controls"></a>ActiveX コントロール  
 Windows フォーム インストラクチャは、Windows フォーム コントロールをホストするために最適化されていますが、ActiveX コントロールを使用することもできます。 Visual Studio では、このタスクに対するサポートが用意されています。 詳細については、「[方法 :Windows フォームに ActiveX コントロールを追加](how-to-add-activex-controls-to-windows-forms.md)します。  
  
### <a name="windowless-controls"></a>ウィンドウなしのコントロール  
 Microsoft Visual Basic® 6.0 と ActiveX テクノロジは、"*ウィンドウなし*" のコントロールをサポートします。 ウィンドウなしのコントロールは、Windows フォームではサポートされていません。  
  
## <a name="custom-design-experience"></a>カスタム デザイン エクスペリエンス  
 カスタムのデザイン時エクスペリエンスを実装する必要がある場合は、独自のデザイナーを作成できます。 複合コントロールからカスタム デザイナー クラスを派生、<xref:System.Windows.Forms.Design.ParentControlDesigner>または<xref:System.Windows.Forms.Design.DocumentDesigner>クラス。 拡張とカスタムのコントロールからカスタム デザイナー クラスを派生、<xref:System.Windows.Forms.Design.ControlDesigner>クラス。  
  
 使用して、<xref:System.ComponentModel.DesignerAttribute>にコントロールをデザイナーに関連付けます。 詳細については、次を参照してください。[デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))と[方法。デザイン時機能を活用した Windows フォーム コントロールを作成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))です。  
  
## <a name="see-also"></a>関連項目

- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [方法: シンプルな Windows フォーム コントロールを開発する](how-to-develop-a-simple-windows-forms-control.md)
- [複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)
- [デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [方法: デザイン時機能を活用した Windows フォーム コントロールを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
