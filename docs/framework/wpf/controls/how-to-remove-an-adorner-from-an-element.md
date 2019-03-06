---
title: '方法: 要素から装飾を削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: 0c74fe9ed1e7190ce4ff26a7dbae1413f950ba7e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374077"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>方法: 要素から装飾を削除する
この例は、プログラムで指定した特定の装飾を削除する方法を示しています。<xref:System.Windows.UIElement>します。  
  
## <a name="example"></a>例  
 この簡潔なコード例は、によって返される装飾の配列の最初のガイドを削除します<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>します。  この例の発生時に、装飾を取得する、<xref:System.Windows.UIElement>という*myTextBox*します。  呼び出しで、要素が指定されている場合<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>、装飾を持たない`null`が返されます。  このコードは明示的に null の配列をチェックし、アプリケーションに最適に比較的一般的な null 配列が必要な場合は、します。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>例  
 この要約のコード例は、機能的には、前述の詳細な例です。 このコードで明示的に確認、null 配列のできないできるようにする、<xref:System.NullReferenceException>例外が発生する可能性があります。  このコードは、null 配列のまれなことが必要です、アプリケーションに最適です。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>関連項目
- [装飾の概要](adorners-overview.md)
