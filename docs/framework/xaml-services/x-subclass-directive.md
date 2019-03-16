---
title: x:Subclass ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: c348d8fa2bd66a9abbb64c9363bb4dae0933ba34
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048003"
---
# <a name="xsubclass-directive"></a>x:Subclass ディレクティブ
XAML マークアップのコンパイルの動作を変更するときに`x:Class`も提供されます。 基づいている部分クラスを作成する代わりに`x:Class`、提供されている`x:Class`は中間のクラスとして作成し、指定された派生クラスをベースにする予定ですし`x:Class`。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|任意。 含む CLR 名前空間を指定します`classname`します。 場合`namespace`を指定すると、ドット (.) で区切られます`namespace`と`classname`します。|  
|`classname`|必須。 読み込まれた XAML およびその XAML の分離コードで接続する部分クラスの CLR 名を指定します。 「解説」を参照してください。|  
|`subclassNamespace`|任意。 異なっていてもかまいません`namespace`他の各名前空間を解決できない場合。 含む CLR 名前空間を指定します`subclassName`します。 場合`subclassName`を指定すると、ドット (.) で区切られます`subclassNamespace`と`subclassName`します。|  
|`subclassName`|必須。 サブクラスの CLR 名を指定します。|  
  
## <a name="dependencies"></a>依存関係  
 [X:class ディレクティブ](x-class-directive.md)オブジェクトが同じでも指定する必要があり、そのオブジェクトは、XAML の運用環境のルート要素である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `x:Subclass` 部分クラス宣言をサポートしない言語の使用状況は主にします。  
  
 として使用されるクラス、`x:Subclass`入れ子になったクラスにすることはできませんと`x:Subclass`「の依存関係」セクションで説明したように、ルート オブジェクトを参照する必要があります。  
  
 それ以外の場合の概念の意味`x:Subclass`の .NET Framework XAML サービス実装では未定義です。 これは、.NET Framework XAML サービスの動作で、全体的なプログラミング モデルでは、どの XAML マークアップとコードのバックアップの接続が指定されていないためにです。 さらに、概念の実装に関連する`x:Class`と`x:Subclass`プログラミング モデルまたはアプリケーションのモデルを使用して、XAML マークアップ、コンパイルされたマークアップ、および CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実行されます。 各フレームワークでは、いくつかの動作、またはビルド環境に含める必要がある特定のコンポーネントを有効にする、独自のビルド操作があります。 、フレームワーク内でビルド アクションが分離コードに使用される特定の CLR 言語に基づいてもは異なります。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:Subclass` ページ ルートまたは指定できます、<xref:System.Windows.Application>を既に持っているアプリケーション定義のルート`x:Class`します。 宣言する`x:Subclass`ページまたはアプリケーションのルート、または指定することがない以外の任意の要素で`x:Class`存在する場合、コンパイル時エラーが発生します。  
  
 その作業を正しくクラスの派生を作成する、`x:Subclass`シナリオは非常に複雑です。 中間ファイル (.xaml ファイル名を反映する名前を持つ、マークアップ コンパイルにより、プロジェクトの obj フォルダーで作成される .g ファイル) を確認する必要があります。 これらの中間ファイルは、コンパイル済みのアプリケーションに参加している部分クラスに特定のプログラミング構成要素の起点を特定するのに役立ちます。  
  
 派生クラスでイベント ハンドラーである必要があります`internal override`(`Friend Overrides` Microsoft Visual Basic で) コンパイル時に中間クラスで作成されると、ハンドラーのスタブをオーバーライドするためにします。 それ以外の場合、派生クラスの実装には、(シャドウ) 中間クラスの実装が非表示にして、中間クラス ハンドラーは呼び出されません。  
  
 両方を定義するときに`x:Class`と`x:Subclass`、によって参照されるクラスのすべての実装を提供する必要はありません`x:Class`します。 のみを使用して、名前を指定する必要があります、`x:Class`属性、コンパイラに中間ファイル (コンパイラはオンに既定の名前をここで) で作成したクラスのガイダンスがあります。 与えることができます、`x:Class`クラスの実装。 ただし、これは、典型的なシナリオの両方を使用して`x:Class`と`x:Subclass`します。  
  
## <a name="see-also"></a>関連項目
- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
