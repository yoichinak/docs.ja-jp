---
title: x:Class ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: 563802be655e0cb66c9a2735a64da9d7723c2a43
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401516"
---
# <a name="xclass-directive"></a>x:Class ディレクティブ
マークアップと分離コードの間で部分クラスを結合するように、XAML マークアップのコンパイルを構成します。 コード部分クラスは、共通言語仕様 (CLS) 言語の個別のコードファイルで定義されます。一方、マークアップ部分クラスは、通常、XAML のコンパイル時にコード生成によって作成されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|任意。 によって`classname`識別される部分クラスを含む CLR 名前空間を指定します。 を`namespace`指定した場合、ドット (.) `namespace`は`classname`とを分離します。 「解説」を参照してください。|  
|`classname`|必須。 読み込まれた XAML とその XAML の分離コードを接続する部分クラスの CLR 名を指定します。|  
  
## <a name="dependencies"></a>依存関係  
 `x:Class`は、XAML 運用環境のルート要素でのみ指定できます。 `x:Class`は、XAML 運用環境で親を持つオブジェクトでは無効です。 詳細については、「 [ \[4.3.1.6\] 」セクション](https://go.microsoft.com/fwlink/?LinkId=114525)を参照してください。  
  
## <a name="remarks"></a>Remarks  
 この`namespace`値には、関連する名前空間を名前階層に編成するための追加のドットが含まれている場合があります。これは、.NET Framework プログラミングにおける一般的な手法です。 値の`x:Class`文字列内の最後のドットのみが`classname.`分離`namespace`され、として`x:Class`使用されるクラスは、入れ子になったクラスにすることはできません。 入れ子になったクラスが許可されている場合`x:Class` 、入れ子になったクラスは使用できません。  
  
 を使用`x:Class`する既存のプログラミングモデル`x:Class`では、分離コードのない XAML ページを持つことが完全に有効であるという意味では省略可能です。 ただし、この機能は、XAML を使用するフレームワークによって実装されるビルドアクションと対話します。 `x:Class`機能は、XAML によって指定されたコンテンツのさまざまな分類がアプリケーションモデルとそれに対応するビルドアクションに存在するロールの影響も受けます。 XAML でイベント処理属性値が宣言されている場合、または定義するクラスが分離コードクラスに含まれるカスタム要素をインスタンス`x:Class`化する場合は、の適切なクラスにディレクティブ参照 (または[x:Subclass](x-subclass-directive.md)) を指定する必要があります。分離コード。  
  
 `x:Class`ディレクティブの値は、クラスの完全修飾名を指定する文字列である必要があります。ただし、 <xref:System.Type.FullName%2A?displayProperty=nameWithType>アセンブリ情報は含まれません (と同じ)。 単純なアプリケーションの場合、分離コードがその方法でも構造化されている場合は、CLR 名前空間の情報を省略できます (コード定義はクラスレベルで開始されます)。  
  
 ページまたはアプリケーション定義の分離コードファイルは、コンパイルされたアプリケーションを生成するプロジェクトの一部として含まれているコードファイル内に存在する必要があります。また、マークアップコンパイルも関係します。 CLR クラスの名前の規則に従う必要があります。 詳細については、「[フレームワークのデザインガイドライン](../../standard/design-guidelines/index.md)」を参照してください。 既定では、分離コードクラスはで`public`ある必要がありますが、 [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)を使用して別のアクセスレベルで定義することもできます。  
  
 この`x:Class`属性の解釈は CLR ベースの xaml 実装にのみ適用されます。特に xaml サービスに .NET Framework ます。 CLR に基づいていない、.NET Framework XAML サービスを使用していないその他の XAML 実装は、XAML マークアップの接続や実行時コードのバックアップに別の解決式を使用する場合があります。 の一般的な解釈の`x:Class`詳細については、「 [ \[MS\]XAML](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
 特定のレベルのアーキテクチャでは、の`x:Class`意味は .NET Framework XAML サービスでは定義されていません。 これは .NET Framework XAML サービスで、XAML マークアップとバッキングコードの接続に使用するプログラミングモデルが指定されていないためです。 ディレクティブのその他`x:Class`の使用方法は、プログラミングモデルまたはアプリケーションモデルを使用して XAML マークアップと CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実装される場合があります。 各フレームワークは独自のビルドアクションを持つことができ、ビルド環境に含まれる必要がある動作または特定のコンポーネントの一部を有効にすることができます。 フレームワーク内では、ビルドアクションは、分離コードに使用されている特定の CLR 言語によって異なる場合もあります。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF プログラミングモデルにおける x:Class  
 Wpf アプリケーションと wpf アプリケーションモデルでは、 `x:Class`は、xaml ファイルのルートである任意の要素の属性として宣言できます (xaml がビルドアクションを持つ`Page` WPF アプリケーションプロジェクトに含まれる場合)。または、<xref:System.Windows.Application>コンパイルされた WPF アプリケーションのアプリケーション定義の c4 > root。 ページ`x:Class`ルートまたはアプリケーションルート以外の要素、またはコンパイルされていない wpf xaml ファイル上でを宣言すると、.NET Framework 3.0 および .NET Framework 3.5 wpf xaml コンパイラでコンパイル時エラーが発生します。 Wpf での`x:Class`処理に関するその他の側面については、「 [wpf の分離コードと XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation の x:Class  
 Windows Workflow Foundation の場合`x:Class` 、は、全体が xaml で構成されるカスタムアクティビティのクラスに名前を付けます。または、分離コードを使用してアクティビティデザイナーの xaml ページの部分クラスに名前を付けます。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Class` に関しては、別途ドキュメントが用意されています。 詳細については[、「XAML 名前空間 (x:)」を参照してください。言語機能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>関連項目

- [x:Subclass ディレクティブ](x-subclass-directive.md)
- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
