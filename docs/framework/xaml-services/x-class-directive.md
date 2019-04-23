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
ms.openlocfilehash: 5f7b072e90e92070dd7fda2f0ad44814009268b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199454"
---
# <a name="xclass-directive"></a>x:Class ディレクティブ
マークアップと分離コードの間の部分クラスを結合する XAML マークアップのコンパイルを構成します。 内の別のコード ファイルでコードの部分クラスが定義されている、[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]言語は、通常、マークアップの部分クラスは、XAML のコンパイル時にコードを生成して作成します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|任意。 指定します、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]で識別される部分クラスを含む名前空間`classname`します。 場合`namespace`を指定すると、ドット (.) で区切られます`namespace`と`classname`します。 「解説」を参照してください。|  
|`classname`|必須。 指定します、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]読み込まれた XAML およびその XAML の分離コードで接続する部分クラスの名前。|  
  
## <a name="dependencies"></a>依存関係  
 `x:Class` XAML の運用環境のルート要素でのみ指定できます。 `x:Class` XAML の運用環境での親を持つ任意のオブジェクトでは無効です。 詳細については、次を参照してください。 [ \[MS XAML\]セクション 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
## <a name="remarks"></a>Remarks  
 `namespace`値は、.NET Framework プログラミングで一般的な手法は、名前の階層に関連する名前空間を整理する追加のドットを含めることができます。 文字列の最後のドットのみ`x:Class`を分離する値を解釈`namespace`と`classname.`クラスとして使用される`x:Class`入れ子になったクラスにすることはできません。 ドットの意味を判断するため、入れ子になったクラスは許可されません`x:Class`文字列が入れ子になったクラスが許可されている場合はあいまいです。  
  
 既存のプログラミング モデルを使用する`x:Class`、`x:Class`は完全に分離コードがない XAML ページ有効であることの意味では省略可能です。 ただし、その機能は、XAML を使用しているフレームワークによって実装されるビルド アクションと対話します。 `x:Class` 機能は、XAML で指定されたコンテンツのさまざまな分類は、アプリケーション モデルであるし、ビルド アクションを対応するロールの影響も受けます。 指定した、XAML では、イベント処理の属性値または分離コード クラスでクラスを定義するが、カスタム要素をインスタンス化を宣言する場合、`x:Class`ディレクティブの参照 (または[X:subclass](x-subclass-directive.md)) に、分離コードの適切なクラスです。  
  
 値、`x:Class`ディレクティブは、アセンブリ情報がない場合は、クラスの完全修飾名を指定する文字列である必要があります (に相当、 <xref:System.Type.FullName%2A?displayProperty=nameWithType>)。 単純なアプリケーションでは、分離コードがそのように (クラス レベルで コードの定義から開始) も構造化された場合、CLR 名前空間の情報を省略できます。  
  
 ページまたはアプリケーションの定義については、分離コード ファイルは、コンパイル済みのアプリケーションを作成し、マークアップ コンパイルは、プロジェクトの一部として含まれているコード ファイル内である必要があります。 CLR クラスの名前規則に従う必要があります。 詳細については、次を参照してください。 [Framework デザイン ガイドライン](../../standard/design-guidelines/index.md)します。 既定では、分離コード クラスがある必要があります`public`。 ただし、を使用して異なるアクセス レベルで定義できる、 [X:classmodifier ディレクティブ](x-classmodifier-directive.md)します。  
  
 この解釈、`x:Class`属性にのみ適用されます、CLR ベースの XAML 実装では、特に .NET Framework XAML サービスにします。 CLR には基づいていませんし、.NET Framework XAML サービスを使用しないその他の XAML 実装には、XAML マークアップを接続し、実行時のコードをバックアップするための別の解像度数式を使用可能性があります。 一般的な解釈の詳細については`x:Class`を参照してください[ \[MS XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
 アーキテクチャの意味のあるレベルで`x:Class`.NET Framework XAML サービスでは未定義です。 これは、.NET Framework XAML サービスでプログラミング モデルでは、どの XAML マークアップとコードのバックアップの接続が指定されていないためにです。 その他の使用、`x:Class`ディレクティブは、プログラミング モデルまたはアプリケーションのモデルを使用して、XAML マークアップと CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実装される場合があります。 各フレームワークには、独自のビルド操作をいくつかの動作またはビルド環境に含める必要がある特定のコンポーネントを有効にすることができます。 フレームワーク内でビルド アクションは分離コードに使用される特定の CLR 言語によっても異なります。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF のプログラミング モデルでは、X:class  
 WPF アプリケーションと、WPF アプリケーション モデルで`x:Class`XAML ファイルのルートであるし、コンパイルされる任意の要素の属性として宣言することができます (と WPF アプリケーション プロジェクトでは、XAML が含まれている`Page`ビルド アクション)、または、「c4 > <xref:System.Windows.Application> コンパイルされた WPF アプリケーションのアプリケーション定義のルート。 宣言する`x:Class`ページのルートまたはアプリケーションのルート以外の要素またはコンパイルされない WPF XAML ファイルでは、コンパイル時エラーが発生、[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]と[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]WPF XAML コンパイラ。 他の側面について`x:Class`WPF での処理を参照してください[分離コードと wpf XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)します。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation の X:class  
 Windows Workflow foundation で`x:Class`全体を XAML で構成されるカスタム アクティビティのクラスの名前または分離コードを含むアクティビティ デザイナーの XAML ページの部分クラスの名前します。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Class` に関しては、別途ドキュメントが用意されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)します。  
  
## <a name="see-also"></a>関連項目

- [x:Subclass ディレクティブ](x-subclass-directive.md)
- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier ディレクティブ](x-classmodifier-directive.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
