---
title: Windows フォームにおけるグラフィックスと描画
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 08f87436ade62bb54295b012a1c24dc177ea9667
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705425"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows フォームにおけるグラフィックスと描画
共通言語ランタイムは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と呼ばれる Windows グラフィックス デバイス インターフェイス ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) の高度な実装を使用します。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して、グラフィックスの作成、テキストの描画や、グラフィカル イメージをオブジェクトとして操作することができます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] はパフォーマンスと使いやすさを提供するよう設計されています。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して、Windows フォームとコントロールのグラフィカル イメージを表示できます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を Web フォームで直接使用することはできませんが、イメージの Web サーバー コントロールからグラフィカル イメージを表示できます。  
  
 このセクションでは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] プログラミングの基礎を紹介するトピックが見つかります。 このセクションは、包括的なリファレンスを意図したものではありませんが、<xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush>、および <xref:System.Drawing.Color> の各オブジェクトに関する情報が含まれ、図形の描画、テキストの描画、イメージの表示などのタスクを実行する方法について説明します。 詳細については、[GDI + の参照](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference)を参照してください。  
  
 すぐに開始する場合、「[グラフィックス プログラミングについて](getting-started-with-graphics-programming.md)」を参照してください。 Windows フォームで線、図形、テキストなどを描画するためのコードの使用方法に関するトピックがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [グラフィックスの概要](graphics-overview-windows-forms.md)  
 グラフィックスに関連するマネージド クラスの概要を提供します。  
  
 [GDI+ マネージド コードについて](about-gdi-managed-code.md)  
 マネージド [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスに関する情報を提供します。  
  
 [マネージド グラフィックス クラスの使用](using-managed-graphics-classes.md)  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] マネージド クラスを使用して、さまざまなタスクを完了する方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Drawing>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の基本的なグラフィックス機能を使用できるようにします。  
  
 <xref:System.Drawing.Drawing2D>  
 2 次元グラフィックスおよびベクター グラフィックス機能の詳細を提供します。  
  
 <xref:System.Drawing.Imaging>  
 高度な [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] イメージング機能を提供します。  
  
 <xref:System.Drawing.Text>  
 高度な [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] タイポグラフィ機能を提供します。 この名前空間のクラスを使用して、フォントのコレクションを作成して使用することができます。  
  
 <xref:System.Drawing.Printing>  
 印刷機能を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [コントロールのカスタム描画およびレンダリング](../controls/custom-control-painting-and-rendering.md)  
 描画コントロールのコードを提供する方法について詳しく説明します。
