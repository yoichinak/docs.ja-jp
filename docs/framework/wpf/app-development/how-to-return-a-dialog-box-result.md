---
title: '方法: ダイアログ ボックスの結果を返す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357769"
---
# <a name="how-to-return-a-dialog-box-result"></a>方法: ダイアログ ボックスの結果を返す
この例は、呼び出すことによって開かれたウィンドウのダイアログの結果を取得する方法を示します<xref:System.Windows.Window.ShowDialog%2A>します。  
  
## <a name="example"></a>例  
 ダイアログ ボックスを閉じる前にその<xref:System.Windows.Window.DialogResult%2A>でプロパティを設定する必要があります、 <xref:System.Nullable%601> <xref:System.Boolean>ユーザーがダイアログ ボックスを閉じた方法を示します。 この値がによって返される<xref:System.Windows.Window.ShowDialog%2A> ダイアログ ボックスが閉じられた方法と、その結果、結果を処理する方法を決定するクライアント コードを許可します。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> 呼び出すことによって、ウィンドウが開かれた場合にのみ設定できます<xref:System.Windows.Window.ShowDialog%2A>します。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出す<xref:System.Windows.Window.ShowDialog%2A>すべての windows と無制限のユーザー入力イベントを使用する権限が必要です。
