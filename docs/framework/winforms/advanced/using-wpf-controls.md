---
title: WPF コントロールの使用
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713801"
---
# <a name="using-wpf-controls"></a>WPF コントロールの使用
Windows フォーム ベースのアプリケーションでは、Windows Presentation Foundation (WPF) コントロールを使用できます。 これらは、2 つの異なるビュー テクノロジが円滑に相互運用します。  
  
 Windows フォーム デザイナーでは、Windows Presentation Foundation コントロールをホストするためのビジュアル デ ザイン環境を提供します。 WPF コントロールがという特殊な Windows フォーム コントロールによってホストされている<xref:System.Windows.Forms.Integration.ElementHost>します。 このコントロールは、フォームのレイアウトに参加して、キーボードとマウスのメッセージを受信する WPF コントロールを使用します。 デザイン時に配置することができます、<xref:System.Windows.Forms.Integration.ElementHost>任意の Windows フォーム コントロールと同様に制御します。  
  
 Windows フォーム コントロールは WPF ベースのアプリケーションで使用することもできます。 詳細については、[Visual Studio で XAML をデザイン](/visualstudio/designers/designing-xaml-in-visual-studio)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: コピーして、デザイン時に ElementHost コントロールを貼り付ける](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Windows フォーム上の Windows Presentation Foundation コントロールをコピーする方法を示します。  
  
 [チュートリアル: デザイン時に Windows フォームでの WPF コンテンツの配置](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 固定やスナップ線をなど、Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation コントロールを配置する方法を示しています。
  
 [チュートリアル: デザイン時に Windows フォームで新しい WPF コンテンツを作成します。](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Windows フォーム ベースのアプリケーションで使用するための Windows Presentation Foundation コントロールを作成する方法を示します。
  
 [チュートリアル: デザイン時に Windows フォームでの WPF コンテンツの割り当てください。](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 フォームに表示する Windows Presentation Foundation コントロールの種類を選択する方法を示します。  
  
 [チュートリアル: WPF コンテンツのスタイル設定](walkthrough-styling-wpf-content.md)  
 Windows フォーム デザイナー間のワークフローを示しています、 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] Windows Presentation Foundation コントロールにスタイルを適用するためです。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Windows フォーム ベースのアプリケーションでホストの Windows Presentation Foundation コントロールに使用できるクラスについて説明します。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Windows フォーム コントロールをホストする Windows Presentation Foundation ベースのアプリケーションで使用できるクラスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)  
 Windows Presentation Foundation と Windows フォーム テクノロジ間の相互運用をについて説明します。  
  
 [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)  
 Visual Studio での Windows Presentation Foundation コントロールをデザインする方法について説明します。
