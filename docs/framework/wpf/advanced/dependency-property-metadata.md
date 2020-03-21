---
title: 依存関係プロパティのメタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 3d84510fce69e81929cbe9b6088e12aaf3409769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186364"
---
# <a name="dependency-property-metadata"></a>依存関係プロパティのメタデータ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]プロパティ システムには、リフレクションまたは一般的な共通言語ランタイム (CLR) の特性を通じてプロパティについて報告できる内容を超えるメタデータ レポート システムが含まれています。 依存関係プロパティのメタデータは、依存関係プロパティを定義するクラスで個別に割り当てることも、依存関係プロパティを別のクラスに追加する際に変更することもできます。また、依存関係プロパティをその定義元の基本クラスから継承するすべての派生クラスで明確にオーバーライドすることもできます。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティのコンシューマーの観点から依存関係プロパティを理解しており、「[依存関係プロパティの概要](dependency-properties-overview.md)」を読んでいることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="dp_metadata_contents"></a>
## <a name="how-dependency-property-metadata-is-used"></a>依存関係プロパティのメタデータの使用方法  
 依存関係プロパティのメタデータは、依存プロパティの特性を照会して調べるためのオブジェクトとして存在します。 また、このメタデータは、特定の依存関係プロパティを処理するために、プロパティ システムによって頻繁にアクセスされます。 依存関係プロパティのメタデータ オブジェクトには、次のような情報が格納されます。  
  
- 依存関係プロパティの既定値 (ローカル値、スタイル、継承などによって依存関係プロパティに対して他の値を決定できない場合)。依存関係プロパティの値を割り当てるときに、プロパティ システムで使用される優先順位に既定値が適用される方法の詳細については、「[依存関係プロパティの値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
- 所有者型に基づく強制型変換または変更通知の動作に影響を与えるコールバック実装への参照。 多くの場合、これらのコールバックは非パブリックなアクセス レベルで定義されます。したがって、参照が、許可されたアクセス スコープ内にない限り、一般にメタデータから実際の参照を取得することはできません。 依存関係プロパティのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。  
  
- 対象の依存関係プロパティが WPF フレームワーク レベルのプロパティと見なされる場合、WPF フレームワーク レベルの依存関係プロパティ特性がメタデータに含まれる可能性があります。これは、WPF フレームワーク レベルのレイアウト エンジンやプロパティ継承ロジックなどのサービスの情報および状態を報告します。 この内容に関する依存関係プロパティのメタデータの詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。  
  
<a name="APIs"></a>
## <a name="metadata-apis"></a>メタデータ API  
 プロパティ システムで使用されるメタデータ情報のほとんどを報告する型は<xref:System.Windows.PropertyMetadata>クラスです。 メタデータ インスタンスは、依存関係プロパティをプロパティ システムに登録する際に必要に応じて指定されます。それ自体を所有者として追加する追加の型、または基本クラスの依存関係プロパティ定義から継承したメタデータをオーバーライドする追加の型に再度指定することもできます。 (プロパティ登録でメタデータが指定されていない場合は、そのクラスの既定値<xref:System.Windows.PropertyMetadata>を使用して既定値が作成されます)。登録されたメタデータは、<xref:System.Windows.PropertyMetadata><xref:System.Windows.DependencyProperty.GetMetadata%2A><xref:System.Windows.DependencyObject>インスタンスの依存関係プロパティからメタデータを取得するさまざまなオーバーロードを呼び出すときに返されます。  
  
 クラス<xref:System.Windows.PropertyMetadata>は、WPF フレームワーク レベルのクラスなどのアーキテクチャ分割に対して、より具体的なメタデータを提供するためにから派生します。 <xref:System.Windows.UIPropertyMetadata>アニメーション レポートを追加<xref:System.Windows.FrameworkPropertyMetadata>し、前のセクションで説明した WPF フレームワーク レベルのプロパティを提供します。 依存関係プロパティを登録すると、これらの<xref:System.Windows.PropertyMetadata>派生クラスに登録できます。 メタデータが検査されると、基本<xref:System.Windows.PropertyMetadata>型を派生クラスにキャストして、より具体的なプロパティを調べることができる可能性があります。  
  
> [!NOTE]
> で指定できるプロパティ特性<xref:System.Windows.FrameworkPropertyMetadata>は、このドキュメントでは「flags」と呼ばれることがあります。 依存関係プロパティの登録またはメタデータのオーバーライドで使用する新しいメタデータ インスタンスを作成する場合は、フラグ列挙体<xref:System.Windows.FrameworkPropertyMetadataOptions>を使用してこれらの値を指定し、列挙体の連結値をコンストラクターに指定する<xref:System.Windows.FrameworkPropertyMetadata>可能性があります。 ただし、いったん構築されると、これらのオプション特性は、列挙値<xref:System.Windows.FrameworkPropertyMetadata>の構築ではなく、一連のブール型プロパティとして公開されます。 これらのブール型プロパティを使用すると、目的の情報を取得するためにフラグ列挙値に対してマスクを適用することなく、各条件をチェックすることができます。 コンストラクターは、コンストラクターシグネチャの長さを<xref:System.Windows.FrameworkPropertyMetadataOptions>妥当な状態に保つために連結を使用しますが、実際に構築されたメタデータは、メタデータのクエリをより直感的にするために個別のプロパティを公開します。  
  
<a name="override_or_subclass"></a>
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>メタデータをオーバーライドする場合、クラスを派生する場合  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、依存関係プロパティを完全に再実装することなく、依存関係プロパティの一部の特性を変更するための機能が用意されています。 これは、特定の型に存在する依存関係プロパティについて、そのプロパティ メタデータの別のインスタンスを構築することで実現されます。 既存の依存関係プロパティの大部分は仮想プロパティではありません。したがって、厳密には、継承クラスでの依存関係プロパティの "再実装" は、既存のメンバーをシャドウすることによってのみ実現されます。  
  
 型の依存関係プロパティに対して有効にしようとしているシナリオが、既存の依存関係プロパティの特性の変更では実現できない場合、派生クラスを作成し、その派生クラスでカスタム依存関係プロパティを宣言することが必要になる場合があります。 カスタム依存関係プロパティは、API によって定義された依存関係プロパティと同じように[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動作します。 カスタム依存関係プロパティの詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
 オーバーライドすることができない依存関係プロパティの代表的な特性の 1 つは、依存関係プロパティの値型です。 目的の動作にほぼ合致する依存関係プロパティを継承していても、その依存関係プロパティに別の型が必要な場合には、カスタム依存関係プロパティを実装し、型変換またはカスタム クラスのその他の実装を通じてプロパティをリンクする必要があります。 また、このコールバックは登録フィールド<xref:System.Windows.ValidateValueCallback>自体に存在し、メタデータ内に存在しないため、既存の を置き換えることはできません。  
  
<a name="scenarios"></a>
## <a name="scenarios-for-changing-existing-metadata"></a>既存のメタデータを変更するシナリオ  
 既存の依存関係プロパティのメタデータを使用している場合、依存関係プロパティのメタデータを変更する一般的なシナリオの 1 つは、既定値を変更することです。 プロパティ システム コールバックの変更または追加は、より高度なシナリオです。 これは、実装している派生クラスの相互関係が依存関係プロパティごとに異なる場合に使用します。 コードと宣言的な使用方法の両方をサポートするプログラミング モデルを使用する条件の 1 つとして、プロパティを任意の順序で設定できる必要があります。 したがって、依存関係プロパティはすべて、コンテキストを使用せずに Just-In-Time で設定する必要があります。また、設定順序 (コンストラクター内の順序など) に依存することもできません。 この内容に関するプロパティ システムの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。 検証コールバックは、メタデータの一部ではなく、依存関係プロパティ識別子の一部であることに注意してください。 したがって、検証コールバックは、メタデータのオーバーライドでは変更できません。  
  
 既存の依存関係プロパティに対して、WPF フレームワーク レベルのプロパティのメタデータ オプションの変更が必要になる場合があります。 これらのオプションは、WPF フレームワーク レベルのプロパティに関する特定の既知の条件を、レイアウト システムなどの他の WPF フレームワーク レベルのプロセスに伝達します。  オプションの設定は、通常、新しい依存関係プロパティを登録する場合にのみ行われますが、または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A><xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出しの一部として WPF フレームワーク レベルのプロパティ メタデータを変更することもできます。 使用する具体的な値および詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。 新しく登録した依存関係プロパティに対してこれらのオプションを設定する方法の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
<a name="dp_override_metadata"></a>
### <a name="overriding-metadata"></a>メタデータのオーバーライド  
 メタデータのオーバーライドの主な目的は、型に存在する依存関係プロパティに適用される、メタデータから派生したさまざまな動作を変更できるようにすることです。 この理由については、「[メタデータ](#dp_metadata_contents)」セクションで詳しく説明します。 コード例を含む詳細については、「[方法 : 依存関係プロパティのメタデータをオーバーライドする](how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
 登録呼び出し ( )<xref:System.Windows.DependencyProperty.Register%2A>の間に、依存関係プロパティにプロパティ メタデータを指定できます。 ただし、多くの場合、その依存関係プロパティを継承するクラスに対して、型固有のメタデータを提供する必要があります。 これは<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>、メソッドを呼び出すことによって行うことができます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API の例として、<xref:System.Windows.FrameworkElement>クラスは、最初に依存関係プロパティを登録する<xref:System.Windows.UIElement.Focusable%2A>型です。 ただし、<xref:System.Windows.Controls.Control>このクラスは依存関係プロパティのメタデータをオーバーライドして、独自の初期既定値`false`を提供し、それを`true`から に変更し、それ以外<xref:System.Windows.UIElement.Focusable%2A>の場合は元の実装を再利用します。  
  
 メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>がマージされます。 新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>しい を追加すると、そのコールバックはメタデータに格納されます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、 の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>値は、メタデータで指定した最も近い先祖からの参照として昇格されます。  
  
- 実際の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>プロパティ システムの動作では、階層内のすべてのメタデータ所有者の実装が保持され、テーブルに追加され、プロパティ システムによって実行される順序は、最派生クラスのコールバックが最初に呼び出されるということです。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>が置き換えられます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.DefaultValue%2A>指定しない場合、値<xref:System.Windows.PropertyMetadata.DefaultValue%2A>はメタデータで指定された最も近い先祖から取得されます。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>実装は置き換えられます。 新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>しい を追加すると、そのコールバックはメタデータに格納されます。 オーバーライドで を<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>指定しない場合、 の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>値は、メタデータで指定した最も近い先祖からの参照として昇格されます。  
  
- プロパティ システムの動作では、直接<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>メタデータ内の の のみが呼び出されます。 階層内の他<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>の実装への参照は保持されません。  
  
 この動作は によって<xref:System.Windows.PropertyMetadata.Merge%2A>実装され、派生メタデータ クラスでオーバーライドできます。  
  
#### <a name="overriding-attached-property-metadata"></a>添付プロパティのメタデータのオーバーライド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、添付プロパティは依存関係プロパティとして実装されます。 このことは、添付プロパティもプロパティ メタデータを持ち、これを個々のクラスでオーバーライドできることを意味します。 添付プロパティのスコープに関する考慮事項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、一般に、<xref:System.Windows.DependencyObject>任意のプロパティに添付プロパティを設定できることです。 したがって、派生<xref:System.Windows.DependencyObject>クラスは、クラスのインスタンスに設定される可能性があるため、任意の添付プロパティのメタデータをオーバーライドできます。 オーバーライドできるのは、既定値、コールバック、または WPF フレームワーク レベルの特性報告プロパティです。 添付プロパティがクラスのインスタンスで設定されている場合、そのオーバーライド プロパティ メタデータ特性が適用されます。 たとえば、プロパティが他では特に指定されていないときには、オーバーライド値がクラスのインスタンス上の添付プロパティの値として報告されるように、既定値をオーバーライドできます。  
  
> [!NOTE]
> プロパティ<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>は添付プロパティには関係ありません。  
  
<a name="dp_add_owner"></a>
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>既存の依存関係プロパティの所有者としてのクラスの追加  
 クラスは、メソッドを使用して、既に登録されている依存関係プロパティの所有者として自分自身を<xref:System.Windows.DependencyProperty.AddOwner%2A>追加できます。 これにより、当初は別の型に対して登録された依存関係プロパティをクラスで使用できるようになります。 通常、追加するクラスは、所有者としてその依存関係プロパティを最初に登録した型の派生クラスではありません。 これにより、元の所有者クラスと追加するクラスが同一のクラス階層内にない場合でも、クラスとその派生クラスで依存関係プロパティの実装を "継承" することが事実上可能になります。 また、追加するクラスとすべての派生クラスでは、型固有のメタデータを元の依存関係プロパティに提供することができます。  
  
 追加するクラスは、プロパティ システムのユーティリティ メソッドを介してそれ自体を所有者として追加するだけでなく、追加のパブリック メンバーをそれ自体で宣言する必要があります。これは、依存関係プロパティを完全な形でプロパティ システムに登録し、コードとマークアップの両方に対して公開するためです。 既存の依存関係プロパティを追加するクラスは、その依存関係プロパティのオブジェクト モデルを公開する限り、新しいカスタム依存関係プロパティを定義するクラスと同様の役割を負います。 これらのメンバーの中で最初に公開するのは、依存関係プロパティの識別子フィールドです。 このフィールドは、呼`public static readonly`び出し<xref:System.Windows.DependencyProperty>の戻り値に割り当てられる<xref:System.Windows.DependencyProperty.AddOwner%2A>type のフィールドである必要があります。 定義する 2 番目のメンバーは、共通言語ランタイム (CLR) "ラッパー" プロパティです。 ラッパーを使用すると、コード内で依存関係プロパティを操作する方がはるかに便利になります (<xref:System.Windows.DependencyObject.SetValue%2A>毎回呼び出しを避けることができ、ラッパー自体で 1 回だけ呼び出しを行うことができます)。 このラッパーの実装方法は、カスタム依存関係プロパティを登録する場合の実装方法とまったく同じです。 依存関係プロパティの実装の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「[依存関係プロパティの所有者の種類を追加する](how-to-add-an-owner-type-for-a-dependency-property.md)」を参照してください。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner および添付プロパティ  
 所有者クラスによって<xref:System.Windows.DependencyProperty.AddOwner%2A>添付プロパティとして定義されている依存関係プロパティを呼び出すことができます。 通常、これは、以前の添付プロパティを非添付の依存関係プロパティとして公開する目的で行います。 次に、<xref:System.Windows.DependencyProperty.AddOwner%2A>依存関係プロパティ識別子として使用する`public static readonly`フィールドとして戻り値を公開し、プロパティがメンバー テーブルに表示され、クラスで添付されていないプロパティの使用法をサポートするように、適切な "ラッパー" プロパティを定義します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [フレームワーク プロパティ メタデータ](framework-property-metadata.md)
