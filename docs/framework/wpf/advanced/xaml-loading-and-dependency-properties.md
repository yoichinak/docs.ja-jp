---
title: XAML 読み込みと依存関係プロパティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: ed608a658b5077a20ed56419c4ac731641610e3d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373076"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 読み込みと依存関係プロパティ
現在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、本質的に、依存関係プロパティに注意してください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バイナリの読み込み時にプロセッサに依存関係プロパティのプロパティ システムのメソッドが使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と依存関係プロパティの属性を処理します。 これにより、プロパティ ラッパーが効果的にバイパスされます。 この動作を考慮する必要があり、プロパティ システムのメソッド以外、プロパティのラッパーで、他のコードを配置することを避ける必要がありますカスタム依存関係プロパティを実装するときに<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>します。  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、コンシューマーと作成者の両方としての依存関係プロパティを理解し、読み取りがある前提としています[依存関係プロパティの概要](dependency-properties-overview.md)と[カスタム依存関係プロパティ](custom-dependency-properties.md)します。 読み取りが[XAML の概要 (WPF)](xaml-overview-wpf.md)と[XAML 構文の詳細](xaml-syntax-in-detail.md)します。  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML ローダーの実装とパフォーマンス  
 実装上の理由からは、依存関係プロパティとしてプロパティを特定し、プロパティ システムにアクセスする小さい負荷<xref:System.Windows.DependencyObject.SetValue%2A>それではなくプロパティ ラッパーとそのセッターを使用して設定します。 これは、ため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、型およびメンバーのマークアップは、さまざまな文字列の構造で示されたリレーションシップを知ることのみを基になるコードの全体のオブジェクト モデルを推論する必要があります。  
  
 種類は、xmlns とアセンブリの属性が属性として設定されているをサポートすることを決定する、メンバーを識別するの組み合わせによって検索され、広範なリフレクション プロパティ値をサポートするどのような種類がそれ以外の場合は解決する必要があります。使用して<xref:System.Reflection.PropertyInfo>します。 指定した型の依存関係プロパティは、プロパティ システムを通じてストレージ テーブルとしてアクセスできるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、このテーブルを使用しのプロパティを指定された*ABC*呼び出すことによってより効率的に設定できる<xref:System.Windows.DependencyObject.SetValue%2A>で格納している<xref:System.Windows.DependencyObject>を依存関係プロパティの識別子を使用して型を派生*ABCProperty*します。  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>カスタム依存関係プロパティの影響  
 ため、現在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロパティ設定のプロセッサの動作がまったくラッパーをバイパスする、カスタム依存関係プロパティに、ラッパーのセットの定義に追加のロジックを追加する必要ありません。 セットの定義でこのようなロジックを配置する場合、プロパティが設定されている場合、ロジックは実行されません[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードではなく。  
  
 同様に、その他の側面、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]からプロパティ値を取得するプロセッサ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用の処理も<xref:System.Windows.DependencyObject.GetValue%2A>ラッパーを使用するのではなく。 また必要がありますで実装しないようにするため、`get`を超えて定義、<xref:System.Windows.DependencyObject.GetValue%2A>呼び出します。  
  
 次の例として、プロパティの識別子を格納する場所のラッパーで推奨される依存関係プロパティの定義を`public` `static` `readonly`フィールド、および`get`と`set`定義コードがありませんバックアップの依存関係プロパティを定義するために必要なプロパティ システム方法。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>関連項目
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [コレクション型依存関係プロパティ](collection-type-dependency-properties.md)
- [依存関係プロパティのセキュリティ](dependency-property-security.md)
- [DependencyObject の安全なコンストラクター パターン](safe-constructor-patterns-for-dependencyobjects.md)
