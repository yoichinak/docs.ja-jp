---
title: x:Array のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 4f4e26eb3e5ccaf66b2173c7fc9952375c5f2a58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139140"
---
# <a name="xarray-markup-extension"></a>x:Array のマークアップ拡張機能
マークアップ拡張機能を XAML でのオブジェクトの配列には、一般的なサポートを提供します。 これに対応して、 `x:ArrayExtension` XAML [XAML MS] を入力します。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`typeName`|型の名前を`x:Array`が含まれます。 `typeName` 可能性があります (および多くの場合は)、XAML を含む名前空間を XAML のプレフィックスとして定義を入力します。|  
|`arrayContents`|組み込みに割り当てられている項目コンテンツ`ArrayExtension.Items`プロパティ。 通常、これらの項目が内に含まれる 1 つまたは複数のオブジェクト要素として指定、`x:Array`開始タグと終了します。 指定されたオブジェクトは、ここで指定された XAML 型に代入する予想される`typeName`します。|  
  
## <a name="remarks"></a>Remarks  
 `Type` すべての必須の属性は、 `x:Array` object 要素。 A`Type`パラメーターの値が使用する必要はありません、`x:Type`マークアップ拡張機能は、短い型の名前は、XAML 型を文字列として指定できます。  
  
 入力 XAML の型と CLR の出力の間の関係、.NET Framework XAML サービス実装で<xref:System.Type>作成された配列は、サービス コンテキストのマークアップ拡張機能によって影響を受けます。 出力<xref:System.Type>は、<xref:System.Xaml.XamlType.UnderlyingType%2A>ために必要な検索した後、入力の XAML 型の<xref:System.Xaml.XamlType>XAML スキーマ コンテキストに基づいて、<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。  
  
 配列の内容に割り当てられている、処理されるときに、`ArrayExtension.Items`組み込みプロパティ。 <xref:System.Windows.Markup.ArrayExtension>実装では、これは、表さ<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>します。  
  
 このマークアップ拡張機能の処理がによって定義されている、.NET Framework XAML サービス実装、<xref:System.Windows.Markup.ArrayExtension>クラス。 <xref:System.Windows.Markup.ArrayExtension> シールされていないと、カスタムの配列型のマークアップ拡張機能の実装の基礎として使用できます。  
  
 `x:Array` 以上の目的の一般的な XAML の言語の機能拡張です。 `x:Array`にも、構造化されたプロパティのコンテンツとして XAML でサポートされているコレクションを取得する特定のプロパティの XAML 値を指定するために役立ちます。 内容を指定するなど、<xref:System.Collections.IEnumerable>プロパティを`x:Array`使用量。  
  
 `x:Array` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 `x:Array` そのルールの例外では部分的に代替の属性値の処理を提供することではなく`x:Array`その内部テキ スト コンテンツの代替の処理を提供します。 この動作により、型を配列にグループ化とは名前付きの配列にアクセスして、後で、分離コードで参照されている既存のコンテンツ モデルでサポートされていない可能性があります。呼び出すことができます<xref:System.Array>個々 の配列の項目を取得するメソッド。  
  
 中かっこを使用して、XAML 内のすべてのマークアップ拡張機能 ({,} `)`それぞれの属性構文では、マークアップ拡張機能が属性値を処理する必要がありますを XAML プロセッサが認識される規約。 一般にマークアップ拡張機能の詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)します。  
  
 XAML 2009 で`x:Array`マークアップ拡張機能ではなくプリミティブ言語として定義されます。 詳細については、次を参照してください。[共通の XAML 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)します。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 設定するオブジェクト要素では通常、`x:Array`に存在する要素のない、 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML 名前空間に既定以外の XAML 名前空間プレフィックス マッピングが必要とします。  
  
 たとえば、2 つの文字列の単純な配列では、次の`sys`プレフィックス (とも`x`)、配列のレベルで定義します。  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 配列要素として使用されるカスタムの型のクラスはオブジェクト要素としての XAML でインスタンス化するための要件もサポートする必要があります。 詳細については、次を参照してください。 [XAML とカスタム クラスの WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)します。  
  
## <a name="see-also"></a>関連項目

- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
