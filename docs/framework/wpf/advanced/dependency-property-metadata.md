---
title: 依存関係プロパティのメタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: a4b2edce76bc5ab97e644ec8dbdf045931e87786
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663430"
---
# <a name="dependency-property-metadata"></a>依存関係プロパティのメタデータ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムには、リフレクションや一般的な [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 特性から得られる以上の詳細なプロパティ情報を提供するメタデータ報告システムがあります。 依存関係プロパティのメタデータは、依存関係プロパティを定義するクラスで個別に割り当てることも、依存関係プロパティを別のクラスに追加する際に変更することもできます。また、依存関係プロパティをその定義元の基本クラスから継承するすべての派生クラスで明確にオーバーライドすることもできます。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](dependency-properties-overview.md)」トピックを通読していることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>依存関係プロパティのメタデータの使用方法  
 依存関係プロパティのメタデータは、依存プロパティの特性を照会して調べるためのオブジェクトとして存在します。 また、このメタデータは、特定の依存関係プロパティを処理するために、プロパティ システムによって頻繁にアクセスされます。 依存関係プロパティのメタデータ オブジェクトには、次のような情報が格納されます。  
  
- 依存関係プロパティの既定値 (ローカル値、スタイル、継承などによってその他の依存関係プロパティ値が指定されない場合)。依存関係プロパティの値を割り当てる際の、既定値と、プロパティ システムで使用される優先順位の関係に関する詳細な説明については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
- 所有者型に基づく強制型変換または変更通知の動作に影響を与えるコールバック実装への参照。 多くの場合、これらのコールバックは非パブリックなアクセス レベルで定義されます。したがって、参照が、許可されたアクセス スコープ内にない限り、一般にメタデータから実際の参照を取得することはできません。 依存関係プロパティのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。  
  
- 対象の依存関係プロパティが WPF フレームワーク レベルのプロパティと見なされる場合、WPF フレームワーク レベルの依存関係プロパティ特性がメタデータに含まれる可能性があります。これは、WPF フレームワーク レベルのレイアウト エンジンやプロパティ継承ロジックなどのサービスの情報および状態を報告します。 この内容に関する依存関係プロパティのメタデータの詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>メタデータ API  
 ほとんどのプロパティ システムによって使用されるメタデータ情報を報告する型が、<xref:System.Windows.PropertyMetadata>クラス。 メタデータ インスタンスは、依存関係プロパティをプロパティ システムに登録する際に必要に応じて指定されます。それ自体を所有者として追加する追加の型、または基本クラスの依存関係プロパティ定義から継承したメタデータをオーバーライドする追加の型に再度指定することもできます。 (プロパティの登録がメタデータを既定値を指定しない場合の<xref:System.Windows.PropertyMetadata>そのクラスの既定の値が作成されます)。として登録されているメタデータが返される<xref:System.Windows.PropertyMetadata>を呼び出すと、さまざまな<xref:System.Windows.DependencyProperty.GetMetadata%2A>で依存関係プロパティからメタデータを取得するオーバー ロードを<xref:System.Windows.DependencyObject>インスタンス。  
  
 <xref:System.Windows.PropertyMetadata>は後から派生したクラス、WPF フレームワーク レベル クラスなどのアーキテクチャ区分をより詳細なメタデータを提供します。 <xref:System.Windows.UIPropertyMetadata> アニメーションが報告を追加および<xref:System.Windows.FrameworkPropertyMetadata>前のセクションで説明した WPF フレームワーク レベル プロパティを提供します。 依存関係プロパティが登録されると、これらを登録できます<xref:System.Windows.PropertyMetadata>クラスを派生します。 メタデータを検査する場合、ベース<xref:System.Windows.PropertyMetadata>より特定のプロパティを確認するように、型を派生クラスにキャスト可能性があることができます。  
  
> [!NOTE]
>  指定できるプロパティ特性<xref:System.Windows.FrameworkPropertyMetadata>「フラグ」には、このドキュメントでを呼ぶこともあります。 フラグ列挙を使用してこれらの値を指定する依存関係プロパティの登録で使用するための新しいメタデータ インスタンスに作成するか、またはメタデータのオーバーライド、 <xref:System.Windows.FrameworkPropertyMetadataOptions> 列挙体の値が連結された可能性がありますに提供し、<xref:System.Windows.FrameworkPropertyMetadata>コンス トラクター。 ただし、構築されると、これらのオプション特性が内で公開された、<xref:System.Windows.FrameworkPropertyMetadata>一連の構築の列挙値ではなく、ブール型プロパティ。 これらのブール型プロパティを使用すると、目的の情報を取得するためにフラグ列挙値に対してマスクを適用することなく、各条件をチェックすることができます。 コンス トラクターを使用して連結された<xref:System.Windows.FrameworkPropertyMetadataOptions>コンス トラクター シグネチャの長さを実際に構築されたメタデータより直感的なメタデータをクエリするために個別のプロパティを公開します。 一方、妥当な保持するためにします。  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>メタデータをオーバーライドする場合、クラスを派生する場合  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、依存関係プロパティを完全に再実装することなく、依存関係プロパティの一部の特性を変更するための機能が用意されています。 これは、特定の型に存在する依存関係プロパティについて、そのプロパティ メタデータの別のインスタンスを構築することで実現されます。 既存の依存関係プロパティの大部分は仮想プロパティではありません。したがって、厳密には、継承クラスでの依存関係プロパティの "再実装" は、既存のメンバーをシャドウすることによってのみ実現されます。  
  
 型の依存関係プロパティに対して有効にしようとしているシナリオが、既存の依存関係プロパティの特性の変更では実現できない場合、派生クラスを作成し、その派生クラスでカスタム依存関係プロパティを宣言することが必要になる場合があります。 カスタム依存関係プロパティは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で定義されている依存関係プロパティとまったく同じように動作します。 カスタム依存関係プロパティの詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
 オーバーライドすることができない依存関係プロパティの代表的な特性の 1 つは、依存関係プロパティの値型です。 目的の動作にほぼ合致する依存関係プロパティを継承していても、その依存関係プロパティに別の型が必要な場合には、カスタム依存関係プロパティを実装し、型変換またはカスタム クラスのその他の実装を通じてプロパティをリンクする必要があります。 また、置き換えることはできません、既存<xref:System.Windows.ValidateValueCallback>で、登録フィールド自体とそのメタデータ内ではなく、このコールバックが存在するため、します。  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>既存のメタデータを変更するシナリオ  
 既存の依存関係プロパティのメタデータを使用している場合、依存関係プロパティのメタデータを変更する一般的なシナリオの 1 つは、既定値を変更することです。 プロパティ システム コールバックの変更または追加は、より高度なシナリオです。 これは、実装している派生クラスの相互関係が依存関係プロパティごとに異なる場合に使用します。 コードと宣言的な使用方法の両方をサポートするプログラミング モデルを使用する条件の 1 つとして、プロパティを任意の順序で設定できる必要があります。 したがって、依存関係プロパティはすべて、コンテキストを使用せずに Just-In-Time で設定する必要があります。また、設定順序 (コンストラクター内の順序など) に依存することもできません。 この内容に関するプロパティ システムの詳細については、「[依存関係プロパティのコールバックと検証](dependency-property-callbacks-and-validation.md)」を参照してください。 検証コールバックは、メタデータの一部ではなく、依存関係プロパティ識別子の一部であることに注意してください。 したがって、検証コールバックは、メタデータのオーバーライドでは変更できません。  
  
 既存の依存関係プロパティに対して、WPF フレームワーク レベルのプロパティのメタデータ オプションの変更が必要になる場合があります。 これらのオプションは、WPF フレームワーク レベルのプロパティに関する特定の既知の条件を、レイアウト システムなどの他の WPF フレームワーク レベルのプロセスに伝達します。  新しい依存関係プロパティを登録する場合にのみ一般に行ってはオプションの設定がの一部として WPF フレームワーク レベル プロパティのメタデータを変更することも、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>または<xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出します。 使用する具体的な値および詳細については、「[フレームワーク プロパティ メタデータ](framework-property-metadata.md)」を参照してください。 新しく登録した依存関係プロパティに対してこれらのオプションを設定する方法の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>メタデータのオーバーライド  
 メタデータのオーバーライドの主な目的は、型に存在する依存関係プロパティに適用される、メタデータから派生したさまざまな動作を変更できるようにすることです。 この理由については、「[メタデータ](#dp_metadata_contents)」セクションで詳しく説明します。 コード例を含む詳細については、「[方法 : 依存関係プロパティのメタデータをオーバーライドする](how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
 登録の呼び出し中に依存関係プロパティのプロパティのメタデータを指定することができます (<xref:System.Windows.DependencyProperty.Register%2A>)。 ただし、多くの場合、その依存関係プロパティを継承するクラスに対して、型固有のメタデータを提供する必要があります。 呼び出すことによってこれを行う、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッド。  例については、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]、<xref:System.Windows.FrameworkElement>クラスは、最初に登録する型、<xref:System.Windows.UIElement.Focusable%2A>依存関係プロパティ。 <xref:System.Windows.Controls.Control>クラスからの変更、独自の既定の初期値を提供する依存関係プロパティのメタデータをオーバーライドする`false`に`true`、それ以外の場合、元に再使用と<xref:System.Windows.UIElement.Focusable%2A>実装します。  
  
 メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 結合されます。 新しく追加した場合<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>はメタデータでそれを指定した最も近い先祖からの参照として昇格します。  
  
- 実際のプロパティ システム動作<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>は、階層内のすべてのメタデータ所有者用の実装が保持され、最派生クラスのコールバックが最初に呼び出されますが、プロパティ システムによる実行の順序で、テーブルに追加します。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> 置き換えられます。 指定しない場合、<xref:System.Windows.PropertyMetadata.DefaultValue%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.DefaultValue%2A>メタデータでそれを指定した最も近い先祖します。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 実装は置き換えられます。 新しく追加した場合<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>オーバーライドでは、値で<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>はメタデータでそれを指定した最も近い先祖からの参照として昇格します。  
  
- プロパティ システム動作はのみですが、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>直接のメタデータが呼び出されます。 その他への参照<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>階層内の実装が保持されます。  
  
 この動作を実装して<xref:System.Windows.PropertyMetadata.Merge%2A>、派生メタデータ クラスでオーバーライドすることができます。  
  
#### <a name="overriding-attached-property-metadata"></a>添付プロパティのメタデータのオーバーライド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、添付プロパティは依存関係プロパティとして実装されます。 このことは、添付プロパティもプロパティ メタデータを持ち、これを個々のクラスでオーバーライドできることを意味します。 添付プロパティのスコープに関する考慮事項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は通常を<xref:System.Windows.DependencyObject>添付プロパティを設定を持つことができます。 そのため、いずれか<xref:System.Windows.DependencyObject>派生クラスは、すべての添付プロパティのメタデータをオーバーライドできるように、クラスのインスタンスに設定する必要があります。 オーバーライドできるのは、既定値、コールバック、または WPF フレームワーク レベルの特性報告プロパティです。 添付プロパティがクラスのインスタンスで設定されている場合、そのオーバーライド プロパティ メタデータ特性が適用されます。 たとえば、プロパティが他では特に指定されていないときには、オーバーライド値がクラスのインスタンス上の添付プロパティの値として報告されるように、既定値をオーバーライドできます。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>添付プロパティのプロパティは無効です。  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>既存の依存関係プロパティの所有者としてのクラスの追加  
 クラスがそれ自体を使用して、既に登録されている依存関係プロパティの所有者として追加、<xref:System.Windows.DependencyProperty.AddOwner%2A>メソッド。 これにより、当初は別の型に対して登録された依存関係プロパティをクラスで使用できるようになります。 通常、追加するクラスは、所有者としてその依存関係プロパティを最初に登録した型の派生クラスではありません。 これにより、元の所有者クラスと追加するクラスが同一のクラス階層内にない場合でも、クラスとその派生クラスで依存関係プロパティの実装を "継承" することが事実上可能になります。 また、追加するクラスとすべての派生クラスでは、型固有のメタデータを元の依存関係プロパティに提供することができます。  
  
 追加するクラスは、プロパティ システムのユーティリティ メソッドを介してそれ自体を所有者として追加するだけでなく、追加のパブリック メンバーをそれ自体で宣言する必要があります。これは、依存関係プロパティを完全な形でプロパティ システムに登録し、コードとマークアップの両方に対して公開するためです。 既存の依存関係プロパティを追加するクラスは、その依存関係プロパティのオブジェクト モデルを公開する限り、新しいカスタム依存関係プロパティを定義するクラスと同様の役割を負います。 これらのメンバーの中で最初に公開するのは、依存関係プロパティの識別子フィールドです。 このフィールドにする必要があります、`public static readonly`型のフィールド<xref:System.Windows.DependencyProperty>の戻り値に割り当てられる、<xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出します。 2 番目に定義するメンバーは、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] の "ラッパー" プロパティです。 ラッパーにより、コードで、依存関係プロパティを操作するはるかに便利です (呼び出しを避けるため<xref:System.Windows.DependencyObject.SetValue%2A>各時間、およびラッパー自体でその呼び出しを 1 回だけを行うことができます)。 このラッパーの実装方法は、カスタム依存関係プロパティを登録する場合の実装方法とまったく同じです。 依存関係プロパティの実装の詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「[依存関係プロパティの所有者の種類を追加する](how-to-add-an-owner-type-for-a-dependency-property.md)」を参照してください。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner および添付プロパティ  
 呼び出すことができます<xref:System.Windows.DependencyProperty.AddOwner%2A>所有者クラスで添付プロパティとして定義されている依存関係プロパティ。 通常、これは、以前の添付プロパティを非添付の依存関係プロパティとして公開する目的で行います。 公開し、<xref:System.Windows.DependencyProperty.AddOwner%2A>として値を返す、`public static readonly`依存関係プロパティの識別子として使用するためのフィールドし、プロパティが、メンバー テーブルが表示され、非添付プロパティをサポートするように、適切な「ラッパー」プロパティを定義しますクラスで使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [フレームワーク プロパティ メタデータ](framework-property-metadata.md)
