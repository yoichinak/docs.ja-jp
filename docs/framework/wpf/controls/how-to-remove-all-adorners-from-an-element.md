---
title: '方法: 要素からすべての装飾を削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116795"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>方法: 要素からすべての装飾を削除する
この例は、プログラムで指定したすべての装飾を削除する方法を示しています。<xref:System.Windows.UIElement>します。  
  
## <a name="example"></a>例  
 この詳細なコード例では、すべての装飾を削除によって返される装飾の配列で<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>します。  この例の発生時に、装飾を取得する、<xref:System.Windows.UIElement>という*myTextBox*します。  呼び出しで、要素が指定されている場合<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>、装飾を持たない`null`が返されます。  このコードは明示的に null の配列をチェックし、アプリケーションに最適に比較的一般的な null 配列が必要な場合は、します。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>例  
 この要約のコード例は、機能的には、前述の詳細な例です。 このコードで明示的に確認、null 配列のできないできるようにする、<xref:System.NullReferenceException>例外が発生する可能性があります。  このコードは、null 配列のまれなことが必要です、アプリケーションに最適です。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>関連項目

- [装飾の概要](adorners-overview.md)
