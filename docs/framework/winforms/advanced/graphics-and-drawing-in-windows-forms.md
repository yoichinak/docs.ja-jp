---
title: Windows フォームにおけるグラフィックスと描画
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505545"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows フォームにおけるグラフィックスと描画
共通言語ランタイムは、高度な実装の Windows グラフィックス デバイス インターフェイス (GDI) と呼ばれる GDI + を使用します。 GDI + を使用してグラフィックスを作成、テキストを描画およびグラフィカル イメージ オブジェクトとして操作することができます。 GDI + はパフォーマンスと使いやすさを提供しています。 GDI + を使用すると、Windows フォームとコントロールのグラフィカル イメージをレンダリングします。 GDI + できません使用する Web フォームで直接、イメージの Web サーバー コントロールからグラフィカル イメージを表示できます。  
  
 このセクションでは、GDI + プログラミングの基礎を紹介するトピックを紹介します。 このセクションは、包括的なリファレンスを意図したものではありませんが、<xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush>、および <xref:System.Drawing.Color> の各オブジェクトに関する情報が含まれ、図形の描画、テキストの描画、イメージの表示などのタスクを実行する方法について説明します。 詳細については、次を参照してください。 [GDI + の参照](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference)します。  
  
 すぐに開始する場合、「[グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)」を参照してください。 Windows フォームで線、図形、テキストなどを描画するためのコードの使用方法に関するトピックがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [グラフィックスの概要](graphics-overview-windows-forms.md)  
 グラフィックスに関連するマネージド クラスの概要を提供します。  
  
 [GDI+ マネージド コードについて](about-gdi-managed-code.md)  
 マネージ GDI + クラスについてを説明します。  
  
 [マネージド グラフィックス クラスの使用](using-managed-graphics-classes.md)  
 方法を完全な GDI + を使用してタスクのさまざまなマネージ クラスについて説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing>  
 GDI + の基本的なグラフィックス機能へのアクセスを提供します。  
  
 <xref:System.Drawing.Drawing2D>  
 2 次元グラフィックスおよびベクター グラフィックス機能の詳細を提供します。  
  
 <xref:System.Drawing.Imaging>  
 高度な GDI + イメージング機能を提供します。  
  
 <xref:System.Drawing.Text>  
 高度な GDI + タイポグラフィ機能を提供します。 この名前空間のクラスを使用して、フォントのコレクションを作成して使用することができます。  
  
 <xref:System.Drawing.Printing>  
 印刷機能を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [コントロールのカスタム描画およびレンダリング](../controls/custom-control-painting-and-rendering.md)  
 描画コントロールのコードを提供する方法について詳しく説明します。
