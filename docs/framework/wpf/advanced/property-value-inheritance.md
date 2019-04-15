---
title: プロパティ値の継承
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: 48543d2cfc11fc33dff6239cdfd7bfcd946e986a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186830"
---
# <a name="property-value-inheritance"></a>プロパティ値の継承
プロパティ値の継承は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの機能です。 プロパティ値の継承により、要素のツリー内の子要素は、親要素から特定のプロパティの値を取得できます。これは、最も近い親要素のいずれかに設定されているとおりにその値を継承することで行われます。 親要素もプロパティ値の継承を通じてその値を取得している場合があるため、システムはページ ルートまで再帰している可能性があります。 プロパティ値の継承は、プロパティ システムの既定の動作ではありません。あるプロパティに子要素でのプロパティ値の継承を実行させるには、そのプロパティに特定のメタデータを設定する必要があります。  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>プロパティ値の継承は包含継承である  
 ここで言う "継承" は、型や一般的なオブジェクト指向プログラミングのコンテキストにおける継承 (派生クラスがその基底クラスからメンバー定義を継承する) とは若干異なる概念です。 この意味での継承は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でも使用されます。さまざまな基底クラスで定義されたプロパティは、要素として使用される場合の派生 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] クラスの属性として、およびコードのメンバーとして公開されます。 プロパティ値の継承は、要素のツリー内の親子のリレーションシップに基づいて、ある要素から別の要素にプロパティ値が継承されるしくみに特に関連します。 その要素のツリーが最も直接的に認識されるのは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップでアプリケーションを定義する際にさまざまな要素を別の要素内に入れ子にする場合です。 オブジェクトのツリーはプログラムで作成することもできます。これを行うには、オブジェクトを別のオブジェクトの指定したコレクションに追加します。完成したツリーでも、実行時にプロパティ値の継承が同様に動作します。  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>プロパティ値の継承を実際の応用例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] には、プロパティの継承が有効なプロパティがいくつか含まれています。 これらのプロパティの一般的なシナリオは次のとおりです。これらのプロパティは、ページごとに一度だけ設定するのが適していますが、いずれかの基本要素クラスのメンバーでもあるため、ほとんどの子要素にも存在することになります。 たとえば、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティ コントロールの方向のフロー コンテンツの表示し、ページ上に配置する必要があります。 通常、テキスト フローの概念は、すべての子要素で一貫して処理される必要があります。 要素ツリーのあるレベルにおいて、何らかの理由でユーザーまたは環境の操作によってフロー方向がリセットされた場合は、一般に要素全体でリセットする必要があります。 ときに、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティは、継承するようにした場合は、値を設定またはアプリケーション内の各ページの表示ニーズをすべて含む要素ツリーのレベルにリセット 1 回のみ必要があります。 初期既定値であっても、同様の方法で値を継承します。 プロパティ値の継承モデルでは、要素の値を個別にリセットすることもできます。これは、複数のフロー方向の混在を意図したまれなケースに対応するためです。  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>カスタム プロパティを継承可能にする  
 カスタム プロパティのメタデータを変更することで、独自のカスタム プロパティを継承可能にすることもできます。 ただし、プロパティを継承可能にする場合は、パフォーマンスについて考慮する必要があります。 ローカル値や、スタイル、テンプレート、またはデータ バインディングから取得した値がそのプロパティに設定されていない場合、継承可能なプロパティは、それ自身に割り当てられた値を論理ツリー内のすべての子要素に提供します。  
  
 プロパティを値の継承に参加させるには、「[添付プロパティを登録する](how-to-register-an-attached-property.md)」の説明に従ってカスタム添付プロパティを作成します。 プロパティ メタデータを登録 (<xref:System.Windows.FrameworkPropertyMetadata>) し、そのメタデータ内のオプション設定で「継承」オプションを指定します。 また、値が継承されるようになったため、プロパティに既定値が設定されていることも確認します。 プロパティを添付プロパティとして登録しましたが、"非添付" の依存関係プロパティの場合と同様に、所有者型で get アクセスおよび set アクセスのプロパティ "ラッパー" を作成することもできます。 その後、継承可能なプロパティが設定することも、所有者型または派生型は、ダイレクトのプロパティのラッパーを使用して、またはいずれかで、添付プロパティの構文を使用して設定できます<xref:System.Windows.DependencyObject>します。  
  
 添付プロパティのグローバル プロパティのような概念的にはいずれかの値をチェックすることができます<xref:System.Windows.DependencyObject>し、有効な結果を取得します。 添付プロパティの一般的なシナリオは、子要素のプロパティ値を設定するのには、このシナリオは、該当するプロパティが添付プロパティは常に各要素に対して添付プロパティとして暗黙的に存在する場合より効果的な (<xref:System.Windows.DependencyObject>) ツリーでします。  
  
> [!NOTE]
>  プロパティ値の継承は、非添付依存関係プロパティについても機能しているように見えることがありますが、ランタイム ツリーでの特定の要素の境界を介する非添付プロパティの継承動作は定義されていません。 常に使用する<xref:System.Windows.DependencyProperty.RegisterAttached%2A>に指定したプロパティを登録する<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>メタデータにします。  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>ツリー境界を越えてプロパティ値を継承する  
 プロパティの継承は、要素のツリーを走査して行われます。 多くの場合、このツリーは論理ツリーに対応します。 ただしなど、要素ツリーを定義するマークアップに WPF コア レベルのオブジェクトを含めるたびに、 <xref:System.Windows.Media.Brush>、不連続の論理ツリーを作成しました。 を通じて概念的に拡張されていない場合は true。 論理ツリー、<xref:System.Windows.Media.Brush>論理ツリーは WPF フレームワーク レベルの概念であるためです。 これのメソッドを使用する場合、結果に反映を確認できます<xref:System.Windows.LogicalTreeHelper>します。 ただし、プロパティ値の継承の論理ツリー内のこのギャップを埋めることができ、継承可能なプロパティが添付プロパティとありません意図的な継承ブロッキング境界として登録されている限り、継承された値を受け渡すことができます (など、 <xref:System.Windows.Controls.Frame>) が発生しました。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [添付プロパティの概要](attached-properties-overview.md)
- [依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)
