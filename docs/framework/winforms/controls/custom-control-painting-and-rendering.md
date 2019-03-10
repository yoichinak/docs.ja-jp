---
title: コントロールのカスタム描画およびレンダリング
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722140"
---
# <a name="custom-control-painting-and-rendering"></a>コントロールのカスタム描画およびレンダリング
コントロールのカスタム描画では、.NET Framework で簡単、多くの複雑なタスクの 1 つです。 カスタム コントロールを作成するときは、コントロールの外観に関する多くのオプションがあります。 継承するコントロールを作成している場合、 `Control`、により、コントロールはそのグラフィカル表現を表示するためにコードを提供する必要があります。 継承することによって、ユーザー コントロールを作成するかどうかは、 `UserControl`、継承は、Windows フォーム コントロールのいずれかでは、標準のグラフィカル表示をオーバーライドしてグラフィックス コードを指定します。 カスタムの内在コントロールのレンダリングを提供するかどうか、`UserControl`を作成する、オプションが制限されますがも、さまざまなコントロールとアプリケーションのグラフィカル表現を許可します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows フォーム コントロールのレンダリング](rendering-a-windows-forms-control.md)  
 コントロールの表示ロジックをプログラミングする方法を示します。  
  
 [ユーザー描画コントロール](user-drawn-controls.md)  
 書き込みと、コントロールのレンダリング コードをオーバーライドするための手順の概要を示します。  
  
 [内在コントロール](constituent-controls.md)  
 ユーザー コントロールとフォームの内在コントロールのカスタム レンダリング コードを実装する方法について説明します。  
  
 [方法: 実行時にコントロールを非表示にします。](how-to-make-your-control-invisible-at-run-time.md)  
 使用する方法を示しています、<xref:System.Windows.Forms.Control.Visible%2A>プロパティを非表示とコントロールを表示します。  
  
 [方法: コントロールに透明な背景を提供します。](how-to-give-your-control-a-transparent-background.md)  
 使用する方法を示しています、<xref:System.Windows.Forms.Control.SetStyle%2A>が不透明、透明または部分的に透明な背景色を作成します。  
  
 [visual スタイルが使用されているコントロールのレンダリング](rendering-controls-with-visual-styles.md)  
 それらをサポートするオペレーティング システムで visual スタイルを使用してコントロールをレンダリングする方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Control>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.UserControl>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 このメソッドをについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: 描画の Graphics オブジェクトを作成します。](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 紹介[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]詳細については、Visual Studio の観点と、リンクからのグラフィックス機能。  
  
 [さまざまなカスタム コントロール](varieties-of-custom-controls.md)  
 作成できるカスタム コントロールの種類について説明します。
