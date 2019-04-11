---
title: '方法: visual スタイル要素を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 57c2bc5722f77338225d70b514345344211656dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312398"
---
# <a name="how-to-render-a-visual-style-element"></a>方法: visual スタイル要素を描画する
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間を公開<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>Windows ユーザーを表すオブジェクト インターフェイス (UI) 要素の視覚スタイルによってサポートされています。 このトピックでは、使用する方法を示します、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>をレンダリングする、<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>を表す、**ログオフ**と**シャット ダウン**スタート メニューのボタン。  
  
### <a name="to-render-a-visual-style-element"></a>Visual スタイル要素を描画するには  
  
1. 作成、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>し、描画する要素に設定します。 使用に注意してください、<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType>プロパティおよび<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType>メソッドは、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A>コンス トラクターまたは要素が未定義の visual スタイルが無効になっている場合、例外がスローされます。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. 呼び出す、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A>メソッドを要素のレンダリング、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>現在を表します。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   派生したカスタム コントロール、<xref:System.Windows.Forms.Control>クラス。  
  
-   A<xref:System.Windows.Forms.Form>カスタム コントロールをホストします。  
  
-   参照、 <xref:System?displayProperty=nameWithType>、 <xref:System.Drawing?displayProperty=nameWithType>、 <xref:System.Windows.Forms?displayProperty=nameWithType>、および<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間。  
  
## <a name="see-also"></a>関連項目

- [visual スタイルが使用されているコントロールのレンダリング](rendering-controls-with-visual-styles.md)
