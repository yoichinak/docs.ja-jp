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
このトピックでは、 <xref:System.Windows.Freezable> オブジェクトを効果的に使用し、作成する方法を説明します。 Freezable オブジェクトを使用することで、アプリケーションのパフォーマンスを向上させることができます。 Freezable オブジェクトには、ブラシ、ペン、変換、ジオメトリ、アニメーションなどが含まれます。

<a name="whatisafreezable"></a>
## <a name="what-is-a-freezable"></a>Freezable オブジェクトとは
<xref:System.Windows.Freezable> オブジェクトは、非フリーズとフリーズの 2 つの状態を持つ特殊な型です。非フリーズ状態では、 <xref:System.Windows.Freezable> オブジェクトはその他のオブジェクトと同様にふるまいます。フリーズされると、 <xref:System.Windows.Freezable> オブジェクトを変更することはできなくなります。

<xref:System.Windows.Freezable> オブジェクトは、 <xref:System.Windows.Freezable.Changed> イベントによってオブザーバーにオブジェクトの変更を通知します。 <xref:System.Windows.Freezable> オブジェクトをフリーズすると、変更通知にリソースを費やす必要がなくなるため、パフォーマンスを向上させることができます。フリーズ状態の <xref:System.Windows.Freezable> オブジェクトはスレッド間で共有することもできます。非フリーズ状態の <xref:System.Windows.Freezable> オブジェクトをスレッド間で共有することはできません。

<xref:System.Windows.Freezable> クラスには多くの用途がありますが、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションで <xref:System.Windows.Freezable> オブジェクトが最も使用されているのはグラフィックス サブシステム関連です。

<xref:System.Windows.Freezable> クラスは、グラフィックス システムの特定のオブジェクトを使用しやすくし、アプリケーションのパフォーマンスを向上させることができます。 <xref:System.Windows.Freezable> を継承する型には、 <xref:System.Windows.Media.Brush> 、 <xref:System.Windows.Media.Transform> 、 <xref:System.Windows.Media.Geometry> クラスなどがあります。アンマネージ リソースが含まれているため、システムはこれらのオブジェクトの変更を監視し、変更時に対応するアンマネージ リソースを更新する必要があります。グラフィックス システムのオブジェクトを実際には変更しない場合でも、変更される場合に備えて、システムはいくらかのリソースを使ってオブジェクトを監視する必要があります。

たとえば、 <xref:System.Windows.Media.SolidColorBrush> ブラシを作成し、ボタンの背景を描画するのに使用する場合を考えましょう。

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  

ボタンが描画されるとき、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス サブシステムは、ボタンの外観を作成するために、ピクセルのグループを描画するのに指定した情報を使用します。単色ブラシを使用してボタンを描画する方法について説明しますが、単色ブラシが実際に描画するのではありません。グラフィックス システムは、ボタンやブラシに対応する高速で低レベルのオブジェクトを生成し、それが実際に画面に表示されます。

ブラシを変更する場合は、これらの低レベルのオブジェクトを再び生成する必要があります。 Freezable クラスは、ブラシに対応する低レベル オブジェクトを検索して変更時に更新する機能を付与します。この機能が有効のとき、ブラシは「非フリーズ状態」であると言われます。

Freezable オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> メソッドによって、この自己更新機能を無効にすることができます。 このメソッドを使用すると、ブラシは「フリーズ状態」つまり変更不可能な状態になります。

> [!NOTE]
> すべての Freezable オブジェクトがフリーズできるわけではありません。 <xref:System.InvalidOperationException> をスローされることを回避するために、Freezable オブジェクトの <xref:System.Windows.Freezable.CanFreeze%2A> プロパティ値を確認して、フリーズできるかどうかを事前に判断します。

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

Freezable オブジェクトを変更する必要がなくなったときにそれをフリーズすることには、パフォーマンス上の利点があります。この例のブラシをフリーズすれば、ブラシが変更されないと分かっているので、グラフィックス システムはさらなる最適化をすることができます。

> [!NOTE]
> 便宜上、Freezable オブジェクトは、明示的にフリーズしない限りフリーズされません。

<a name="frozenfreezables"></a>
## <a name="using-freezables"></a>Freezable オブジェクトの使用
非フリーズの Freezable オブジェクトは他の型のオブジェクトと同様に使用できます。次の例では、 <xref:System.Windows.Media.SolidColorBrush> を使用してボタンの背景を描画した後に、その色を黄色から赤に変更します。グラフィックス システムは、次の画面更新時に、ボタンの色を黄色から赤に自動的に更新します。

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  

### <a name="freezing-a-freezable"></a>Freezable オブジェクトをフリーズする
<xref:System.Windows.Freezable> オブジェクトを変更不可の状態にするには、その <xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出す必要があります。Freezable オブジェクトを格納しているオブジェクトをフリーズすると、それらのオブジェクトも同様にフリーズされます。例えば、 <xref:System.Windows.Media.PathGeometry> をフリーズすると、それに含まれる図やセグメントも同時にフリーズされます。

Freezable オブジェクトは次のいずれかに該当する場合、フリーズ**できません**。

- アニメーション化されたまたは、データ バインドされたプロパティを持つ。

- 動的リソースによって設定されるプロパティを持つ。(動的リソースの詳細については[XAML リソース](xaml-resources.md)を参照)

- フリーズできない <xref:System.Windows.Freezable> オブジェクトを含む。

これらの条件が false で、その <xref:System.Windows.Freezable> オブジェクトを変更する予定がない場合、それをフリーズすることで前述の通りパフォーマンスの利点を得られます。

Freezable オブジェクトの <xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出したら、その後は変更することができません。フリーズされたオブジェクトを変更しようとすると、 <xref:System.InvalidOperationException> がスローされます。次のコードは、フリーズした後にブラシを変更しようとするので、例外をスローします。

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  

この例外をスローすることを避けるために、 <xref:System.Windows.Freezable.IsFrozen%2A> メソッドを使用して <xref:System.Windows.Freezable> がフリーズされているかを調べられます。

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

上記のコード例では、<xref:System.Windows.Freezable.Clone%2A>メソッドを使用してフリーズされたオブジェクトの変更可能なコピーを作成しました。次のセクションでは、複製の作成について説明します。

**注** フリーズされた Freezable オブジェクトはアニメーションできないため、フリーズされた <xref:System.Windows.Freezable> オブジェクトを <xref:System.Windows.Media.Animation.Storyboard> でアニメーションしようとすると、アニメーション システムはオブジェクトの変更可能な複製を自動的に作成します。複製によるパフォーマンスのオーバーヘッドをなくすため、オブジェクトをアニメーションする場合には、それを非フリーズ状態のままにしておきます。ストーリーボードを使用したアニメーションの詳細については、[ストーリー ボードの概要](../graphics-multimedia/storyboards-overview.md) を参照してください。

### <a name="freezing-from-markup"></a>マークアップからのフリーズ  
マークアップで宣言された <xref:System.Windows.Freezable> オブジェクトをフリーズするには、 `PresentationOptions:Freeze` 属性を使用します。次の例では、<xref:System.Windows.Media.SolidColorBrush> はページ リソースとして宣言され、フリーズされ、ボタンの背景として設定されています。

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  

`Freeze` 属性を使用するには、Presentation Options 名前空間（ `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` ）にマッピングする必要があります。この名前空間をマッピングするために、 `PresentationOptions` というプレフィックスを使用することを推奨します。

```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  

この属性を認識しない XAML リーダーもあるため、 [mc: Ignorable 属性](mc-ignorable-attribute.md) を使用して、 `Presentation:Freeze` 属性を無視できるよう設定しておくことをお勧めします。

```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
詳細については、 [mc: Ignorable 属性](mc-ignorable-attribute.md) を参照してください。
  
### <a name="unfreezing-a-freezable"></a>Freezable オブジェクトを「フリーズ解除する」
一度フリーズされると、<xref:System.Windows.Freezable>は変更されたり解凍されたりすることはありません。ただし、<xref:System.Windows.Freezable.Clone%2A>メソッドまたは<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドを使用して、フリーズされていない複製を作成できます。
  
次の例では、ブラシを使用してボタンの背景を設定し、その後ブラシは固定されます。そのブラシの非フリーズ状態の複製を、<xref:System.Windows.Freezable.Clone%2A>メソッドを使用して作成します。そのクローンを変更し、ボタンの背景を黄色から赤に変更するために使用します。
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  どのメソッドを使用して複製しても、新しい <xref:System.Windows.Freezable> オブジェクトにアニメーションはコピーされません。
  
<xref:System.Windows.Freezable.Clone%2A>と<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドは、フリーズ可能オブジェクトの詳細コピーを作成します。フリーズ可能オブジェクトに他のフリーズされたフリーズ可能オブジェクトが含まれている場合は、それらも複製されて変更可能になります。たとえば、フリーズされた<xref:System.Windows.Media.PathGeometry>を修正して修正可能にすると、それに含まれる図形とセグメントもコピーされて修正可能になります。
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>Freezable クラスの作成
<xref:System.Windows.Freezable> から派生したクラスには次の機能が付与されます。
  
- 特殊な状態：読み取り専用 (フリーズ)状態と書き込み可能な状態。
  
- スレッドの安全性。 フリーズされた<xref:System.Windows.Freezable>は、スレッド間で共有することができます。 
  
- 詳細な変更通知：その他の <xref:System.Windows.DependencyObject> とは異なり、 Freezable オブジェクトはサブ プロパティの値が変更されたときに通知します。
  
- 簡単に複製：Freezable クラスは既にディープ クローンを作成する複数のメソッドを実装します。
  
<xref:System.Windows.Freezable> は <xref:System.Windows.DependencyObject> の一種であり、依存関係プロパティ システムを使用します。クラスのプロパティを依存関係プロパティにする必要はありませんが、<xref:System.Windows.Freezable> クラスは依存関係プロパティを考慮して設計さているので、依存関係プロパティを使用すればコード量を減らすことができます。依存関係プロパティ システムの詳細については、 [依存関係プロパティの概要](dependency-properties-overview.md) を参照してください。
  
<xref:System.Windows.Freezable> から派生するクラスは、 <xref:System.Windows.Freezable.CreateInstanceCore%2A>メソッドをオーバーライドする必要があります。すべてのデータに依存関係プロパティを使用している場合は、それでおしまいです。
  
依存関係プロパティ以外のデータ メンバーが含まれている場合は、次のメソッドもオーバーライドする必要があります。
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
依存関係プロパティ以外のデータ メンバーの読み書きでは、次のルールを守ってください。
  
- 依存関係プロパティ以外のデータ メンバーを読み取る [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] の最初に、 <xref:System.Windows.Freezable.ReadPreamble%2A> メソッドを呼び出す。
  
- 依存関係プロパティ以外のデータ メンバーを書き込む [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の最初に、 <xref:System.Windows.Freezable.WritePreamble%2A> メソッドを呼び出す。 (<xref:System.Windows.Freezable.WritePreamble%2A> を呼び出した後は、同じ [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 内で依存関係プロパティ以外のデータ メンバーを読み取るとしても、<xref:System.Windows.Freezable.ReadPreamble%2A> を呼び出す必要はありません。)
  
- 依存関係プロパティ以外のデータ メンバーの書き込みを含むメソッドを終了する前に、 <xref:System.Windows.Freezable.WritePostscript%2A> メソッドを呼び出す。
  
クラスに、<xref:System.Windows.DependencyObject> オブジェクトではあっても依存関係プロパティではないデータ メンバーが含まれている場合、その値のいずれかを変更するたびに、それを `null` 設定する場合であっても、<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> メソッドを呼び出す必要があります。
  
> [!NOTE]
>  <xref:System.Windows.Freezable> オブジェクトのメソッドをオーバーライドする時に、基底クラスの実装を呼び出すことは非常に重要です。
  
カスタム <xref:System.Windows.Freezable> クラスの例については、 [カスタム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=159981) を参照してください。
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Freezable>
- [カスタム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=159981)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
