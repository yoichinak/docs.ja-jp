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
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141538"
---
# <a name="collection-type-dependency-properties"></a>コレクション型依存関係プロパティ
ここでは、プロパティの型がコレクション型である場合に依存関係プロパティを実装する方法についての、ガイダンスと推奨されるパターンを示します。  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>コレクション型依存関係プロパティの実装  
 一般に、依存関係プロパティの実装パターンでは、CLR<xref:System.Windows.DependencyProperty>プロパティ ラッパーを定義します。 コレクション型プロパティを実装するときは、これと同じパターンに従います。 ただし、コレクション型プロパティは、コレクション内に含まれる型自体が派生クラスである<xref:System.Windows.DependencyObject><xref:System.Windows.Freezable>場合、パターンに複雑な程度の複雑さを導入します。  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>既定値を上回るコレクションの初期化  
 依存関係プロパティを作成するときは、初期フィールド値としてプロパティの既定値を指定しません。 代わりに、依存関係プロパティのメタデータを使用して既定値を指定します。 プロパティが参照型の場合、依存関係プロパティのメタデータで指定する既定値はインスタンスごとの既定値ではありません。その型のすべてのインスタンスに適用される既定値です。 したがって、コレクション プロパティ メタデータによって定義される単一の静的コレクションを、その型の新しく作成されるインスタンスの作業既定値として使用しないように注意してください。 代わりに、クラス コンストラクターのロジックの一部として、コレクションの値に一意 (インスタンス) のコレクションを意図的に設定する必要があります。 それ以外の場合は、意図しないシングルトン クラスを作成することになります。  
  
 各データ メンバー フィールドが JSON オブジェクトにマップされ、フィールド名がオブジェクトの "key" 部分にマップされ、"value" 部分がオブジェクトの値の部分に再帰的にマップされます。 次の例のセクションでは、既定値の欠陥を含`Aquarium`むクラス の定義を示します。 このクラスは、型制約を持`AquariumObjects`つジェネリック<xref:System.Collections.Generic.List%601>型を使用するコレクション型<xref:System.Windows.FrameworkElement>依存関係プロパティ を定義します。 依存関係プロパティ<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>の呼び出しでは、メタデータは、新しいジェネリック<xref:System.Collections.Generic.List%601>となる既定値を確立します。

> [!WARNING]
> 次のコードは正しく動作しません。

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 ただし、コードをこのままにすると、単一のリストの既定値が `Aquarium` のすべてのインスタンスで共有されます。 次のテスト コードは、2 つの異なる `Aquarium` インスタンスをインスタンス化し、それぞれに単一の異なる `Fish` を追加する方法を示していますが、これを実行すると、想定外の結果になります。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 各コレクションのカウントが 1 になるのではなく、いずれのコレクションもカウントが 2 になります。 これは、各 `Aquarium` で `Fish` が既定値のコレクションに追加されますが、その起因となっているのがメタデータでの単一のコンストラクター呼び出しであり、したがって、すべてのインスタンス間で共有されるためです。 これは望ましい状況ではありません。  
  
 この問題を解決するには、クラス コンストラクターの呼び出しの一部として、コレクションの依存関係プロパティの値を一意のインスタンスにリセットする必要があります。 プロパティは読み取り専用の依存関係プロパティであるため、メソッドを<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>使用して、クラス内でのみアクセス<xref:System.Windows.DependencyPropertyKey>可能な を使用して設定します。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 再びテスト コードを実行すると、結果は期待したものに近くなり、各 `Aquarium` が独自の一意のコレクションをサポートします。  
  
 コレクション プロパティを読み取り/書き込みにすると、このパターンには若干のバリエーションが発生します。 その場合は、パブリック識別子を使用して、セット ラッパー内の<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>非キー シグネチャを呼び出す初期化を実行する、コンストラクターから public <xref:System.Windows.DependencyProperty> set アクセサーを呼び出すことができます。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>コレクション プロパティからのバインディング値変更の報告  
 それ自体が依存関係プロパティであるコレクション プロパティは、変更をサブプロパティに自動的には報告しません。 コレクションにバインディングを作成している場合は、これによってバインディングが変更を報告しないことがあり、一部のデータ バインディング シナリオが無効になります。 ただし、コレクション型としてコレクション型<xref:System.Windows.FreezableCollection%601>を使用する場合は、コレクション内の含まれている要素へのサブプロパティの変更が正しく報告され、バインドは期待どおりに動作します。  
  
 依存関係オブジェクト コレクションでサブプロパティのバインディングを有効にするには、コレクション プロパティを<xref:System.Windows.FreezableCollection%601>type として作成し、そのコレクションに<xref:System.Windows.DependencyObject>対する型制約を派生クラスに対して行います。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FreezableCollection%601>
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
- [データバインディングの概要](../../../desktop-wpf/data/data-binding-overview.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
