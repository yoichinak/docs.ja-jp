---
title: Windows フォーム DataGridView コントロールの既定の機能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 26633b0abaa8c1c2916153b2236ecf9e4982fd68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208866"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの既定の機能
Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールは多くの既定の機能をユーザーに提供します。  
  
## <a name="default-functionality"></a>既定の機能  
 <xref:System.Windows.Forms.DataGridView>コントロールは、既定で次のような機能を持ちます:  
  
-   テーブルを垂直方向にスクロールしても列ヘッダーおよび行ヘッダーが見える状態のまま自動的に表示します。  
  
-   現在の行を示す選択を含む行ヘッダーがあります。  
  
-   最初のセルに選択を示す四角形があります。  
  
-   自動的にサイズを変更できるユーザーが列の区分線をダブルクリックしたときに列があります。  
  
-   自動的に Windows XP と Windows Server 2003 ファミリで視覚スタイルをサポートしているときに、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>メソッドの呼び出し元アプリケーションの`Main`メソッド。  
  
 さらに、<xref:System.Windows.Forms.DataGridView>コントロールの内容は既定で編集できます:  
  
-   ユーザーがダブルクリックするか、セル中で F2 キーを押した場合、コントロールは自動的にセルを編集モードにし、ユーザーが入力したセルの内容を更新します。  
  
-   ユーザーは、グリッドの最後にスクロールする場合、新しいレコードを追加するための行が存在する、ユーザーが表示されます。 新しい行を追加、ユーザーは、この行をクリックすると、<xref:System.Windows.Forms.DataGridView>コントロールは、既定値を使用します。 ユーザーは、esc キーを押すと、この新しい行が表示されなくなります。  
  
-   ユーザーは、行ヘッダーをクリックすると、行全体が選択されます。  
  
 <xref:System.Windows.Forms.DataGridView> プロパティの設定から<xref:System.Windows.Forms.DataGridView.DataSource%2A> コントロールをデータ ソースにバインドしたとき、コントロールは次のように振る舞います:  
  
-   列ヘッダーのテキストとして、データ ソースの列の名前が自動的に使用します。  
  
-   データ ソースの内容が表示されます。 <xref:System.Windows.Forms.DataGridView> 列は、データ ソースの各列に対して自動的に作成されます。  
  
-   テーブルに 1 行ごとに表示される行のデータを作成します。  
  
-   ユーザーが列ヘッダーをクリックすると、基になるデータに基づく行を自動的に並べ替えます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
