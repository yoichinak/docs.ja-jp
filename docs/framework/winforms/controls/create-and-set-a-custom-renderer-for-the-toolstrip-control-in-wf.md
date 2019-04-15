---
title: '方法: Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ca1a7444c029632f83b1600e5855a13c83777594
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296382"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>方法: Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する
<xref:System.Windows.Forms.ToolStrip> コントロールは、テーマとスタイルを簡単にサポートを提供します。 いずれかを設定して完全にカスタムの外観と動作 (ルック アンド フィール) を実現できる、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>プロパティまたは<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>プロパティ、カスタム レンダラーをします。  
  
 レンダラーを各ユーザーに割り当てることができます<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.ContextMenuStrip>、または<xref:System.Windows.Forms.StatusStrip>コントロール、またはを使用できる、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A>プロパティを設定してすべてのオブジェクトに影響を与える、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 返します<xref:System.Windows.Forms.ToolStripRenderMode.Custom>場合にのみの値<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>ない`null`します。  
  
### <a name="to-create-a-custom-renderer"></a>カスタム レンダラーを作成するには  
  
1. 拡張、<xref:System.Windows.Forms.ToolStripRenderer>クラス。  
  
2. 実装して目的のカスタム レンダリングをオーバーライドする適切な*にしています.* メンバー  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>現在のレンダラーにカスタム レンダラーを設定するには  
  
1. 1 つのカスタム レンダラーを設定する<xref:System.Windows.Forms.ToolStrip>、設定、<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>プロパティ、カスタム レンダラーをします。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. または、すべてのカスタム レンダラーを設定する<xref:System.Windows.Forms.ToolStrip>アプリケーションに含まれるクラス。設定、<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>プロパティにカスタム レンダラーを設定し、<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>プロパティを<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>します。  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
