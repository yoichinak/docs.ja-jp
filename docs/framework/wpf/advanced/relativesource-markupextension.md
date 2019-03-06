---
title: RelativeSource のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: a6a7d615a3a54fbc75bb86b295fdf80433a31dc5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476335"
---
# <a name="relativesource-markupextension"></a>RelativeSource のマークアップ拡張機能

プロパティを指定します、<xref:System.Windows.Data.RelativeSource>内で使用する、バインディング ソースを[バインディング マークアップ拡張](binding-markup-extension.md)を設定するとき、または、<xref:System.Windows.Data.Binding.RelativeSource%2A>のプロパティを<xref:System.Windows.Data.Binding>XAML に設定されている要素。

## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML 属性の使用方法 (バインディング拡張内で入れ子にした場合)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

- または -

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a>XAML 値

|||
|-|-|
|`modeEnumValue`|次のいずれかになります。<br /><br /> -文字列トークン`Self`; に対応する、<xref:System.Windows.Data.RelativeSource>使用作成すると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.Self>します。<br />-文字列トークン`TemplatedParent`; に対応する、<xref:System.Windows.Data.RelativeSource>使用作成すると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>します。<br />-文字列トークン`PreviousData`; に対応する、<xref:System.Windows.Data.RelativeSource>使用作成すると、<xref:System.Windows.Data.RelativeSource.Mode%2A>プロパティに設定<xref:System.Windows.Data.RelativeSourceMode.PreviousData>します。<br />-以下をご覧ください情報で`FindAncestor`モード。|
|`FindAncestor`|文字列トークン `FindAncestor`。 このトークンを使用すると、`RelativeSource` によって先祖の型およびオプションで先祖レベルを指定するモードになります。 これは、<xref:System.Windows.Data.RelativeSource> プロパティが <xref:System.Windows.Data.RelativeSource.Mode%2A> に設定された状態で作成された <xref:System.Windows.Data.RelativeSourceMode.FindAncestor> に対応します。|
|`typeName`|
  `FindAncestor` モードで必要です。 
  <xref:System.Windows.Data.RelativeSource.AncestorType%2A> プロパティに指定する型の名前。|
|`intLevel`|
  `FindAncestor` モードのオプションです。 論理ツリー内で親の方向に向けて数えた先祖レベル。|

## <a name="remarks"></a>Remarks

`{RelativeSource TemplatedParent}` バインディングの用法は、コントロールの UI とコントロールのロジックの分離のより大きな概念に対応するキーの手法です。 これによって、テンプレートが適用される親 (テンプレートが適用されるランタイム オブジェクト インスタンス) へのバインディングをテンプレート定義内から行うことができます。 この場合、 [TemplateBinding マークアップ拡張機能](templatebinding-markup-extension.md)は実際のバインディング式の短縮形:`{Binding RelativeSource={RelativeSource TemplatedParent}}`します。 `TemplateBinding` または`{RelativeSource TemplatedParent}`の使用方法はどちらも、テンプレートを定義する XAML 内にのみ関連します。 詳細については、次を参照してください[TemplateBinding マークアップ拡張機能。](templatebinding-markup-extension.md)

`{RelativeSource FindAncestor}` コントロールが常に必要な場合に特定の先祖の型のビジュアル ツリー内のケースのコントロールのテンプレートまたは予測可能な自己完結型の UI コンポジションで主に使用します。 たとえば、項目コントロールの各項目は `FindAncestor` を使用して、その項目コントロールの親先祖のプロパティにバインドすることができます。 または、テンプレート内のコントロール合成に参加している要素は、同じ合成体系の親要素に対して `FindAncestor` バインディングを使用できます。

XAML 構文のセクションに示した `FindAncestor` モードのオブジェクト要素構文では、2 番目のオブジェクト要素構文は `FindAncestor` モード向けに使用されます。 `FindAncestor` モードでは、<xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値が必要です。 設定する必要があります<xref:System.Windows.Data.RelativeSource.AncestorType%2A>を使用して、属性として、 [X:type マークアップ拡張機能](../../xaml-services/x-type-markup-extension.md)検索する先祖の型への参照。 
  <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 値は、実行時にバインディング要求を処理する際に使用されます。


  `FindAncestor` モードでは、オプションの <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> プロパティは、要素ツリー内に型の先祖が複数存在する可能性がある場合に、先祖の検索のあいまいさを解消するのに役立ちます。


  `FindAncestor` モードの使用方法の詳細については、「<xref:System.Windows.Data.RelativeSource>」を参照してください。

`{RelativeSource Self}` シナリオに便利ですが、インスタンスの 1 つのプロパティが、同じインスタンスと通常の依存関係プロパティ リレーションシップはありません (強制型変換) などの別のプロパティの値に依存既に間それら 2 つのプロパティが存在します。 値はリテラルと同じです (とは、型指定と同じ) になるように、2 つのプロパティがオブジェクトに存在を適用することもまれですが、`Converter`パラメーターを持つバインドを`{RelativeSource Self}`ソース間で変換するコンバーターを使用して、対象の型。 別のシナリオの`{RelativeSource Self}`の一部として、<xref:System.Windows.MultiDataTrigger>します。

たとえば、<xref:System.Windows.Shapes.Rectangle> という XAML は、<xref:System.Windows.FrameworkElement.Width%2A> 要素を定義します。<xref:System.Windows.Shapes.Rectangle> にどのような値が入力されても、`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>` は常に正方形となります。

`{RelativeSource PreviousData}` データ テンプレート、またはバインディングを使用しているコレクションをデータ ソースとしての場合に便利です。 使用することができます`{RelativeSource PreviousData}`をコレクション内の連続するデータ項目間のリレーションシップを強調表示します。 これと関連して、データ ソース内の現在の項目と直前の項目との間に <xref:System.Windows.Data.MultiBinding> を確立し、そのバインディング上のコンバーターを使用して、2 つの項目 (およびそれらのプロパティ) 間の相違を特定する手法もあります。

次の例の項目テンプレートに出現する 1 つ目の <xref:System.Windows.Controls.TextBlock> は、現在の数値を表示します。 2 番目の<xref:System.Windows.Controls.TextBlock>バインディングが、<xref:System.Windows.Data.MultiBinding>名目上が 2 つ<xref:System.Windows.Data.Binding>利用者: 現在のレコードとを使用して、前のデータ レコードを意図的に使用するバインディングを`{RelativeSource PreviousData}`。 
  <xref:System.Windows.Data.MultiBinding> 上のコンバーターが、両者の差を計算し、バインディングに返します。

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

ここでは、概念が未カバーとしては、データ バインディングを記述するを参照してください[データ バインディングの概要](../data/data-binding-overview.md)します。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ実装では、このマークアップ拡張機能の処理がによって定義されている、<xref:System.Windows.Data.RelativeSource>クラス。

`RelativeSource` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が、属性を処理する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.Binding>
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [バインディング宣言の概要](../data/binding-declarations-overview.md)
- [x:Type マークアップ拡張機能](../../xaml-services/x-type-markup-extension.md)
