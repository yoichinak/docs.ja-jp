---
title: オブジェクト ツリーに存在しないオブジェクト要素の初期化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: b0032492a9403660e91980f5e968b519a4306589
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610495"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>オブジェクト ツリーに存在しないオブジェクト要素の初期化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の初期化処理では、プロセスに処理を委任することがあり、そのプロセスは、一般的にその要素が論理ツリーまたはビジュアル ツリーのいずれかに接続されていることを前提としています。 このトピックでは、どちらのツリーにも接続されていない要素を初期化するために必要となる場合がある手順について説明します。  

## <a name="elements-and-the-logical-tree"></a>要素と論理ツリー  
 コード内で [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスのインスタンスを作成するときは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスのオブジェクト初期化処理の一部が、クラス コンストラクターの呼び出し時に実行されるコードから意図的に除外されていることに注意してください。 特に、コントロール クラスの場合は、コントロールの視覚的表現のほとんどが、コンストラクターでは定義されません。 代わりに、視覚的表現は、コントロールのテンプレートによって定義されます。 このテンプレートのソースには、さまざまなものがありますが、ほとんどの場合は、テーマ スタイルから取得されます。 テンプレートは、実質的には遅延バインディングです。そのコントロールがレイアウト可能になるまで、必要なテンプレートはコントロールに適用されません。 コントロールは、ルートでレンダリングするための表面に接続される論理ツリーに適用されるまで、レイアウトが可能になりません。 このルート レベル要素によって、論理ツリーで定義されているすべての子要素のレンダリングが開始されます。  
  
 このプロセスには、ビジュアル ツリーも関与します。 テンプレートによってビジュアル ツリーに組み込まれる要素も、接続されるまでは完全にインスタンス化されません。  
  
 この動作の影響で、要素の視覚的特性がすべて揃っていることを前提とする特定の操作には、追加の手順が必要になります。 構築されているが、まだツリーに適用されていないクラスの視覚的特性を取得しようとする場合などが、その例です。 たとえば、呼び出そうとする場合<xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A>上、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>を渡しているビジュアルがツリーに接続されていない要素とその要素は、追加の初期化手順が完了するまでは視覚的に完了しません。  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>BeginInit と EndInit を使用して要素を初期化する  
 さまざまなクラスに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]実装、<xref:System.ComponentModel.ISupportInitialize>インターフェイス。 使用する、<xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>と<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>(レンダリングに影響をその値のプロパティの設定) には、初期化の手順を含むコード内の領域を示すためにインターフェイスのメソッド。 後<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>呼びますで、シーケンスのレイアウト システムは、要素を処理し、暗黙的なスタイルの検索を開始します。  
  
 要素のプロパティを設定する場合は、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>派生クラスでのクラスのバージョンを呼び出すことができます<xref:System.Windows.FrameworkElement.BeginInit%2A>と<xref:System.Windows.FrameworkElement.EndInit%2A>へのキャストではなく<xref:System.ComponentModel.ISupportInitialize>します。  
  
### <a name="sample-code"></a>サンプル コード  
 次の例はレンダリングを使用するコンソール アプリケーションのサンプル コード[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]と<xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType>loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の適切な位置を示すためにファイル<xref:System.Windows.FrameworkElement.BeginInit%2A>と<xref:System.Windows.FrameworkElement.EndInit%2A>を調整する他の API 呼び出しの周りレンダリングに影響するプロパティ。  
  
 この例では、main 関数のみを示します。 関数 `Rasterize` および `Save` (この例には示していません) は、イメージ処理および入出力を扱うユーティリティ関数です。  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>関連項目

- [WPF のツリー](trees-in-wpf.md)
- [WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
