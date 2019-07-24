---
title: 依存関係プロパティのメタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 800bf80e5ba3e697c122bcf4b1bc0f302357d087
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401618"
---
# <a name="dependency-property-metadata"></a>依存関係プロパティのメタデータ
プロパティ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]システムには、リフレクションまたは一般的な共通言語ランタイム (CLR) の特性によってプロパティについて報告できる値を超えるメタデータレポートシステムが含まれています。 依存関係プロパティのメタデータは、依存関係プロパティを定義するクラスで個別に割り当てることも、依存関係プロパティを別のクラスに追加する際に変更することもできます。また、依存関係プロパティをその定義元の基本クラスから継承するすべての派生クラスで明確にオーバーライドすることもできます。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>前提条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」トピックを通読していることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>依存関係プロパティのメタデータの使用方法  
 依存関係プロパティのメタデータは、依存プロパティの特性を照会して調べるためのオブジェクトとして存在します。 また、このメタデータは、特定の依存関係プロパティを処理するために、プロパティ システムによって頻繁にアクセスされます。 依存関係プロパティのメタデータ オブジェクトには、次のような情報が格納されます。  
  
- 依存関係プロパティの既定値 (ローカル値、スタイル、継承などによってその他の依存関係プロパティ値が指定されない場合)。依存関係プロパティの値を割り当てる際の、既定値と、プロパティ システムで使用される優先順位の関係に関する詳細な説明については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
- 所有者型に基づく強制型変換または変更通知の動作に影響を与えるコールバック実装への参照。 多くの場合、これらのコールバックは非パブリックなアクセス レベルで定義されます。したがって、参照が、許可されたアクセス スコープ内にない限り、一般にメタデータから実際の参照を取得することはできません。 依存関係プロパティのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。  
  
- 対象の依存関係プロパティが WPF フレームワーク レベルのプロパティと見なされる場合、WPF フレームワーク レベルの依存関係プロパティ特性がメタデータに含まれる可能性があります。これは、WPF フレームワーク レベルのレイアウト エンジンやプロパティ継承ロジックなどのサービスの情報および状態を報告します。 この内容に関する依存関係プロパティのメタデータの詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>メタデータ API  
 プロパティシステムによって使用されるほとんどのメタデータ情報を報告する<xref:System.Windows.PropertyMetadata>型は、クラスです。 メタデータ インスタンスは、依存関係プロパティをプロパティ システムに登録する際に必要に応じて指定されます。それ自体を所有者として追加する追加の型、または基本クラスの依存関係プロパティ定義から継承したメタデータをオーバーライドする追加の型に再度指定することもできます。 (プロパティの登録でメタデータが指定されていない<xref:System.Windows.PropertyMetadata>場合は、そのクラスの既定値を使用して既定値が作成されます)。登録されたメタデータ<xref:System.Windows.PropertyMetadata>は、 <xref:System.Windows.DependencyObject>インスタンスの依存<xref:System.Windows.DependencyProperty.GetMetadata%2A>関係プロパティからメタデータを取得するさまざまなオーバーロードを呼び出すと、として返されます。  
  
 次<xref:System.Windows.PropertyMetadata>に、クラスをから派生させることにより、WPF フレームワークレベルのクラスなどのアーキテクチャの区分に対して、より具体的なメタデータを提供します。 <xref:System.Windows.UIPropertyMetadata>アニメーションレポートを追加し<xref:System.Windows.FrameworkPropertyMetadata> 、前のセクションで説明した WPF フレームワークレベルのプロパティを提供します。 依存関係プロパティが登録されると、これら<xref:System.Windows.PropertyMetadata>の派生クラスに登録できます。 メタデータが検査されると、 <xref:System.Windows.PropertyMetadata>基本型を派生クラスにキャストして、より具体的なプロパティを調べることができる可能性があります。  
  
> [!NOTE]
>  で<xref:System.Windows.FrameworkPropertyMetadata>指定できるプロパティ特性は、このドキュメントでは "flags" と呼ばれることもあります。 依存関係プロパティの登録またはメタデータのオーバーライドで使用する新しいメタデータインスタンスを作成する場合は、 <xref:System.Windows.FrameworkPropertyMetadataOptions>フラグ列挙体を使用してこれらの値を指定します。その後、列挙体の値を連結します。<xref:System.Windows.FrameworkPropertyMetadata>コンストラクター。 ただし、構築されると、これらのオプション特性は<xref:System.Windows.FrameworkPropertyMetadata> 、の構築列挙値ではなく一連のブール型プロパティとして内に公開されます。 これらのブール型プロパティを使用すると、目的の情報を取得するためにフラグ列挙値に対してマスクを適用することなく、各条件をチェックすることができます。 コンストラクターは、コンストラクターシグネチャ<xref:System.Windows.FrameworkPropertyMetadataOptions>の長さを適切に保つために、連結されたを使用します。一方、実際に構築されたメタデータは、メタデータのクエリをより直観的に行うために個別のプロパティを公開します。  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>メタデータをオーバーライドする場合、クラスを派生する場合  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、依存関係プロパティを完全に再実装することなく、依存関係プロパティの一部の特性を変更するための機能が用意されています。 これは、特定の型に存在する依存関係プロパティについて、そのプロパティ メタデータの別のインスタンスを構築することで実現されます。 既存の依存関係プロパティの大部分は仮想プロパティではありません。したがって、厳密には、継承クラスでの依存関係プロパティの "再実装" は、既存のメンバーをシャドウすることによってのみ実現されます。  
  
 型の依存関係プロパティに対して有効にしようとしているシナリオが、既存の依存関係プロパティの特性の変更では実現できない場合、派生クラスを作成し、その派生クラスでカスタム依存関係プロパティを宣言することが必要になる場合があります。 カスタム依存関係プロパティは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api によって定義された依存関係プロパティと同じように動作します。 カスタム依存関係プロパティの詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
 オーバーライドすることができない依存関係プロパティの代表的な特性の 1 つは、依存関係プロパティの値型です。 目的の動作にほぼ合致する依存関係プロパティを継承していても、その依存関係プロパティに別の型が必要な場合には、カスタム依存関係プロパティを実装し、型変換またはカスタム クラスのその他の実装を通じてプロパティをリンクする必要があります。 また、このコールバックは、 <xref:System.Windows.ValidateValueCallback>メタデータ内ではなく登録フィールド自体に存在するため、既存のを置き換えることはできません。  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>既存のメタデータを変更するシナリオ  
 既存の依存関係プロパティのメタデータを使用している場合、依存関係プロパティのメタデータを変更する一般的なシナリオの 1 つは、既定値を変更することです。 プロパティ システム コールバックの変更または追加は、より高度なシナリオです。 これは、実装している派生クラスの相互関係が依存関係プロパティごとに異なる場合に使用します。 コードと宣言的な使用方法の両方をサポートするプログラミング モデルを使用する条件の 1 つとして、プロパティを任意の順序で設定できる必要があります。 したがって、依存関係プロパティはすべて、コンテキストを使用せずに Just-In-Time で設定する必要があります。また、設定順序 (コンストラクター内の順序など) に依存することもできません。 この内容に関するプロパティ システムの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。 検証コールバックは、メタデータの一部ではなく、依存関係プロパティ識別子の一部であることに注意してください。 したがって、検証コールバックは、メタデータのオーバーライドでは変更できません。  
  
 既存の依存関係プロパティに対して、WPF フレームワーク レベルのプロパティのメタデータ オプションの変更が必要になる場合があります。 これらのオプションは、WPF フレームワーク レベルのプロパティに関する特定の既知の条件を、レイアウト システムなどの他の WPF フレームワーク レベルのプロセスに伝達します。  オプションの設定は、通常、新しい依存関係プロパティを登録するときにのみ実行されますが、 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>または<xref:System.Windows.DependencyProperty.AddOwner%2A>の呼び出しの一部として、WPF フレームワークレベルのプロパティのメタデータを変更することもできます。 使用する具体的な値および詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。 新しく登録した依存関係プロパティに対してこれらのオプションを設定する方法の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>メタデータのオーバーライド  
 メタデータのオーバーライドの主な目的は、型に存在する依存関係プロパティに適用される、メタデータから派生したさまざまな動作を変更できるようにすることです。 この理由については、「[メタデータ](#dp_metadata_contents)」セクションで詳しく説明します。 コード例を含む詳細については、「[方法 : 依存関係プロパティのメタデータをオーバーライドする](how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
 登録呼び出し中に依存関係プロパティのプロパティメタデータを指定でき<xref:System.Windows.DependencyProperty.Register%2A>ます ()。 ただし、多くの場合、その依存関係プロパティを継承するクラスに対して、型固有のメタデータを提供する必要があります。 これは、 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドを呼び出すことによって行うことができます。  Api [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の例<xref:System.Windows.UIElement.Focusable%2A>として、クラスは、最初に依存関係プロパティを登録する型です。<xref:System.Windows.FrameworkElement> ただし、 <xref:System.Windows.Controls.Control>クラスは、依存関係プロパティのメタデータをオーバーライドして、独自の初期既定`false`値を提供し、それをからに<xref:System.Windows.UIElement.Focusable%2A> `true`変更します。それ以外の場合は、元の実装を再利用します。  
  
 メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>マージされます。 新しい<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>を追加すると、そのコールバックがメタデータに格納されます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>値はメタデータで指定された最も近い先祖から参照として昇格されます。  
  
- の<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>実際のプロパティシステムの動作では、階層内のすべてのメタデータ所有者の実装が保持され、テーブルに追加されます。プロパティシステムによって実行される順序により、最も多くの派生クラスのコールバックが最初に呼び出されることになります。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>が置き換えられます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.DefaultValue%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.DefaultValue%2A>値は、メタデータで指定された最も近い先祖から取得されます。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>実装は置き換えられます。 新しい<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>を追加すると、そのコールバックがメタデータに格納されます。 オーバーライドでを<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>指定しない場合、の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>値はメタデータで指定された最も近い先祖から参照として昇格されます。  
  
- プロパティシステムの動作は、直接の<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>メタデータ内ののみが呼び出されることを示します。 階層内の他<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>の実装への参照は保持されません。  
  
 この動作はによっ<xref:System.Windows.PropertyMetadata.Merge%2A>て実装され、派生メタデータクラスでオーバーライドできます。  
  
#### <a name="overriding-attached-property-metadata"></a>添付プロパティのメタデータのオーバーライド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、添付プロパティは依存関係プロパティとして実装されます。 このことは、添付プロパティもプロパティ メタデータを持ち、これを個々のクラスでオーバーライドできることを意味します。 の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]添付プロパティのスコープに関する考慮事項は、通常<xref:System.Windows.DependencyObject> 、添付プロパティが設定されている場合があります。 したがって、 <xref:System.Windows.DependencyObject>クラスのインスタンスに設定されている可能性があるため、任意の派生クラスで、添付プロパティのメタデータをオーバーライドできます。 オーバーライドできるのは、既定値、コールバック、または WPF フレームワーク レベルの特性報告プロパティです。 添付プロパティがクラスのインスタンスで設定されている場合、そのオーバーライド プロパティ メタデータ特性が適用されます。 たとえば、プロパティが他では特に指定されていないときには、オーバーライド値がクラスのインスタンス上の添付プロパティの値として報告されるように、既定値をオーバーライドできます。  
  
> [!NOTE]
>  プロパティ<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>は、添付プロパティには関係ありません。  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>既存の依存関係プロパティの所有者としてのクラスの追加  
 クラスは、 <xref:System.Windows.DependencyProperty.AddOwner%2A>メソッドを使用して、既に登録されている依存関係プロパティの所有者として自身を追加できます。 これにより、当初は別の型に対して登録された依存関係プロパティをクラスで使用できるようになります。 通常、追加するクラスは、所有者としてその依存関係プロパティを最初に登録した型の派生クラスではありません。 これにより、元の所有者クラスと追加するクラスが同一のクラス階層内にない場合でも、クラスとその派生クラスで依存関係プロパティの実装を "継承" することが事実上可能になります。 また、追加するクラスとすべての派生クラスでは、型固有のメタデータを元の依存関係プロパティに提供することができます。  
  
 追加するクラスは、プロパティ システムのユーティリティ メソッドを介してそれ自体を所有者として追加するだけでなく、追加のパブリック メンバーをそれ自体で宣言する必要があります。これは、依存関係プロパティを完全な形でプロパティ システムに登録し、コードとマークアップの両方に対して公開するためです。 既存の依存関係プロパティを追加するクラスは、その依存関係プロパティのオブジェクト モデルを公開する限り、新しいカスタム依存関係プロパティを定義するクラスと同様の役割を負います。 これらのメンバーの中で最初に公開するのは、依存関係プロパティの識別子フィールドです。 このフィールドは、 `public static readonly` <xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出しの戻り値<xref:System.Windows.DependencyProperty>に割り当てられる型のフィールドである必要があります。 定義する2番目のメンバーは、共通言語ランタイム (CLR) "ラッパー" プロパティです。 ラッパーを使用すると、コードで依存関係プロパティを操作することがはるかに簡単<xref:System.Windows.DependencyObject.SetValue%2A>になります (毎回の呼び出しを回避し、ラッパー自体で1回だけ呼び出しを行うことができます)。 このラッパーの実装方法は、カスタム依存関係プロパティを登録する場合の実装方法とまったく同じです。 依存関係プロパティの実装の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「[依存関係プロパティの所有者の種類を追加する](how-to-add-an-owner-type-for-a-dependency-property.md)」を参照してください。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner および添付プロパティ  
 Owner クラスに<xref:System.Windows.DependencyProperty.AddOwner%2A>よって添付プロパティとして定義されている依存関係プロパティに対してを呼び出すことができます。 通常、これは、以前の添付プロパティを非添付の依存関係プロパティとして公開する目的で行います。 次に、依存関係<xref:System.Windows.DependencyProperty.AddOwner%2A>プロパティの識別子と`public static readonly`して使用するフィールドとして戻り値を公開し、適切な "ラッパー" プロパティを定義します。これにより、プロパティが members テーブルに表示され、添付されていないプロパティがサポートされるようになります。クラスの使用方法。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [フレームワーク プロパティ メタデータ](framework-property-metadata.md)
