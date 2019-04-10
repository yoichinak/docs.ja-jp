---
title: '方法: アプリケーション間でドラッグ アンド ドロップ操作を実行する'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: f7fecf2f90c56e5ac10ea5929f1c23b25bf181bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221757"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>方法: アプリケーション間でドラッグ アンド ドロップ操作を実行する
アプリケーション間でのドラッグ アンド ドロップ操作の実行は、アプリケーション内での場合と同じですが、両方のアプリケーションが <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> プロパティと <xref:System.Windows.Forms.DragEventArgs.Effect%2A> プロパティの間で確立された "契約" に従って動作する必要があります。  
  
 次の手順では、作成した Windows ベースのアプリケーションと、Windows オペレーティング システムに含まれるワードパッドというワード プロセッサを使用して、アプリケーション間でのドラッグ アンド ドロップ操作を行います。 ワードパッドには、ドラッグ アンド ドロップされたテキストに対して実行できる処理のセットが定義されています。コードを記述する Windows ベースのアプリケーションはこれらの効果に従って動作するため、ドラッグ アンド ドロップ操作を正常に完了できます。  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>アプリケーション間でドラッグ アンド ドロップ手順を実行するには  
  
1.  新しい Windows フォーム アプリケーションを作成します。  
  
2.  フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。  
  
3.  ドロップされたデータを受け取るように <xref:System.Windows.Forms.TextBox> コントロールを設定します。  
  
     詳細については、「[チュートリアル:Windows フォームにおけるドラッグ アンド ドロップ操作の実行](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)します。  
  
4.  作成した Windows ベースのアプリケーションを実行し、アプリケーションの実行中にワードパッドを起動します。  
  
     ワードパッドは、Windows によってインストールされるテキスト エディターであり、ドラッグ アンド ドロップ操作をサポートします。 キーを押してアクセス、**開始**ボタンをクリックして**実行**、」と入力し、`WordPad`のテキスト ボックスに、**実行**をクリックしてダイアログボックス**OK**します。  
  
5.  ワードパッドが起動したら、テキストの文字列を入力します。  
  
6.  マウスを使用してテキストを選択し、選択したテキストを Windows ベースのアプリケーションの <xref:System.Windows.Forms.TextBox> コントロールにドラッグします。  
  
     マウスを <xref:System.Windows.Forms.TextBox> コントロールに移動すると (そして、その結果 <xref:System.Windows.Forms.Control.DragEnter> イベントが発生すると)、マウス ポインターの形が変化し、選択したテキストを <xref:System.Windows.Forms.TextBox> コントロールにドロップできます。  
  
     また、テキスト文字列をワードパッドにドラッグ アンド ドロップできるように <xref:System.Windows.Forms.TextBox> コントロールを設定することもできます。 詳細については、「[チュートリアル:Windows フォームにおけるドラッグ アンド ドロップ操作の実行](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目

- [方法: クリップボードにデータを追加する](how-to-add-data-to-the-clipboard.md)
- [方法: クリップボードからデータを取得する](how-to-retrieve-data-from-the-clipboard.md)
- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)
