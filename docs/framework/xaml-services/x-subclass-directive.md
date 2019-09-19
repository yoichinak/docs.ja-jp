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
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053910"
---
# <a name="xsubclass-directive"></a>x:Subclass ディレクティブ
が指定されている`x:Class`場合に XAML マークアップのコンパイル動作を変更します。 に`x:Class`基づく部分クラスを作成する代わりに、指定さ`x:Class`れたが中間クラスとして作成され、指定された派生クラスがに`x:Class`基づいていると想定されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|任意。 を含む`classname`CLR 名前空間を指定します。 を`namespace`指定した場合、ドット (.) `namespace`は`classname`とを分離します。|  
|`classname`|必須。 読み込まれた XAML とその XAML の分離コードを接続する部分クラスの CLR 名を指定します。 「解説」を参照してください。|  
|`subclassNamespace`|任意。 は、各名前`namespace`空間が他の名前空間を解決できるかどうかとは異なる場合があります。 を含む`subclassName`CLR 名前空間を指定します。 を`subclassName`指定した場合、ドット (.) `subclassNamespace`は`subclassName`とを分離します。|  
|`subclassName`|必須。 サブクラスの CLR 名を指定します。|  
  
## <a name="dependencies"></a>依存関係  
 [X:Class ディレクティブ](x-class-directive.md)は、同じオブジェクトでも指定する必要があります。また、そのオブジェクトは XAML 運用のルート要素である必要があります。  
  
## <a name="remarks"></a>Remarks  
 `x:Subclass`使用法は、主に部分クラス宣言をサポートしない言語を対象としています。  
  
 として`x:Subclass`使用されるクラスは、入れ子になっ`x:Subclass`たクラスにすることはできません。また、「依存関係」セクションで説明されているように、ルートオブジェクトを参照する必要があります。  
  
 それ以外の場合、の`x:Subclass`概念上の意味は、.NET Framework XAML サービスの実装によって定義されていません。 これは .NET Framework XAML サービスの動作では、XAML マークアップとバッキングコードの接続によって使用されるプログラミングモデル全体が指定されないためです。 およびに`x:Class`関連するその`x:Subclass`他の概念の実装は、プログラミングモデルまたはアプリケーションモデルを使用して、XAML マークアップ、コンパイルされたマークアップ、および CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実行されます。 各フレームワークには、動作の一部またはビルド環境に含まれる必要がある特定のコンポーネントを有効にする独自のビルドアクションがある場合があります。 フレームワーク内では、ビルドアクションは、分離コードに使用される特定の CLR 言語によって異なる場合もあります。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:Subclass`は、が`x:Class`既に存在するアプリケーション定義<xref:System.Windows.Application>内のページルートまたはルートに配置できます。 ページ`x:Subclass`またはアプリケーションルート以外の要素での宣言、または存在しない`x:Class`要素の指定により、コンパイル時エラーが発生します。  
  
 この`x:Subclass`シナリオに対して正しく動作する派生クラスを作成するのは非常に複雑です。 場合によっては、中間ファイル (マークアップコンパイルによってプロジェクトの obj フォルダーに生成された g ファイル) を調べて、.xaml ファイル名が含まれている名前を使用する必要があります。 これらの中間ファイルを使用すると、コンパイルされたアプリケーションの部分クラスに結合されている特定のプログラミング構成要素の発生元を特定できます。  
  
 コンパイル時に中間クラスで作成さ`internal override`れ`Friend Overrides`たハンドラーのスタブをオーバーライドするには、派生クラスのイベントハンドラーが (Microsoft Visual Basic) である必要があります。 それ以外の場合は、派生クラスの実装によって中間クラスの実装が非表示になり、中間クラスのハンドラーは呼び出されません。  
  
 と`x:Class` `x:Class`の両方を定義する場合、によって参照されるクラスの実装を指定する必要はありません。 `x:Subclass` `x:Class`属性を使用して名前を指定するだけで、中間ファイルに作成するクラスに関するガイダンスがコンパイラに提供されます (この場合、コンパイラは既定の名前を選択しません)。 クラスに`x:Class`は実装を与えることができますが、これはと`x:Subclass`の両方`x:Class`を使用する場合の一般的なシナリオではありません。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [WPF における XAML とカスタム クラス](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
