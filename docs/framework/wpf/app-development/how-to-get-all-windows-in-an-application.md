---
title: '方法: すべての Windows アプリケーションでの取得します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378827"
---
# <a name="how-to-get-all-windows-in-an-application"></a>方法: すべての Windows アプリケーションでの取得します。
この例は、すべてを取得する方法を示しています。<xref:System.Windows.Window>アプリケーション内のオブジェクト。  
  
## <a name="example"></a>例  
 すべてをインスタンス化<xref:System.Windows.Window>オブジェクトを表示するかどうかで管理されているウィンドウの参照のコレクションが自動的に追加<xref:System.Windows.Application>から公開されていると<xref:System.Windows.Application.Windows%2A>します。  
  
 列挙できます<xref:System.Windows.Application.Windows%2A>を次のコードを使用してインスタンス化されたすべての windows を取得します。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
