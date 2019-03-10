---
title: ToolTip コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 33a66e8ab5c8b09c5ed3dcf9dc60810a42d4d05d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724038"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip コンポーネントの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ToolTip> コンポーネントは、ユーザーがコントロールをポイントしたときにテキストを表示します。 ツールヒントは任意のコントロールに関連付けることができます。 このコンポーネントの使用例: フォーム領域を保存するボタンに小さなアイコンを表示およびボタンの機能を説明するツールヒントを使用します。  
  
## <a name="working-with-the-tooltip-component"></a>ToolTip コンポーネントの操作  
 A<xref:System.Windows.Forms.ToolTip>コンポーネントは、提供、`ToolTip`を Windows フォームやその他のコンテナーに複数のコントロールのプロパティ。 たとえば、1 つを配置する場合<xref:System.Windows.Forms.ToolTip>フォーム上のコンポーネントの「名前を入力する」表示できます、<xref:System.Windows.Forms.TextBox>を制御し、「ここをクリックして変更を保存する」、<xref:System.Windows.Forms.Button>コントロール。  
  
 主要なメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネントは<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>と<xref:System.Windows.Forms.ToolTip.GetToolTip%2A>します。 使用することができます、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>コントロールに表示されるツールヒントを設定します。 詳細については、「[方法 :デザイン時に Windows フォーム上のコントロールのツールヒントを設定](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)します。 プロパティは<xref:System.Windows.Forms.ToolTip.Active%2A>設定する必要がある必要があります`true`のツールヒントを表示すると<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>、ツール ヒントの文字列が示されている時間の長さを設定するのツールヒントを表示するには、コントロールでユーザーがどのくらいの期間ポイントする必要がありますと時間方法ツールヒント ウィンドウが表示されるがされます。 詳細については、「[方法 :Windows フォームの ToolTip コンポーネントの遅延時間を変更](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolTip>
- [方法: デザイン時に Windows フォーム上のコントロールのツールヒントを設定します。](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更します。](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
