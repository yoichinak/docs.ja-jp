---
title: '方法: コントロールに透明な背景を提供します。'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 5a54b76eb92c7d3f518b9bf13e154e6faf58de63
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718169"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>方法: コントロールに透明な背景を提供します。
.NET Framework の従来のバージョンでは、あらかじめフォームのコンストラクターに <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを設定しておかないと、透明な背景色を設定できませんでした。 フレームワークの現在のバージョンでは、ほとんどのコントロールの背景色を、設計時に <xref:System.Drawing.Color.Transparent%2A> [プロパティ] **ウィンドウで、またはフォームのコンストラクターのコードで、** に設定できます。  
  
> [!NOTE]
>  Windows フォーム コントロールは、完全な透過性はサポートしていません。 透明な Windows フォーム コントロールの背景は、その親によって描画されます。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> プロパティが <xref:System.Windows.Forms.ButtonBase.BackColor%2A> に設定されている場合でも、 <xref:System.Drawing.Color.Transparent%2A>コントロールは透明な背景をサポートしません。  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>コントロールに透明な背景を設定するには  
  
-   [プロパティ] ウィンドウで <xref:System.Windows.Forms.ButtonBase.BackColor%2A> プロパティを選択し、 <xref:System.Drawing.Color.Transparent%2A>に設定します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Drawing.Color.FromArgb%2A>
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [マネージド グラフィックス クラスの使用](../advanced/using-managed-graphics-classes.md)
- [方法: 不透明な直線および半透明な直線を描画します。](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
