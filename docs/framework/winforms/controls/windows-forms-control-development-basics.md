---
title: Windows フォーム コントロール開発の基本概念
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 6a7009ead6ceba58c17579835d03254f259f8e51
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723064"
---
# <a name="windows-forms-control-development-basics"></a>Windows フォーム コントロール開発の基本概念
Windows フォーム コントロールから直接または間接的に派生するクラスは、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>します。 次の一覧には、Windows フォーム コントロールを開発するための一般的なシナリオについて説明します。  
  
-   既存の組み合わせを制御複合コントロールを作成します。  
  
     複合コントロールは、コントロールとして再利用できるユーザー インターフェイスをカプセル化します。 複合コントロールの例は、テキスト ボックスと [リセット] ボタンで構成されるコントロールです。 ビジュアル デザイナーは、複合コントロールを作成するための豊富なサポートを提供します。 派生する複合コントロールを作成するには、<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>します。 基本クラス<xref:System.Windows.Forms.UserControl>キーボード ルーティングを提供する子コントロールを子コントロールをグループとして機能できるようにします。 詳細については、「[複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)」を参照してください。  
  
-   これをカスタマイズするか、その機能を追加する既存のコントロールを拡張します。  
  
     色を変更することはできません ボタンとボタンがクリックしてされた回数を追跡する追加のプロパティを持つ拡張コントロールの例に示します。 クラスを派生し、プロパティ、メソッド、およびイベントを追加、またはオーバーライドでは、任意の Windows フォーム コントロールをカスタマイズできます。  
  
-   ないコントロールの作成、結合または、既存のコントロールを拡張します。  
  
     このシナリオでは、基本クラスから、コントロールを派生<xref:System.Windows.Forms.Control>します。 追加したり、プロパティ、メソッド、および基底クラスのイベントをオーバーライドしたりします。 最初に、次を参照してください。[方法。単純な Windows フォーム コントロールを開発](how-to-develop-a-simple-windows-forms-control.md)します。  
  
 Windows フォーム コントロールの基底クラス<xref:System.Windows.Forms.Control>、Windows ベースのクライアント側アプリケーションでのビジュアル表示に必要なプラミングを提供します。 <xref:System.Windows.Forms.Control> ウィンドウ ハンドル、メッセージのルーティングを処理し、マウスとキーボード イベントとその他の多くのユーザー インターフェイス イベントを提供します。 高度なレイアウトを提供し、ビジュアルの表示に固有のプロパティをなどがあります。 <xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Height%2A>、 <xref:System.Windows.Forms.Control.Width%2A>、およびその他の多くの。 さらに、スレッドのサポート、および ActiveX コントロールとの相互運用のセキュリティを提供します。 インフラストラクチャの大部分は基本クラスによって提供されるため、独自の Windows フォーム コントロールを比較的簡単に開発できます。  
  
## <a name="see-also"></a>関連項目
- [方法: 単純な Windows フォーム コントロールを開発します。](how-to-develop-a-simple-windows-forms-control.md)
- [複合 Windows フォーム コントロールの開発](developing-a-composite-windows-forms-control.md)
- [方法: 進行状況を示す Windows フォーム コントロールを作成します。](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
