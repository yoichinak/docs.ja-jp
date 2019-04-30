---
title: コントロールの種類に関するアドバイス
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5dc734997917af7ec4a20a6c12ae04825507c7ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011542"
---
# <a name="control-type-recommendations"></a>コントロールの種類に関するアドバイス
.NET Framework は、新しいコントロールを開発して実装する機能を提供します。 使い慣れたユーザー コントロールだけでなく、独自の描画を実行するカスタム コントロールを作成することも、継承によって既存のコントロールの機能を拡張することもできるようになりました。 作成するコントロールの種類の決定が、混乱を招く可能性があります。 このセクションでは、継承できるさまざまな種類のコントロールの間の違いについて説明し、プロジェクトに合わせて選択する種類に関する注意点を示しています。  
  
> [!NOTE]
>  Web フォームで使用するコントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))」を参照してください。  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Windows フォーム コントロールからの継承  
 既存の Windows フォーム コントロールから継承されたコントロールを派生できます。 この方法では、すべての Windows フォーム コントロールの本質的な機能をすべて保持して、カスタム プロパティ、メソッド、またはその他の機能を追加することでその機能を拡張することができます。 たとえば、数値のみを受け付け、入力を自動的に値に変換できる <xref:System.Windows.Forms.TextBox> から派生したコントロールを作成することができます。 このようなコントロールには、テキスト ボックスのテキストが変更されるたびに呼び出される検証コードが含まれ、値のプロパティを追加で持つことができます。 一部のコントロールでは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドすることで、コントロールのグラフィカル インターフェイスにカスタムの外観を追加することができます。  
  
 次の場合に、Windows フォーム コントロールから継承します。  
  
- 必要とする機能のほとんどが、既存の Windows フォーム コントロールと同じです。  
  
- カスタムのグラフィカル インターフェイスが必要ないか、または既存のコントロールに対して新しいグラフィカルのフロント エンドをデザインします。  
  
## <a name="inheriting-from-the-usercontrol-class"></a>UserControl クラスを継承する  
 ユーザー コントロールは、共通のコンテナー内にカプセル化された Windows フォーム コントロールのコレクションです。 コンテナーは、各 Windows フォーム コントロールに関連付けられている固有の機能をすべて保持し、それらのプロパティを選択的に公開してバインドすることができます。 ユーザー コントロールの例として、データベースから顧客の住所データを表示する貯めに作成されたコントロールがあります。 このコントロールには、各フィールドを表示するいくつかのテキスト ボックスと、レコード間を移動するボタン コントロールが含まれます。 データ バインディングのプロパティは選択的に公開することができ、コントロール全体は、パッケージしてアプリケーション間で再利用できます。  
  
 次の場合に、<xref:System.Windows.Forms.UserControl> クラスから継承します。  
  
- いくつかの Windows フォーム コントロールの機能を再利用可能な 1 つの単位に結合します。  
  
## <a name="inheriting-from-the-control-class"></a>Control クラスからの継承  
 コントロールを作成する別の方法は、<xref:System.Windows.Forms.Control> から継承することで、実質的に一から作成する方法です。 <xref:System.Windows.Forms.Control> クラスは、コントロール (イベントなど) によって必要とされる基本的な機能をすべて提供しますが、コントロール固有の機能やグラフィカル インターフェイスは提供しません。 <xref:System.Windows.Forms.Control> クラスから継承することでコントロールを作成する場合は、ユーザー コントロールや既存の Windows フォーム コントロールから継承する場合よりも、はるかに多くの配慮と労力が必要です。 作成者は、コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> イベントのコード、および必要とされる機能固有のコードを作成する必要があります。 ただし、より大きな柔軟性が可能になり、正確なニーズに合わせてコントロールをカスタムに調整することができます。 カスタム コントロールの例は、アナログ時計の外観や動作を複製する時計コントロールです。 内部タイマー コンポーネントからの <xref:System.Windows.Forms.Timer.Tick> イベントに応答してカスタム描画が呼び出されて、時計の針が移動します。  
  
 次の場合に、<xref:System.Windows.Forms.Control> クラスから継承します。  
  
- コントロールのカスタムのグラフィカル表現を提供します。  
  
- 標準コントロールでは使用できないカスタムの機能を実装する必要があります。  
  
- [方法: 内のコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
- [チュートリアル: Designerserializationvisibilityattribute を使用、基本データ型のコレクションをシリアル化します。](serializing-collections-designerserializationvisibilityattribute.md)  
  
- [チュートリアル: ビジュアルを含む Windows フォーム コントロールからの継承C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
- [方法: コントロールにツールボックス ビットマップを指定します。](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
- [方法: 継承可能な既存の Windows フォーム コントロール](how-to-inherit-from-existing-windows-forms-controls.md)  
  
- [チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
- [方法: コントロール クラスから継承します。](how-to-inherit-from-the-control-class.md)  
  
- [方法: UserControl の実行時の動作をテストします。](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
- [方法: デザイン時にコントロールをフォームの端を揃える](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
- [方法: UserControl クラスを継承します。](how-to-inherit-from-the-usercontrol-class.md)  
  
- [方法: Windows フォームのコントロールの作成](how-to-author-controls-for-windows-forms.md)  
  
- [方法: 複合コントロールを作成](how-to-author-composite-controls.md)  
  
- [チュートリアル: Visual Basic による複合コントロールの作成](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
- [チュートリアル: ビジュアルを含む複合コントロールの作成C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
- [チュートリアル: Visual Basic による Windows フォーム コントロールから継承します。](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
- [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](creating-a-wf-control-design-time-features.md)  
  
- [方法: デザイン時機能を活用した Windows フォーム コントロールを作成します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>関連項目

- [方法: 単純な Windows フォーム コントロールを開発します。](how-to-develop-a-simple-windows-forms-control.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
