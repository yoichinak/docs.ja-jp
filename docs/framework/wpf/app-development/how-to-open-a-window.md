---
title: '方法: ウィンドウを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947681"
---
# <a name="how-to-open-a-window"></a>方法: ウィンドウを開く
この例では、ウィンドウを開く方法を示します。  
  
## <a name="example"></a>例  
 ウィンドウをインスタンス化して開いた<xref:System.Windows.Window>を呼び出すと、<xref:System.Windows.Window.Show%2A>メソッド。 <xref:System.Windows.Window.Show%2A> ウィンドウが開き、新しいウィンドウが閉じるを待たずに直ちに返されます。 この種類のウィンドウとも呼ばれますが、*モードレス*ウィンドウとユーザー入力を制限しません。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 インスタンス化する<xref:System.Windows.Window>安全でないネイティブ メソッドを呼び出す権限が必要です (を参照してください<xref:System.Windows.Window.%23ctor%2A>)。
