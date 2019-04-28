---
title: '方法: カスタム ルーティング イベントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a3850875c8ca747f8709b55f8fe721d25be24304
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776689"
---
# <a name="how-to-create-a-custom-routed-event"></a>方法: カスタム ルーティング イベントを作成する
イベントのルーティングをサポートするために、カスタム イベントを登録する必要があります、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッド。 この例では、カスタム ルーティング イベント作成の基本を紹介します。  
  
## <a name="example"></a>例  
 まず登録次の例に示すように、<xref:System.Windows.RoutedEvent>を使用して、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>メソッド。 慣例により、<xref:System.Windows.RoutedEvent>静的フィールドの名前サフィックスを末尾***イベント***します。 この例では、イベントの名前は`Tap`イベントのルーティング方法で、<xref:System.Windows.RoutingStrategy.Bubble>します。 登録呼び出し後、イベントの add-and-remove [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベント アクセサーを提供できます。  
  
 この特別な例では `OnTap` 仮想メソッド経由でイベントが発生していますが、イベントの発生や変更に対するイベントの反応の仕方はニーズによって変わります。  
  
 この例は、のサブクラス全体を基本的には実装にも注意してください<xref:System.Windows.Controls.Button>; サブクラスであるが、別のアセンブリとしてビルドし、は別にカスタム クラスとしてインスタンス化し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページ。 これはサブクラス化されたコントロールを他のコントロールで構成されたツリーに挿入できるという概念を示すものです。この状況では、このようなコントロールのカスタム イベントには、あらゆるネイティブ [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 要素とまったく同じイベント ルーティング機能が与えられます。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 トンネリング イベントが作成された同じ方法ですが、<xref:System.Windows.RoutedEvent.RoutingStrategy%2A>設定<xref:System.Windows.RoutingStrategy.Tunnel>登録呼び出しで。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のトンネル イベントには接頭辞として "Preview" という単語が付く決まりになっています。  
  
 バブリング イベントの動作例については、「[ルーティング イベントを処理する](how-to-handle-a-routed-event.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ルーティング イベントの概要](routed-events-overview.md)
- [入力の概要](input-overview.md)
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
