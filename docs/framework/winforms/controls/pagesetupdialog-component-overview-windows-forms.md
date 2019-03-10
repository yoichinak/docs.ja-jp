---
title: PageSetupDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 702e9a40652e00cc2f93dd52af29a61a50c90ae0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715803"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PageSetupDialog>コンポーネントは Windows ベースのアプリケーションの印刷用ページの詳細を設定するための事前構成済みダイアログ ボックス。 代わりに、独自のダイアログ ボックスの構成ページの基本設定を設定するのにユーザーの簡単な解決策として、Windows ベース アプリケーションの中で使用します。 ユーザーに境界線と余白の調整、ヘッダーとフッター、および縦または横方向の設定を有効にすることができます。 Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド実行時にダイアログを表示します。 このコンポーネントには 1 つのページのいずれかに関連するプロパティを設定できます (<xref:System.Drawing.Printing.PrintDocument>クラス)、または任意のドキュメント (<xref:System.Drawing.Printing.PageSettings>クラス)。 さらに、<xref:System.Windows.Forms.PageSetupDialog>に格納されている特定のプリンター設定を確認するコンポーネントを使用できます、<xref:System.Drawing.Printing.PrinterSettings>クラス。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.PageSetupDialog>コンポーネント、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog コンポーネント](pagesetupdialog-component-windows-forms.md)
