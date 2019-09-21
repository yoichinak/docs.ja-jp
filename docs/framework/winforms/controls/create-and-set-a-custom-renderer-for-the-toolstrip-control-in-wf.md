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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929740"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>方法: Windows フォームに ToolStrip コントロールのカスタム レンダラーを作成して設定する
<xref:System.Windows.Forms.ToolStrip>コントロールを使うと、テーマとスタイルを簡単にサポートできます。 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> プロパティ<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>またはプロパティをカスタムレンダラーに設定することによって、完全にカスタムの外観と動作 (ルックアンドフィール) を実現できます。  
  
 レンダラー <xref:System.Windows.Forms.ToolStrip>は<xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType> <xref:System.Windows.Forms.MenuStrip>、個々の、、 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> 、またはコントロールに割り当てることができます。また、プロパティをに設定することにより、プロパティを使用してすべてのオブジェクトに影響を与えることができます。 <xref:System.Windows.Forms.ContextMenuStrip>  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>`null`の<xref:System.Windows.Forms.ToolStripRenderMode.Custom> 値<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>がでない場合にのみ、を返します。  
  
### <a name="to-create-a-custom-renderer"></a>カスタムレンダラーを作成するには  
  
1. クラスを<xref:System.Windows.Forms.ToolStripRenderer>拡張します。  
  
2. 適切にオーバーライドして、必要なカスタムレンダリングを実装します. *.* メンバー  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>カスタムレンダラーを現在のレンダラーに設定するには  
  
1. 1つ<xref:System.Windows.Forms.ToolStrip>のカスタムレンダラーを設定するには<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> 、プロパティをカスタムレンダラーに設定します。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. または、アプリケーションに含まれるすべて<xref:System.Windows.Forms.ToolStrip>のクラスのカスタムレンダラーを設定するには、次のようにします。プロパティをカスタムレンダラーに設定し、 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>プロパティをに<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>設定します。 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>  
  
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
