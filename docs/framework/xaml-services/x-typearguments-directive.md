---
title: x:TypeArguments ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: a2a960870d368e57272b3368e69eb38ebbe2ba5d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053714"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments ディレクティブ
ジェネリックの制約型引数をジェネリック型のコンストラクターに渡します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`object`|CLR ジェネリック型によってサポートされる XAML 型のオブジェクト要素宣言。 が`object`既定の xaml 名前空間からではない xaml 型を参照し`object`ている場合、は、 `object`が存在する場合に xaml 名前空間を示すプレフィックスを必要とします。|  
|`typeString`|1つ以上の XAML 型名を文字列として宣言する文字列。この文字列は、CLR ジェネリック型の型引数を提供します。 追加の構文ノートについては、「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 ほとんどの場合、 `typeString`文字列の情報項目として使用される XAML 型にはプレフィックスが付きます。 Clr ジェネリック制約の一般的な型 (や<xref:System.Int32> <xref:System.String>など) は、clr 基底クラスライブラリから取得されます。 これらのライブラリは、フレームワーク固有の一般的な既定の XAML 名前空間にマップされないため、XAML の使用にはプレフィックスマッピングが必要です。  
  
 複数の XAML 型名を指定するには、コンマ区切り記号を使用します。  
  
 ジェネリック制約自体がジェネリック型を使用する場合は、入れ子になった制約型の引数をかっこ () で囲むことができます。  
  
 この定義は .NET Framework XAML `x:TypeArguments`サービスと CLR バッキングの使用に固有であることに注意してください。 言語レベルの定義については、 [ \[\] 「5.3.11」セクション](https://go.microsoft.com/fwlink/?LinkId=114525)を参照してください。  
  
## <a name="usage-examples"></a>使用例  
 これらの例では、次の XAML 名前空間定義が宣言されているものとします。  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>リスト\<文字列 >  
 `<scg:List x:TypeArguments="sys:String" ...>`<xref:System.String>型引数を<xref:System.Collections.Generic.List%601>使用して新しいをインスタンス化します。  
  
### <a name="dictionarystringstring"></a>ディクショナリ\<文字列、文字列 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`2つ<xref:System.Collections.Generic.Dictionary%602> <xref:System.String>の型引数を使用して、新しいをインスタンス化します。  
  
### <a name="queuekeyvaluepairstringstring"></a>Queue < KeyValuePair\<string、string > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`内部制約型<xref:System.Collections.Generic.Queue%601>引数<xref:System.Collections.Generic.KeyValuePair%602> <xref:System.String> と<xref:System.String>を使用して、の制約を持つ新しいをインスタンス化します。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 と WPF 汎用 XAML の使用  
 Xaml 2006 の使用、および WPF アプリケーションで使用される xaml では、一般的に xaml `x:TypeArguments`からのジェネリック型の使用に関して次の制限があります。  
  
- ジェネリック型を参照する汎用 XAML 使用をサポートできるのは、XAML ファイルのルート要素だけです。  
  
- ルート要素は、少なくとも1つの型引数を持つジェネリック型にマップする必要があります。 たとえば、の<xref:System.Windows.Navigation.PageFunction%601>ようになります。 ページ関数は、WPF の XAML 汎用使用サポートの主要なシナリオです。  
  
- ジェネリックのルート要素 XAML オブジェクト要素も、を使用して`x:Class`部分クラスを宣言する必要があります。 これは、WPF ビルドアクションを定義する場合にも当てはまります。  
  
- `x:TypeArguments`入れ子になったジェネリック制約を参照することはできません。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>WPF 3.0 または WPF 3.5 依存関係のない XAML 2009 または XAML 2006  
 Xaml 2006 または XAML 2009 の xaml サービスでは、一般的な XAML の使用に関する WPF 関連の制限は緩やかに .NET Framework ます。 バッキング型システムおよびオブジェクトモデルがサポートできる XAML マークアップ内の任意の位置で、ジェネリックオブジェクト要素をインスタンス化できます。  
  
 CLR 基本型をマップして共通言語プリミティブの XAML 型を取得するのではなく、XAML 2009 を使用する場合は、 `typeString`[共通の Xaml 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)を内の情報項目として使用できます。 たとえば、次のように宣言できます (プレフィックスの割り当ては表示されませんが、x は xaml 言語2009の xaml 言語の xaml 名前空間です)。  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF で .NET Framework 4 を対象とする場合は、xaml 2009 の機能を`x:TypeArguments`と共に使用できますが、ルース xaml (マークアップコンパイルされていない xaml) に対してのみ使用できます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。 XAML をマークアップする必要がある場合は、「XAML 2006 および WPF 汎用 XAML の使用」セクションに記載されている制限事項に従って操作する必要があります。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [x:Type マークアップ拡張機能](x-type-markup-extension.md)
- [共通の XAML 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)
- [XAML のジェネリック](generics-in-xaml.md)
