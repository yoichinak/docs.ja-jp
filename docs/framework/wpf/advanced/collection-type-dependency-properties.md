---
title: コレクション型依存関係プロパティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: 9ce0b70bfdd70b47857167ff14e62ed2bbda569d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010697"
---
# <a name="collection-type-dependency-properties"></a>コレクション型依存関係プロパティ
ここでは、プロパティの型がコレクション型である場合に依存関係プロパティを実装する方法についての、ガイダンスと推奨されるパターンを示します。  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>コレクション型依存関係プロパティの実装  
 依存関係プロパティの一般に従う実装パターンが定義する、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティ ラッパーをそのプロパティはによって支えられて、<xref:System.Windows.DependencyProperty>識別子ではなく、フィールドまたは他の構造体。 コレクション型プロパティを実装するときは、これと同じパターンに従います。 ただし、コレクション型のプロパティが導入されています、パターンをいくつかの複雑さ、コレクション内に含まれる型自体がたびに、<xref:System.Windows.DependencyObject>または<xref:System.Windows.Freezable>クラスを派生します。  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>既定値を上回るコレクションの初期化  
 依存関係プロパティを作成するときは、初期フィールド値としてプロパティの既定値を指定しません。 代わりに、依存関係プロパティのメタデータを使用して既定値を指定します。 プロパティが参照型の場合、依存関係プロパティのメタデータで指定する既定値はインスタンスごとの既定値ではありません。その型のすべてのインスタンスに適用される既定値です。 したがって、コレクション プロパティ メタデータによって定義される単一の静的コレクションを、その型の新しく作成されるインスタンスの作業既定値として使用しないように注意してください。 代わりに、クラス コンストラクターのロジックの一部として、コレクションの値に一意 (インスタンス) のコレクションを意図的に設定する必要があります。 それ以外の場合は、意図しないシングルトン クラスを作成することになります。  
  
 例を次に示します。 この例は、`Aquarium` クラスの定義を示しています。 クラスは、コレクション型依存関係プロパティを定義します。 `AquariumObjects`、ジェネリックを使用する<xref:System.Collections.Generic.List%601>の種類を、<xref:System.Windows.FrameworkElement>制約を入力します。 <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>依存関係プロパティのメタデータを呼び出し、既定値を新しいジェネリックによって確立<xref:System.Collections.Generic.List%601>します。  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 ただし、コードをこのままにすると、単一のリストの既定値が `Aquarium` のすべてのインスタンスで共有されます。 次のテスト コードは、2 つの異なる `Aquarium` インスタンスをインスタンス化し、それぞれに単一の異なる `Fish` を追加する方法を示していますが、これを実行すると、想定外の結果になります。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 各コレクションのカウントが 1 になるのではなく、いずれのコレクションもカウントが 2 になります。 これは、各 `Aquarium` で `Fish` が既定値のコレクションに追加されますが、その起因となっているのがメタデータでの単一のコンストラクター呼び出しであり、したがって、すべてのインスタンス間で共有されるためです。 これは望ましい状況ではありません。  
  
 この問題を解決するには、クラス コンストラクターの呼び出しの一部として、コレクションの依存関係プロパティの値を一意のインスタンスにリセットする必要があります。 使用するプロパティが読み取り専用の依存関係プロパティであるため、<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>メソッドを使用して、設定を<xref:System.Windows.DependencyPropertyKey>はクラス内でアクセス可能です。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 再びテスト コードを実行すると、結果は期待したものに近くなり、各 `Aquarium` が独自の一意のコレクションをサポートします。  
  
 コレクション プロパティを読み取り/書き込みにすると、このパターンには若干のバリエーションが発生します。 その場合は、初期化の非キーの署名を呼び出すことも、これを行うコンス トラクターからパブリック set アクセサーを呼び出すことができます<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>、set ラッパー内でパブリックを使用して<xref:System.Windows.DependencyProperty>識別子。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>コレクション プロパティからのバインディング値変更の報告  
 それ自体が依存関係プロパティであるコレクション プロパティは、変更をサブプロパティに自動的には報告しません。 コレクションにバインディングを作成している場合は、これによってバインディングが変更を報告しないことがあり、一部のデータ バインディング シナリオが無効になります。 ただし、コレクション型を使用する場合<xref:System.Windows.FreezableCollection%601>コレクション型として、コレクション内に含まれる要素に対するサブプロパティの変更が正しく報告され、バインドが期待どおりに動作します。  
  
 依存関係オブジェクト コレクションでサブプロパティのバインディングを有効にするには、型としてコレクション プロパティを作成<xref:System.Windows.FreezableCollection%601>、いずれかにそのコレクションの型制約<xref:System.Windows.DependencyObject>クラスを派生します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FreezableCollection%601>
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
