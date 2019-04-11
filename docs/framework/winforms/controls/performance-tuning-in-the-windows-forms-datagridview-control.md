---
title: Windows フォーム DataGridView コントロールでのパフォーマンス チューニング
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 79f74db4ebd095156207a6218f59c0e9ae423085
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076595"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのパフォーマンス チューニング
大量のデータを使用する場合、`DataGridView`コントロールは慎重に使用する場合を除き、大量のオーバーヘッドが、メモリを使用できます。 限られたメモリでのクライアントではコスト高のメモリがある機能を回避することでこのオーバーヘッドの一部を回避できます。 データ メンテナンスの一部またはすべてを管理することもでき、シナリオでは、メモリ使用量をカスタマイズするために仮想モードを使用して自分でタスクを取得します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 使用する方法について説明します、`DataGridView`大量のデータを使用する場合は、不要なメモリの使用状況とパフォーマンスの低下を回避する方法で制御します。  
  
 [Windows フォーム DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 仮想モードを使用して、標準的なデータ バインディング機構を補完したりする方法について説明します。  
  
 [チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](implementing-virtual-mode-wf-datagridview-control.md)  
 複数の仮想モード イベントのハンドラーを実装する方法について説明します。 行レベルのロールバックとユーザーを編集するためのコミットを実装する方法も示します。  
  
 [Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 オンデマンドで利用可能なクライアント メモリに格納できるよりもを表示する複数のデータがある場合に有用なデータを読み込む方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティ。  
  
## <a name="see-also"></a>関連項目

- [DataGridView コントロール](datagridview-control-windows-forms.md)
- [Windows フォーム DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)
