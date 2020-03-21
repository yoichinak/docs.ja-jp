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
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186248"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 読み込みと依存関係プロパティ
[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの現在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装は、本質的に依存関係プロパティを認識しています。 プロセッサ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、依存関係プロパティであるバイナリ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性および処理属性を読み込むときに、依存関係プロパティのプロパティ システム メソッドを使用します。 これにより、プロパティ ラッパーが事実上バイパスされます。 カスタム依存関係プロパティを実装する場合は、この動作を考慮する必要があり、プロパティ システム メソッドおよび プロパティ システム メソッド<xref:System.Windows.DependencyObject.GetValue%2A>以外の<xref:System.Windows.DependencyObject.SetValue%2A>他のコードをプロパティ ラッパーに配置しないようにする必要があります。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、コンシューマーと作成者の両方として依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」 および 「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照していることを前提としています。 [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)と[XAML 構文の詳細](xaml-syntax-in-detail.md)も読んでください。  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML ローダーの実装とパフォーマンス  
 実装上の理由から、プロパティラッパーとそのセッターを使用するのではなく、プロパティを依存関係プロパティとして識別し、<xref:System.Windows.DependencyObject.SetValue%2A>プロパティ システム メソッドにアクセスして設定する方が、計算コストが低くなります。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサが、マークアップとさまざまな文字列の構造によって示される型とメンバーの関係を知ることに基づいて、バッキング コードのオブジェクト モデル全体を推論する必要があるためです。  
  
 型は xmlns とアセンブリ属性の組み合わせを通じて検索されますが、メンバーを識別し、属性として設定できるメンバーを特定し、プロパティ値がサポートする型を解決するには、 を使用<xref:System.Reflection.PropertyInfo>して広範なリフレクションが必要になります。 特定の型の依存関係プロパティは、プロパティ システムを通じてストレージ テーブルとしてアクセス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]できるため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装はこのテーブルを使用し、依存プロパティ識別子*ABCProperty*を使用して、格納元<xref:System.Windows.DependencyObject.SetValue%2A><xref:System.Windows.DependencyObject>の派生型を呼び出すことによって、任意のプロパティ*ABC*をより効率的に設定できると推測します。  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>カスタム依存関係プロパティへの影響  
 プロパティ設定の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロセッサ動作の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]現在の実装ではラッパーが完全にバイパスされるため、カスタム依存関係プロパティのラッパーのセット定義に追加のロジックを追加しないでください。 このようなロジックをセット定義に入れると、コードではなくプロパティが設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されたときにロジックは実行されません。  
  
 同様に、プロセッサの他[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の側面では、ラッパーを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用<xref:System.Windows.DependencyObject.GetValue%2A>するのではなく、処理からプロパティ値を取得します。 したがって、呼び出しを超えて定義に`get`追加の実装<xref:System.Windows.DependencyObject.GetValue%2A>を避ける必要があります。  
  
 次の例は、ラッパーを持つ推奨される依存関係プロパティ定義で、プロパティ識別子が`public``static``readonly`フィールドとして格納され、`get`および`set`の定義には、依存関係プロパティのバッキングを定義する必要なプロパティ システム メソッド以外のコードが含まれていません。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [コレクション型依存関係プロパティ](collection-type-dependency-properties.md)
- [依存関係プロパティのセキュリティ](dependency-property-security.md)
- [DependencyObject の安全なコンストラクター パターン](safe-constructor-patterns-for-dependencyobjects.md)
