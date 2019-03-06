---
title: '方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: b5e39541fdf031b19e9e74483c0de94295e788d7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375226"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる
使用して、 <xref:System.Windows.Media.BitmapCache> 、複雑なのレンダリング パフォーマンスを向上させるためにクラス<xref:System.Windows.UIElement>します。 要素をキャッシュするには、新しいインスタンスを作成、<xref:System.Windows.Media.BitmapCache>クラスし、要素に割り当てる<xref:System.Windows.UIElement.CacheMode%2A>プロパティ。 再利用することができます、<xref:System.Windows.Media.BitmapCache>で効率的に、<xref:System.Windows.Media.BitmapCacheBrush>します。  
  
## <a name="example"></a>例  
 次のコード例では、複合型の要素を作成して、要素がアニメーション化されるときにパフォーマンスが向上ビットマップとしてキャッシュする方法を示します。 要素は、図形のジオメトリの頂点の数を保持するキャンバスです。 A<xref:System.Windows.Media.BitmapCache>に割り当てられている値、既定値は、<xref:System.Windows.UIElement.CacheMode%2A>キャンバスのし、キャッシュされたビットマップのスムーズな拡張、アニメーションを示しています。  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [方法: キャッシュされた要素をブラシとして使用します。](how-to-use-a-cached-element-as-a-brush.md)
