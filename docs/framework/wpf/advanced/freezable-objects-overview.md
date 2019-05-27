---
title: Freezable オブジェクトの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 1b0bc360c4c04457e71115dc5caf935841a2bbc1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619637"
---
# <a name="freezable-objects-overview"></a>Freezable オブジェクトの概要
このトピックでは、効果的に使用し、作成する方法を説明します。<xref:System.Windows.Freezable>オブジェクトで、アプリケーションのパフォーマンスの向上に役立つ特殊な機能を提供します。 Freezable オブジェクトの例には、ブラシ、ペン、変換、ジオメトリ、およびアニメーションが含まれます。  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>Freezable オブジェクトとは  
 <xref:System.Windows.Freezable> オブジェクトは、非フリーズとフリーズの 2 つの状態を持つ特殊な型です。 非フリーズ状態では、 <xref:System.Windows.Freezable> オブジェクトはその他のオブジェクトと同様にふるまいます。 フリーズされると、 <xref:System.Windows.Freezable> オブジェクトを変更することはできなくなります。  
  
 A<xref:System.Windows.Freezable>提供、<xref:System.Windows.Freezable.Changed>を変更したり、オブジェクトのオブザーバーに通知するイベントです。 固定、<xref:System.Windows.Freezable>変更通知にリソースを費やす必要がなくなったために、パフォーマンスが向上することができます。 固定された<xref:System.Windows.Freezable>フリーズされていないときに、スレッド間で共有することも<xref:System.Windows.Freezable>ことはできません。  
  
 <xref:System.Windows.Freezable> クラスには多くの用途がありますが、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションで <xref:System.Windows.Freezable> オブジェクトが最も使用されているのはグラフィックス サブシステム関連です。  
  
 <xref:System.Windows.Freezable> クラスは、グラフィックス システムの特定のオブジェクトを使用しやすくし、アプリケーションのパフォーマンスを向上させることができます。 <xref:System.Windows.Freezable> を継承する型には、 <xref:System.Windows.Media.Brush> 、 <xref:System.Windows.Media.Transform> 、 <xref:System.Windows.Media.Geometry> クラスなどがあります。 アンマネージ リソースが含まれているため、システムはこれらのオブジェクトの変更を監視し、変更時に対応するアンマネージ リソースを更新する必要があります。 グラフィックス システムのオブジェクトを実際には変更しない場合でも、変更される場合に備えて、システムはいくらかのリソースを使ってオブジェクトを監視する必要があります。  
  
 たとえば、 <xref:System.Windows.Media.SolidColorBrush> ブラシを作成し、ボタンの背景を描画するのに使用する場合を考えましょう。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 ボタンが描画されるとき、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス サブシステムは、ボタンの外観を作成するために、ピクセルのグループを描画するのに指定した情報を使用します。 単色ブラシを使用してボタンを描画する方法について説明しますが、単色ブラシが実際に描画するのではありません。 グラフィックス システムは、ボタンやブラシに対応する高速で低レベルのオブジェクトを生成し、それが実際に画面に表示されます。  
  
 ブラシを変更する場合は、これらの低レベルのオブジェクトを再び生成する必要があります。 Freezable クラスは、ブラシに対応する低レベル オブジェクトを検索して変更時に更新する機能を付与します。 この機能が有効のとき、ブラシは「非フリーズ状態」であると言われます。  
  
 Freezable オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> メソッドによって、この自己更新機能を無効にすることができます。 このメソッドを使用すると、ブラシは「フリーズ状態」つまり変更不可能な状態になります。  
  
> [!NOTE]
>  すべての Freezable オブジェクトがフリーズできるわけではありません。 <xref:System.InvalidOperationException> をスローされることを回避するために、Freezable オブジェクトの <xref:System.Windows.Freezable.CanFreeze%2A> プロパティ値を確認して、フリーズできるかどうかを事前に判断します。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 フリーズ可能オブジェクトを変更するが不要になったときに固定パフォーマンス上の利点を提供します。 この例では、ブラシを固定する場合は、グラフィックス システムはその変更を監視する必要がなくなります。 グラフィックス システムは、ブラシが変更されないことを知っているために、その他の最適化をこともできます。  
  
> [!NOTE]
>  便宜上、Freezable オブジェクトは、明示的にフリーズしない限りフリーズされません。  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>Freezable オブジェクトの使用  
 非フリーズの Freezable オブジェクトは他の型のオブジェクトと同様に使用できます。 次の例では、 <xref:System.Windows.Media.SolidColorBrush> を使用してボタンの背景を描画した後に、その色を黄色から赤に変更します。 グラフィックス システムは、次の画面更新時に、ボタンの色を黄色から赤に自動的に更新します。  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>Freezable オブジェクトをフリーズする  
 <xref:System.Windows.Freezable> オブジェクトを変更不可の状態にするには、その <xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出す必要があります。 Freezable オブジェクトを格納しているオブジェクトをフリーズすると、それらのオブジェクトも同様にフリーズされます。 例えば、 <xref:System.Windows.Media.PathGeometry> をフリーズすると、それに含まれる図やセグメントも同時にフリーズされます。  
  
 Freezable オブジェクトは次のいずれかに該当する場合、フリーズ**できません**。  
  
- アニメーション化されたまたは、データ バインドされたプロパティを持つ。  
  
- 動的リソースによって設定されるプロパティを持つ。 (動的リソースの詳細については[XAML リソース](xaml-resources.md)を参照)  
  
- フリーズできない <xref:System.Windows.Freezable> オブジェクトを含む。  
  
 これらの条件が false で、その <xref:System.Windows.Freezable> オブジェクトを変更する予定がない場合、それをフリーズすることで前述の通りパフォーマンスの利点を得られます。  
  
 Freezable オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出したら、その後は変更することができません。 フリーズされたオブジェクトを変更しようとすると、 <xref:System.InvalidOperationException> がスローされます。 次のコードは、フリーズした後にブラシを変更しようとするので、例外をスローします。  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 この例外をスローすることを避けるために、 <xref:System.Windows.Freezable.IsFrozen%2A> メソッドを使用して <xref:System.Windows.Freezable> がフリーズされているかを調べられます。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 上記のコード例では、<xref:System.Windows.Freezable.Clone%2A>メソッドを使用してフリーズされたオブジェクトの変更可能なコピーを作成しました。 次のセクションでは、複製の作成について説明します。  
  
 **注**ため、固定された freezable アニメーション化できません、アニメーション システムが自動的の変更可能な複製を作成固定された<xref:System.Windows.Freezable>オブジェクトを使用してアニメーション化しようとすると、 <xref:System.Windows.Media.Animation.Storyboard>。 オーバーヘッドを複製することがパフォーマンスをなくすため、オブジェクトをアニメーション化する場合にマスクされていないままにします。 ストーリー ボードを使用したアニメーション化の詳細については、次を参照してください。、[ストーリー ボードの概要](../graphics-multimedia/storyboards-overview.md)します。  
  
### <a name="freezing-from-markup"></a>マークアップからのフリーズ  
 固定するには、<xref:System.Windows.Freezable>オブジェクトを使用する、マークアップで宣言された、`PresentationOptions:Freeze`属性。 次の例では、<xref:System.Windows.Media.SolidColorBrush>はページ リソースとして宣言されており、固定されています。 ボタンの背景を設定するのには使用されます。  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 使用する、`Freeze`属性、プレゼンテーション オプションの名前空間にマップする必要があります:`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`します。 `PresentationOptions` この名前空間をマッピングするための推奨されるプレフィックスを示します。  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 すべての XAML リーダーは、この属性を認識しているためには、使用することをお勧め、 [mc: Ignorable 属性](mc-ignorable-attribute.md)をマークする、`Presentation:Freeze`属性を無視できます。  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 詳細については、次を参照してください。、 [mc: Ignorable 属性](mc-ignorable-attribute.md)ページ。  
  
### <a name="unfreezing-a-freezable"></a>「固定解除する」フリーズ可能オブジェクト  
 1 回凍結、<xref:System.Windows.Freezable>しない変更またはマスクされていない。 ただし、を使用して、固定された複製を作成することができます、<xref:System.Windows.Freezable.Clone%2A>または<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッド。  
  
 次の例では、ブラシを使用して、ボタンの背景を設定し、そのブラシが固定されてします。 使用して、ブラシの固定のコピーが行われた、<xref:System.Windows.Freezable.Clone%2A>メソッド。 クローンを変更し、ボタンの背景を黄色から赤に変更するために使用します。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  新しいコピーされませんアニメーションに使用する複製方法に関係なく<xref:System.Windows.Freezable>します。  
  
 <xref:System.Windows.Freezable.Clone%2A>と<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドは、フリーズ可能オブジェクトの詳細コピーを作成します。 フリーズ可能オブジェクトに他のフリーズされたフリーズ可能オブジェクトが含まれている場合は、それらも複製されて変更可能になります。 たとえば、フリーズされた<xref:System.Windows.Media.PathGeometry>を修正して修正可能にすると、それに含まれる図形とセグメントもコピーされて修正可能になります。  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Freezable クラスの作成  
 派生したクラス<xref:System.Windows.Freezable>次の機能を取得します。  
  
- 特殊な状態。 読み取り専用 (固定)、書き込み可能な状態です。  
  
- スレッド セーフ。 固定された<xref:System.Windows.Freezable>スレッド間で共有することができます。  
  
- 変更の詳細についての通知:その他とは異なり<xref:System.Windows.DependencyObject>、フリーズ可能オブジェクトは変更通知サブ プロパティの値を変更するときにします。  
  
- 簡単に複製: Freezable クラスは既にディープ クローンを生成するいくつかのメソッドを実装します。  
  
 A<xref:System.Windows.Freezable>の種類は、<xref:System.Windows.DependencyObject>をそのため、依存関係プロパティ システムを使用します。 クラスのプロパティは、依存関係プロパティにする必要はありませんが、ために書き込むがあるコードの量を減らすは依存関係プロパティを使用して、<xref:System.Windows.Freezable>クラスは依存関係プロパティを考慮して設計されました。 依存関係プロパティ システムの詳細については、次を参照してください。、[依存関係プロパティの概要](dependency-properties-overview.md)します。  
  
 すべて<xref:System.Windows.Freezable>サブクラスをオーバーライドする必要があります、<xref:System.Windows.Freezable.CreateInstanceCore%2A>メソッド。 クラスは、そのすべてのデータの依存関係プロパティを使用している場合は、完了します。  
  
 クラスに依存関係のないプロパティのデータ メンバーが含まれている場合は、次のメソッドもオーバーライドする必要があります。  
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 次のルールにアクセスして、依存関係プロパティではないデータ メンバーへの書き込みにも注意してください。  
  
- いずれかの先頭に[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]呼び出し、依存関係のないプロパティのデータ メンバーを読み取る、<xref:System.Windows.Freezable.ReadPreamble%2A>メソッド。  
  
- 依存関係のないプロパティのデータ メンバーを書き込む任意の API の先頭には、呼び出し、<xref:System.Windows.Freezable.WritePreamble%2A>メソッド。 (呼び出したら<xref:System.Windows.Freezable.WritePreamble%2A>で、[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]への呼び出しを追加する必要はありません<xref:System.Windows.Freezable.ReadPreamble%2A>も非依存関係プロパティのデータ メンバーを読み取るかどうかです)。  
  
- 呼び出す、<xref:System.Windows.Freezable.WritePostscript%2A>依存関係のないプロパティのデータ メンバーへの書き込みメソッドを終了する前にメソッド。  
  
 クラスにある非依存関係プロパティのデータ メンバーが含まれて かどうか<xref:System.Windows.DependencyObject>オブジェクトも呼び出す必要があります、<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>メソッドは、メンバーを設定している場合でも、その値のいずれかを変更するたびに`null`します。  
  
> [!NOTE]
>  各を開始することが非常に重要<xref:System.Windows.Freezable>基本実装への呼び出しでオーバーライドするメソッド。  
  
 カスタムの例については<xref:System.Windows.Freezable>クラスを参照してください、[カスタム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=159981)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Freezable>
- [カスタム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=159981)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
