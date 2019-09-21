---
title: Windows フォーム DataGridView コントロールでのデータの書式設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969186"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのデータの書式設定
コントロール<xref:System.Windows.Forms.DataGridView>は、セル値と親列に表示されるデータ型の間の自動変換を提供します。 たとえば、テキストボックスの列では、日付、時刻、数値、列挙値の文字列形式を表示し、ユーザーが入力した文字列値をデータストアで必要な型に変換します。  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>DataGridViewCellStyle クラスを使用した書式設定  
 コントロール<xref:System.Windows.Forms.DataGridView>は、クラスを<xref:System.Windows.Forms.DataGridViewCellStyle>使用したセル値の基本的なデータ書式設定を提供します。 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティを使用して、現在の既定のカルチャの日付、時刻、数値、および列挙値の書式を設定するには、「[型の書式設定](../../../standard/base-types/formatting-types.md)」で説明されている書式指定子を使用します。 また、プロパティを使用して、 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>特定のカルチャに対してこれらの値を書式設定することもできます。 指定された形式は、データの表示と、ユーザーが指定した形式で入力したデータの解析の両方に使用されます。  
  
 クラス<xref:System.Windows.Forms.DataGridViewCellStyle>には、折り返し、テキストの配置、および null データベース値のカスタム表示に関する追加の書式設定プロパティが用意されています。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](how-to-format-data-in-the-windows-forms-datagridview-control.md)でデータの書式を設定します。  
  
## <a name="formatting-with-the-cellformatting-event"></a>CellFormatting 設定イベントを使用した書式設定  
 基本的な書式設定がニーズに合わない場合は、 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベントのハンドラーにカスタムデータ書式を提供できます。 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A>ハンドラーに<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>渡されるには、最初にセル値を格納するプロパティがあります。 通常、この値は自動的に表示の種類に変換されます。 値を自分で変換するには<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 、プロパティを表示型の値に設定します。  
  
> [!NOTE]
> 書式指定文字列がセルに対して有効になっている場合、 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>プロパティをに`true`設定しない限り、プロパティ値の変更はオーバーライドされます。  
  
 イベント<xref:System.Windows.Forms.DataGridView.CellFormatting>は、個々のセルのプロパティを値<xref:System.Windows.Forms.DataGridViewCellStyle>に基づいて設定する場合にも便利です。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)でデータの書式設定をカスタマイズします。  
  
 ユーザー指定の値の既定の解析がニーズに合わない場合は、 <xref:System.Windows.Forms.DataGridView.CellParsing> <xref:System.Windows.Forms.DataGridView>コントロールのイベントを処理してカスタム解析を提供できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows フォーム DataGridView コントロールでのデータの表示](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでのデータの書式設定](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでのデータ書式設定のカスタマイズ](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
