---
title: '方法: ダイアログ ボックスの結果を返す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968230"
---
# <a name="how-to-return-a-dialog-box-result"></a>方法: ダイアログ ボックスの結果を返す
この例では、を呼び出す<xref:System.Windows.Window.ShowDialog%2A>ことによって開かれたウィンドウのダイアログの結果を取得する方法を示します。  
  
## <a name="example"></a>例  
 ダイアログボックスを閉じる前に、 <xref:System.Windows.Window.DialogResult%2A>ユーザーがダイアログボックスを閉じ<xref:System.Nullable%601>た方法を示すを<xref:System.Boolean>使用して、プロパティを設定する必要があります。 この値は、に<xref:System.Windows.Window.ShowDialog%2A>よって返されます。これにより、クライアントコードは、ダイアログボックスの終了方法、および結果の処理方法を決定できます。  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>を呼び出す<xref:System.Windows.Window.ShowDialog%2A>ことによってウィンドウが開かれた場合にのみ設定できます。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 を<xref:System.Windows.Window.ShowDialog%2A>呼び出すには、制限なしですべての windows およびユーザー入力イベントを使用するためのアクセス許可が必要です。
