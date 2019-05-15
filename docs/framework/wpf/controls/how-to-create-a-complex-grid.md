---
title: 複雑なグリッドを作成する方法
description: グリッド コントロールを使用して、月間予定表のようなレイアウトを作成する方法の例です。
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: ab5490d608b21fe8b29a078dc1f0147f038c27a3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645670"
---
# <a name="how-to-create-a-complex-grid"></a>複雑なグリッドを作成する方法

この例は、使用する方法を示します、<xref:System.Windows.Controls.Grid>月間予定表のようなレイアウトを作成するコントロール。

## <a name="example"></a>例

次の例を使用して 8 つの行と 8 つの列の定義、<xref:System.Windows.Controls.RowDefinition>と<xref:System.Windows.Controls.ColumnDefinition>クラス。 使用して、<xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType>と<xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType>と共に添付プロパティ、<xref:System.Windows.Shapes.Rectangle>要素で、さまざまな列と行の背景色を入力します。 この設計は、の各セルには、複数の要素が存在できますので、可能な<xref:System.Windows.Controls.Grid>、原則違い<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Documents.Table>。

例では、使用する垂直方向のグラデーション<xref:System.Windows.Shapes.Shape.Fill%2A>列とビジュアルのプレゼンテーションや予定表の読みやすさを向上させるために行。 スタイル<xref:System.Windows.Controls.TextBlock>要素は、日付と曜日を表します。 <xref:System.Windows.Controls.TextBlock> 要素は、セル内を使用して絶対位置、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティと配置プロパティ、アプリケーションのスタイル内で定義されています。

[!code-xaml[GridComplex#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

次の図は、生成されたコントロール、カスタマイズ可能なカレンダーを示しています。

![生成されたコントロールのスクリーン ショット](././media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [純色およびグラデーションによる塗りつぶしの概要](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [パネルの概要](panels-overview.md)
- [テーブルの概要](../advanced/table-overview.md)
