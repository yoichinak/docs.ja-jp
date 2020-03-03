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
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950089"
---
# <a name="varieties-of-custom-controls"></a>さまざまなカスタム コントロール
.NET Framework を使用して、新しいコントロールを開発し、実装できます。 継承によって、使い慣れたユーザー コントロールや既存のコントロールの機能を拡張できます。 また、独自の描画を実行するカスタム コントロールを作成することもできます。  
  
 作成するコントロールの種類を決めるときに、判断に迷うことがあります。 このトピックでは、継承できる各種コントロールの違いを示し、プロジェクトに合わせて特定の種類のコントロールを選択する方法について説明します。  
  
> [!NOTE]
> Web フォームで使用するコントロールを作成する方法については、「[カスタム ASP.NET サーバー コントロールの開発](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))」を参照してください。  
  
## <a name="base-control-class"></a>基本コントロール クラス  
 <xref:System.Windows.Forms.Control>クラスは、Windows フォームコントロールの基本クラスです。 このクラスは、Windows フォーム アプリケーションでのビジュアル表示に必要なインフラストラクチャを提供します。  
  
 クラス<xref:System.Windows.Forms.Control>は、次のタスクを実行して Windows フォームアプリケーションで視覚的な表示を提供します。  
  
- ウィンドウ ハンドルを公開する。  
  
- メッセージ ルーティングを管理する。  
  
- マウス イベントとキーボード イベント、および他のさまざまなユーザー インターフェイス イベントを提供する。  
  
- 高度なレイアウト機能を提供する。  
  
- <xref:System.Windows.Forms.Control.ForeColor%2A>には<xref:System.Windows.Forms.Control.BackColor%2A> 、、<xref:System.Windows.Forms.Control.Width%2A>、、など、ビジュアル表示に固有の多くのプロパティが含まれています。 <xref:System.Windows.Forms.Control.Height%2A>  
  
- Windows フォーム コントロールが Microsoft® ActiveX® コントロールとして機能するために必要なセキュリティとスレッドのサポートを提供する。  
  
 インフラストラクチャの大部分は基本クラスによって提供されるため、独自の Windows フォーム コントロールを比較的簡単に開発できます。  
  
## <a name="kinds-of-controls"></a>コントロールの種類  
 Windows フォームは、*複合*、*拡張*、*カスタム*の 3 種類のユーザー定義コントロールをサポートします。 以下のセクションでは、各種コントロールについて説明し、プロジェクトで使用する種類を選択する際の推奨事項を示します。  
  
### <a name="composite-controls"></a>複合コントロール  
 複合コントロールは、共通のコンテナーにカプセル化された Windows フォーム コントロールのコレクションです。 この種のコントロールは、*ユーザー コントロール*とも呼ばれます。 含まれているコントロールは、*内在コントロール*と呼ばれます。  
  
 複合コントロールは、含まれている各 Windows フォーム コントロールに関連する固有の機能をすべて保持し、それらのプロパティを選択的に公開してバインドできます。 また、開発者側での追加作業を必要としない多数の既定のキーボード処理機能も提供します。  
  
 たとえば、データベースの顧客の住所データを表示する複合コントロールを作成できます。 このコントロールには、 <xref:System.Windows.Forms.DataGridView>データベースフィールド<xref:System.Windows.Forms.BindingSource>を表示するコントロール、 <xref:System.Windows.Forms.BindingNavigator>データソースへのバインドを処理するためのコントロール、およびレコード間を移動するコントロールを含めることができます。 データ バインディング プロパティを選択的に公開したり、コントロール全体をパッケージ化してアプリケーション間で再利用したりできます。 この種類の複合コントロールの例については[、「方法:Windows フォームコントロール](how-to-apply-attributes-in-windows-forms-controls.md)に属性を適用します。  
  
 複合コントロールを作成するには、 <xref:System.Windows.Forms.UserControl>クラスから派生させます。 基本<xref:System.Windows.Forms.UserControl>クラスは、子コントロールのキーボードルーティングを提供し、子コントロールがグループとして機能できるようにします。 詳細については、「[複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)」を参照してください。  
  
 **推奨事項**  
  
 次の場合に、<xref:System.Windows.Forms.UserControl> クラスから継承します。  
  
- いくつかの Windows フォーム コントロールの機能を再利用可能な 1 つの単位に結合します。  
  
### <a name="extended-controls"></a>拡張コントロール  
 既存の Windows フォーム コントロールから継承されたコントロールを派生できます。 この方法では、Windows フォーム コントロールの固有の機能をすべて保持し、カスタム プロパティやカスタム メソッドなどの機能を追加してその機能を拡張できます。 この方法を使用して、基本コントロールの描画ロジックをオーバーライドし、そのユーザー インターフェイスの外観を変更して拡張できます。  
  
 たとえば、ユーザーがクリックした回数を追跡する<xref:System.Windows.Forms.Button>コントロールから派生したコントロールを作成できます。  
  
 コントロールによっては、基本クラスの<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドすることによって、コントロールのグラフィカルユーザーインターフェイスにカスタムの外観を追加することもできます。 クリックを追跡する拡張ボタンでは、 <xref:System.Windows.Forms.Control.OnPaint%2A>メソッドをオーバーライドしての<xref:System.Windows.Forms.Control.OnPaint%2A>基本実装を呼び出してから、 <xref:System.Windows.Forms.Button>コントロールのクライアント領域の1つの隅にクリック数を描画できます。  
  
 **推奨事項**  
  
 次の場合に、Windows フォーム コントロールから継承します。  
  
- 必要とする機能のほとんどが、既存の Windows フォーム コントロールと同じです。  
  
- カスタムのグラフィカル ユーザー インターフェイスが不要な場合、または既存のコントロールの新しいグラフィカル ユーザー インターフェイスをデザインする場合。  
  
### <a name="custom-controls"></a>カスタム コントロール  
 コントロールを作成するもう1つの方法は、から<xref:System.Windows.Forms.Control>継承することによって最初から作成することです。 クラス<xref:System.Windows.Forms.Control>は、マウスやキーボードの処理イベントなど、コントロールに必要なすべての基本機能を提供しますが、コントロール固有の機能やグラフィカルインターフェイスは提供しません。  
  
 <xref:System.Windows.Forms.Control>クラスから継承することによってコントロールを作成する場合は、または<xref:System.Windows.Forms.UserControl>既存の Windows フォームコントロールから継承するよりもはるかに多くの思考と労力が必要です。 多くの実装が開発者に委ねられるため、作成されるコントロールは、複合コントロールや拡張コントロールよりも柔軟性に優れ、ニーズに合わせてコントロールを調整できます。  
  
 カスタムコントロールを実装するには、必要な機能固有<xref:System.Windows.Forms.Control.OnPaint%2A>のコードだけでなく、コントロールのイベントのコードも記述する必要があります。 また、メソッドをオーバーライド<xref:System.Windows.Forms.Control.WndProc%2A>して、windows メッセージを直接処理することもできます。 これはコントロールを作成する最も強力な方法ですが、この手法を効果的に使用するには、Microsoft Win32® API を十分に理解している必要があります。  
  
 カスタム コントロールの例として、アナログ時計の外観と動作を複製した時計コントロールがあります。 カスタム描画が呼び出され、内部<xref:System.Windows.Forms.Timer.Tick> <xref:System.Windows.Forms.Timer>コンポーネントからのイベントに応答して、時計の針が移動します。 詳細については、「[方法 :単純な Windows フォームコントロール](how-to-develop-a-simple-windows-forms-control.md)を開発します。  
  
 **推奨事項**  
  
 次の場合に、<xref:System.Windows.Forms.Control> クラスから継承します。  
  
- コントロールのカスタムのグラフィカル表現を提供します。  
  
- 標準コントロールでは使用できないカスタムの機能を実装する必要があります。  
  
### <a name="activex-controls"></a>ActiveX コントロール  
 Windows フォーム インストラクチャは、Windows フォーム コントロールをホストするために最適化されていますが、ActiveX コントロールを使用することもできます。 Visual Studio では、このタスクに対するサポートが用意されています。 詳細については、「[方法 :ActiveX コントロールを Windows フォーム](how-to-add-activex-controls-to-windows-forms.md)に追加します。  
  
### <a name="windowless-controls"></a>ウィンドウなしのコントロール  
 Microsoft Visual Basic® 6.0 と ActiveX テクノロジは、"*ウィンドウなし*" のコントロールをサポートします。 ウィンドウなしのコントロールは、Windows フォームではサポートされていません。  
  
## <a name="custom-design-experience"></a>カスタム デザイン エクスペリエンス  
 カスタムのデザイン時エクスペリエンスを実装する必要がある場合は、独自のデザイナーを作成できます。 複合コントロールの場合<xref:System.Windows.Forms.Design.ParentControlDesigner> <xref:System.Windows.Forms.Design.DocumentDesigner>は、クラスまたはクラスからカスタムデザイナークラスを派生させます。 拡張コントロールとカスタムコントロールの場合は、 <xref:System.Windows.Forms.Design.ControlDesigner>クラスからカスタムデザイナークラスを派生させます。  
  
 コントロールを<xref:System.ComponentModel.DesignerAttribute>デザイナーに関連付けるには、を使用します。 詳細については、「[デザイン時サポート](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))の[拡張」および「方法:デザイン時機能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))を利用する Windows フォームコントロールを作成します。  
  
## <a name="see-also"></a>関連項目

- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [方法: 単純な Windows フォームコントロールの開発](how-to-develop-a-simple-windows-forms-control.md)
- [複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)
- [デザイン時サポートの拡張](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [方法: デザイン時機能を利用する Windows フォームコントロールを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
