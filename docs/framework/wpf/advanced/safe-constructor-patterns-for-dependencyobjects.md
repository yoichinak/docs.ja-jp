---
title: DependencyObject の安全なコンストラクター パターン
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: d963d9c8b7ddfba0c24fcb10ddf9cc45a2f4d0c5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363983"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>DependencyObject の安全なコンストラクター パターン
一般的に、コンストラクターは派生クラスのコンストラクターの基底の初期化として呼び出されることがあるため、クラスのコンストラクターでは、仮想メソッドやデリゲートなどのコールバックを呼び出しません。 対象オブジェクトの初期化が不完全な状態で、仮想メソッドに入ることがあります。 ただし、プロパティ システム自体は、依存関係プロパティ システムの一部としてコールバックを呼び出し、内部的に公開します。 単純な操作で依存関係プロパティの値を設定すると<xref:System.Windows.DependencyObject.SetValue%2A>呼び出し組み込めますコールバックどこかを決定します。 このため、使用する型が基底クラスとして使われる場合に、コンストラクター本体内に依存関係プロパティ値を設定すると問題が発生する可能性があり、注意が必要です。 実装するための特定のパターンがある<xref:System.Windows.DependencyObject>コンス トラクターをここに記載されている依存関係プロパティの状態と固有のコールバックでは、特定の問題を回避できます。  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>プロパティ システムの仮想メソッド  
 計算中には、次の仮想メソッドまたはコールバックは呼び出される可能性のある、<xref:System.Windows.DependencyObject.SetValue%2A>依存関係プロパティの値を設定する呼び出し: <xref:System.Windows.ValidateValueCallback>、 <xref:System.Windows.PropertyChangedCallback>、 <xref:System.Windows.CoerceValueCallback>、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>します。 これらの仮想メソッドまたはコールバックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のプロパティ システムと依存関係プロパティの汎用性を高めるうえで、それぞれ特定の目的を果たします。 これらの仮想メソッドを使用してプロパティ値の決定をカスタマイズする方法の詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop ルールの適用とプロパティ システムの仮想メソッドの比較  
 ビルド プロセスの一部として Microsoft ツールの FXCop を使用している場合、基底コンストラクターを呼び出す特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フレームワーク クラスを派生させるとき、派生クラスで独自の依存関係プロパティを実装するときに、FXCop の特定のルール違反が発生することがあります。 ルール違反に該当する名前文字列は次のとおりです。  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 このルールは、FXCop に設定されている既定のパブリック ルールの一部です。 このルールによって報告されるのは、依存関係プロパティ システムの仮想メソッドを最終的に呼び出す、依存関係プロパティ システム内のトレースです。 このルール違反は、このトピックで説明されている推奨コンストラクター パターンに従っている場合も発生し続ける可能性があるため、FXCop のルール セット構成でこのルールを無効にするか抑制する必要があります。  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>既存のクラスの使用ではなくクラスの派生が大半の原因  
 このルールによって報告される問題は、構築のシーケンスで仮想メソッドを呼び出すように実装したクラスが派生される場合に発生します。 クラスをシールする場合、クラスが派生されないとわかっている場合、クラスが派生されないように強制する場合は、ここで説明する内容や FXCop のルールによって起こる問題は該当しません。 ただし、テンプレートや拡張可能なコントロール ライブラリのセットを作成する場合などのように、基底クラスとしての使用を想定したクラスを作成する場合は、ここで説明されているコンストラクターの推奨パターンに従う必要があります。  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>既定のコンストラクターにおいて、コールバックによって要求されるすべての値の初期化の必要性  
 任意のクラスのオーバーライドまたはコールバック (「プロパティ システムの仮想メソッド」セクションの一覧にあるコールバック) によって使用されるすべてのインスタンス メンバーは、クラスの既定のコンストラクターで初期化する必要があります。これは、既定以外のコンストラクターのパラメーターによって値の一部に "実際の" 値が入る場合も同様です。  
  
 次のコード例 (および以降の例) は、この規則に違反する擬似 C# コードの例であり、問題を説明しています。  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 アプリケーション コードによって `new MyClass(objectvalue)` が呼び出されると、既定のコンストラクターと基底クラスのコンストラクターが呼び出されます。 設定し、 `Property1 = object1`、仮想メソッドを呼び出し`OnPropertyChanged`、所有`MyClass`<xref:System.Windows.DependencyObject>します。  オーバーライドでは、まだ初期化されていない `_myList` が参照されます。  
  
 これらの問題を回避する方法の 1 つは、コールバックが他の依存関係プロパティのみを使用し、それぞれの使用する依存関係プロパティが、登録済みのメタデータの一部として確立された既定値を持つようにすることです。  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>安全なコンストラクター パターン  
 クラスが基底クラスとして使用される場合に、不完全な初期化のリスクを回避するには、次のパターンに従ってください。  
  
#### <a name="default-constructors-calling-base-initialization"></a>基底クラスの初期化を呼び出す既定のコンストラクター  
 基底クラスの既定値を呼び出す次のコンストラクターを実装します。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>基底クラスのシグネチャと一致しない、既定以外の (簡易) コンストラクター  
 これらのコンストラクターがパラメーターを使用して初期化の依存関係プロパティを設定する場合は、最初に初期化のための独自のクラスの既定のコンストラクターを呼び出し、次にパラメーターを使用して依存関係プロパティを設定します。 これらは、クラスによって定義された依存関係プロパティか、基底クラスから継承された依存関係プロパティのいずれかですが、いずれの場合も次のパターンが適用されます。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>基底クラスのシグネチャと一致する、既定以外の (簡易) コンストラクター  
 同じパラメーター化を使用して基底コンストラクターを呼び出す代わりに、独自のクラスの既定のコンストラクターをもう一度呼び出します。 基底初期化子を呼び出さないでください。代わりに `this()` を呼び出す必要があります。 次に、渡されたパラメーターを関連プロパティを設定する値として使用し、元のコンストラクターの動作を複製します。 特定のパラメーターを設定するプロパティを決定する場合は、参考として元の基底コンストラクターのドキュメントを使用します。  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>すべてのシグネチャを一致させることが必要  
 基本データ型に複数のシグネチャがある場合は、追加のプロパティを設定する前に、クラスの既定のコンストラクターを呼び出す推奨パターンを使用する独自のコンストラクター実装で、考えられるすべてのシグネチャを意図的に一致させる必要があります。  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>SetValue による依存関係プロパティの設定  
 ラッパー プロパティの設定の利便性を持たないしの値を設定するプロパティを設定する場合は、これらの同じパターンが適用されます<xref:System.Windows.DependencyObject.SetValue%2A>します。 呼び出しを<xref:System.Windows.DependencyObject.SetValue%2A>パススルーそのコンス トラクターのパラメーターは、初期化のため、クラスの既定のコンス トラクターを呼び出すも必要があります。  
  
## <a name="see-also"></a>関連項目
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [依存関係プロパティのセキュリティ](dependency-property-security.md)
