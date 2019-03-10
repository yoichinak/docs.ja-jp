---
title: Windows フォーム DataGridView コントロール内のデータの並べ替え
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724922"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロール内のデータの並べ替え

既定では、ユーザーが内のデータを並べ替えることができます、<xref:System.Windows.Forms.DataGridView>コントロールのテキスト ボックスの列見出しをクリックして (またはテキスト ボックスのセルは、.NET Framework 4.7.2 以降でフォーカスがあるときに、f3 キーを押して)。 変更することができます、<xref:System.Windows.Forms.DataGridViewColumn.SortMode>をこれを行う方が良い場合、その他の列の型を並べ替えるにはユーザーを許可する特定の列のプロパティ。 任意の列または複数の列で、データをプログラムで並べ替えるもできます。

## <a name="in-this-section"></a>このセクションの内容

[Windows フォーム DataGridView コントロール内の列の並べ替えモード](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
コントロール内のデータの並べ替えのオプションについて説明します。

[方法: Windows フォームの DataGridView コントロール内の列の並べ替えモードを設定します。](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
ユーザーが既定では並べ替えできない列による並べ替えを有効にする方法について説明します。

[方法: Windows フォームの DataGridView コントロールでの並べ替えをカスタマイズします。](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
プログラムでデータを並べ替える方法とを使用して並べ替え機能をカスタマイズする方法について説明します、<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>イベントまたは実装することによって、<xref:System.Collections.IComparer>インターフェイス。

## <a name="reference"></a>参照

<xref:System.Windows.Forms.DataGridView>  

  <xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッド。

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティ。

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumnSortMode>列挙体。

## <a name="see-also"></a>関連項目

- [DataGridView コントロール](datagridview-control-windows-forms.md)
- [Windows フォーム DataGridView コントロールの列型](column-types-in-the-windows-forms-datagridview-control.md)
