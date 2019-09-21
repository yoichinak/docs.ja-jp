---
title: 依存関係プロパティのコールバックと検証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
ms.openlocfilehash: 7f00961ba100700c68936cc33facfdc758c77d3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940821"
---
# <a name="dependency-property-callbacks-and-validation"></a>依存関係プロパティのコールバックと検証
このトピックでは、検証による判定、プロパティの有効値が変更されたときに呼び出されるコールバック、値の決定への外部的影響のオーバーライドなど、プロパティ関連機能の代替カスタム実装を使用して依存関係プロパティを作成する方法について説明します。 また、これらの手法を用いてプロパティ システムの既定の動作を拡張することが適切であるシナリオについても説明します。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、依存関係プロパティの実装の基本シナリオとカスタム依存関係プロパティへのメタデータの適用方法を理解していることを前提とします。 詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>検証コールバック  
 検証コールバックは、最初の登録時に依存関係プロパティに割り当てることができます。 検証コールバックは、プロパティメタデータの一部ではありません。これは、 <xref:System.Windows.DependencyProperty.Register%2A>メソッドを直接入力したものです。 したがって、依存関係プロパティの検証コールバックを作成した後で、その検証コールバックを新しい実装でオーバーライドすることはできません。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 検証コールバックは、オブジェクト値を受け取るように実装されます。 指定された値がプロパティに対して有効である場合は `true` を、有効でない場合は `false`を返します。 プロパティの型はプロパティ システムに登録済みの適切な型であると想定されます。したがって、通常の場合、コールバック内での型チェックは行われません。 検証コールバックは、プロパティ システムが実行するさまざまな操作で使用されます。 これには、既定値による初期型の初期化、呼び出し<xref:System.Windows.DependencyObject.SetValue%2A>によるプログラムによる変更、または指定された新しい既定値を使用したメタデータのオーバーライドが含まれます。 これらの操作で呼び出された検証コールバックが `false` を返す場合、例外が発生します。 アプリケーションの作成者はこれらの例外を処理する必要があります。 検証コールバックは、列挙値の検証や、プロパティの測定値がゼロ以上に設定されている場合に integer 型または double 型の値を制限するときによく使用されます。  
  
 検証コールバックは、インスタンスではなくクラスを検証するためのものです。 コールバックのパラメーターは、検証するプロパティが<xref:System.Windows.DependencyObject>設定されている特定のとは通信しません。 したがって、検証コールバックを使用して、プロパティ値に影響を及ぼす可能性がある "依存関係" (インスタンス固有のプロパティ値が他のインスタンス固有のプロパティ値や実行時の状態などの要因に依存する関係) を強制することはできません。  
  
 非常に単純な検証コールバックシナリオのコード例を次に示します。 <xref:System.Double>プリミティブとして型指定されたプロパティがまたは<xref:System.Double.NegativeInfinity>ではない<xref:System.Double.PositiveInfinity>ことを検証しています。  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>強制値コールバックとプロパティ変更イベント  
 強制値コールバックは、依存<xref:System.Windows.DependencyObject>関係プロパティの値が変更<xref:System.Windows.PropertyChangedCallback>されるたびにプロパティシステムによって呼び出される実装と同様に、プロパティの特定のインスタンスを渡します。 これら 2 つのコールバックを組み合わせて使用すると、あるプロパティが変更されたときに他のプロパティに自動的に強制または再評価が適用される一連のプロパティを要素に作成することができます。  
  
 依存関係プロパティ間の関連は、最小値、最大値、および実際の値 (または現在の値) を表す 3 つ目のプロパティが要素に含まれる場合において、ユーザー インターフェイスによって駆動されるプロパティがあるときによく使用されます。 ここで、最大値が現在の値より小さい値に調整された場合、現在の値を新しい最大値以下の値に強制する必要があります。現在の値と最小値についても同様の関係が成り立ちます。  
  
 次の、3 つの依存関係プロパティの 1 つを示す非常に簡単なコード例は、こうした関係を表しています。 この例は、関連する *Reading プロパティ (Min、Max、Current) のうちの 1 つである `CurrentReading` プロパティの登録方法を示しています。 ここでは、前のセクションで説明した検証を使用しています。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Current のプロパティ変更コールバックを使用して、他の依存関係プロパティに対して登録されている強制値コールバックを明示的に呼び出すことにより、変更を他のプロパティに伝播します。  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 強制値コールバックは、Current プロパティが依存している可能性があるプロパティの値を検証し、必要に応じて現在の値を強制的に指定します。  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> プロパティの既定値は強制的に指定されません。 既定値に等しいプロパティ値は、プロパティ値が既定値のままである場合、またはその他の値を<xref:System.Windows.DependencyObject.ClearValue%2A>でクリアした場合に発生する可能性があります。  
  
 強制値コールバックとプロパティ変更コールバックはプロパティ メタデータの一部です。 したがって、特定の依存関係プロパティを所有する型から派生させた型に存在するその特定の依存関係プロパティのコールバックは、派生させた型でプロパティのメタデータをオーバーライドすることで変更できます。  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>高度な強制とコールバック シナリオ  
  
### <a name="constraints-and-desired-values"></a>制約と目的の値  
 コール<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>バックは、宣言したロジックに従って値を強制するために、プロパティシステムによって使用されますが、ローカルに設定されたプロパティの強制値は、内部的に "必要な値" を保持します。 制約がアプリケーションの有効期間内に動的に変更される可能性があるプロパティ値に基づいている場合、強制の制約も動的に変更されます。そして、制約されているプロパティは、指定された新しい制約の下で、その値を目的の値にできる限り近づけることができます。 制約がすべて解除された場合、値は目的の値になります。 相互に循環的に依存する複数のプロパティを使用している場合、非常に複雑な依存関係シナリオを導入することができます。 たとえば、Min、Max、Current のシナリオでは、Minimum と Maximum をユーザー設定可能なプロパティにすることができます。 その場合、Maximum が常に Minimum より大きくなり、Minimum が常に Maximum より小さくなるように強制する必要があります。 ただし、この強制を有効にし、Maximum が Minimum に強制された場合、Current が未設定の状態になります。なぜなら、Currenct は Maximum と Minimum の両方に依存し、両者の値の間の範囲内 (この場合はゼロ) に制約されるからです。 その後、Maximum または Minimum が調整された場合、Current はいずれかの値を "追跡" すると考えられます。なぜなら、Current の目的の値が依然として保持されており、制約が緩和されると Current が目的の値に到達しようとするからです。  
  
 依存関係が複雑でも技術的には問題はありません。ただし、多数の再評価が必要になる場合、パフォーマンスが若干低下することがあります。また、UI に直接影響する場合は、ユーザーの混乱につながることもあります。 プロパティ変更コールバックおよび強制値コールバックについては注意が必要です。試行中の強制ができる限り明確に処理されること、およびその制約が "過剰制約" ではないことを確認してください。  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>CoerceValue を使用した値変更の取り消し  
 プロパティシステムは、値<xref:System.Windows.CoerceValueCallback> <xref:System.Windows.DependencyProperty.UnsetValue>を返す任意のを特殊なケースとして扱います。 この特別なケースは、呼び出されるが<xref:System.Windows.CoerceValueCallback>呼び出されたプロパティの変更がプロパティシステムによって拒否され、プロパティシステムがそのプロパティに保持されていた以前の値を報告する必要があることを意味します。 このメカニズムは、非同期に開始されたプロパティの変更が現在のオブジェクトの状態に対して依然として有効であるかどうかをチェックし、有効でない場合はその変更を抑制する場合に役立ちます。 考えられるもう 1 つのシナリオとして、プロパティ値の決定におけるどの構成要素が報告されるプロパティ値を決定するかに応じて値を選択的に抑制することもできます。 これを行うには、コールバック<xref:System.Windows.DependencyProperty>で渡されたとプロパティ識別子をの<xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>入力として使用し、 <xref:System.Windows.ValueSource>を処理します。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [依存関係プロパティのメタデータ](dependency-property-metadata.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
