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
ms.openlocfilehash: 79264687b3a031fcf02ce65a907c7f21e216fbc9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622763"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments ディレクティブ
パスの制約は、ジェネリック型のコンス トラクターに汎用の引数を入力します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`object`|CLR のジェネリック型によってサポートされる XAML 型のオブジェクト要素の宣言。 場合`object`が既定の XAML 名前空間からされていない XAML 型を表して`object`を XAML 名前空間を示すためにプレフィックスが必要です、`object`存在します。|  
|`typeString`|1 つまたは複数の XAML を宣言する文字列は、CLR のジェネリック型の型引数を指定する文字列として名前を入力します。 追加の構文のノートの「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 ほとんどの場合、情報の項目として使用される XAML 型を`typeString`文字列が付きます。 一般的な種類の CLR のジェネリック制約 (たとえば、<xref:System.Int32>と<xref:System.String>) CLR 基本クラス ライブラリから取得します。 これらのライブラリでは、標準的なマップされたフレームワーク固有の既定の XAML 名前空間ではなく、そのため、XAML の使用状況のプレフィックスのマッピングが必要です。  
  
 1 つ以上の XAML 型名を指定するには、コンマ区切り記号を使用します。  
  
 ジェネリック制約自体がジェネリック型を使用する場合は、かっこ () で入れ子になった制約の型引数を格納できます。  
  
 注意この定義の`x:TypeArguments`は .NET Framework XAML サービスに固有と CLR バッキングを使用します。 言語レベルの定義が記載[ \[MS XAML\]セクション 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
## <a name="usage-examples"></a>使用例  
 これらの例については、次の XAML 名前空間の定義が宣言されていることを想定します。  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>リスト\<文字列 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.List%601>で、<xref:System.String>引数を入力します。  
  
### <a name="dictionarystringstring"></a>ディクショナリ\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.Dictionary%602>の 2 つ<xref:System.String>引数を入力します。  
  
### <a name="queuekeyvaluepairstringstring"></a>キュー < KeyValuePair\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 新しいインスタンスを作成<xref:System.Collections.Generic.Queue%601>の制約を持つ<xref:System.Collections.Generic.KeyValuePair%602>内部制約の型引数を持つ<xref:System.String>と<xref:System.String>します。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 および WPF XAML のジェネリックの使用法  
 XAML 2006 の使用状況、および XAML の WPF アプリケーションで使用する、次の制限の存在の`x:TypeArguments`および一般的な XAML のジェネリック型の使用状況。  
  
- XAML ファイルのルート要素だけでは、ジェネリック型を参照する汎用的な XAML 使用量をサポートできます。  
  
- ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。 例としては、<xref:System.Windows.Navigation.PageFunction%601>します。 ページ関数は、WPF における XAML のジェネリックの使用法サポートの主なシナリオです。  
  
- ジェネリックのルート要素の XAML オブジェクト要素が、部分クラスを使用して、宣言する必要がありますも`x:Class`します。 これは、ビルド アクションを WPF を定義する場合でも当てはまります。  
  
- `x:TypeArguments` 入れ子になったジェネリック制約は参照できません。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 または XAML 2006 なし、WPF 3.0 または 3.5 の WPF 依存関係  
 XAML 2006 または XAML 2009 のいずれかの .NET Framework XAML サービスでは、WPF に関連する XAML のジェネリックの使用法の制限が緩和されます。 バッキング型システムとオブジェクト モデルをサポートする XAML のマークアップ内の任意の位置にある汎用オブジェクトの要素をインスタンス化することができます。  
  
 XAML 2009 を使用する場合、CLR をマップする代わりに基本の共通言語プリミティブの XAML 型を取得する型、使用することができます[共通の XAML 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)内の情報項目として、`typeString`します。 たとえば、次を宣言できます (表示されませんが、プレフィックスのマッピングが、x は XAML 2009 の XAML 言語の XAML 名前空間)。  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 対象とする場合と WPF で[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、と共に XAML 2009 の機能を使用する`x:TypeArguments`loose XAML (XAML マークアップ コンパイルされていない) に対してのみです。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。 必要なマークアップをコンパイルする場合、XAML は、「XAML 2006 および WPF 汎用 XAML 使用法」セクションに記載されている制限で動作する必要があります。  
  
## <a name="see-also"></a>関連項目

- [x:Class ディレクティブ](x-class-directive.md)
- [x:Type マークアップ拡張機能](x-type-markup-extension.md)
- [共通の XAML 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)
- [XAML のジェネリック](generics-in-xaml.md)
