---
title: XAML のジェネリック
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 6ca7986513d1a6cbe160ca1a0af6699c323aac7e
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690649"
---
# <a name="generics-in-xaml"></a>XAML のジェネリック
System.Xaml に実装されている .NET Framework XAML サービスでは、CLR のジェネリック型を使用するためのサポートを提供します。 このサポートには、引数の型としてジェネリックの制約を指定して、適切なを呼び出すことによって、制約を適用するが含まれます。`Add`メソッドのジェネリック コレクションの場合。 このトピックを使用して、XAML のジェネリック型の参照の側面について説明します。  
  
## <a name="xtypearguments"></a>x:TypeArguments  
 `x:TypeArguments` ディレクティブは、XAML 言語によって定義されます。 ジェネリックの型によってサポートされる XAML 型のメンバーとして使用されているときに`x:TypeArguments`型のバッキング コンス トラクターにジェネリック引数を渡すを制限します。 .NET Framework XAML サービスに関連する参照構文の使用`x:TypeArguments`、構文の例を含むを参照してください[X:typearguments ディレクティブ](x-typearguments-directive.md)します。  
  
 `x:TypeArguments`文字列を受け取り、型コンバーター バッキングの場合は通常、属性の使用法は XAML で宣言されています。  
  
 XAML ノード ストリームについては、宣言によって`x:TypeArguments`から取得できます<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>で、`StartObject`ノード ストリーム内の位置。 戻り値<xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType>の一覧を示します<xref:System.Xaml.XamlType>値。 呼び出すことによって、XAML の型がジェネリック型を表すかどうかの決定ができる<xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>します。  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>ルールと XAML のジェネリックの構文表記規則  
 XAML でのジェネリック型する必要があります常として表す、制約付きの汎用的な制約なしのジェネリックは、XAML 型システムまたは XAML ノード ストリームに存在することはありませんし、XAML マークアップで表現できることはできません。 によって参照されているジェネリック型の入れ子にされた型の制約である場合、XAML の属性構文内で参照できるジェネリック`x:TypeArguments`、またはの場合、`x:Type`ジェネリック型の CLR 型参照を提供します。 これは、<xref:System.Xaml.Schema.XamlTypeTypeConverter>クラスの .NET Framework XAML サービスで定義します。  
  
 XAML 属性の構文形式で有効になって<xref:System.Xaml.Schema.XamlTypeTypeConverter>一般的な MSIL を変更します]、[角度を使用する CLR の構文規則の種類と、ジェネリックの制約の角かっこし、制約のコンテナーのかっこを代わりに置き換えられます。 例については、次を参照してください。 [X:typearguments ディレクティブ](x-typearguments-directive.md)します。  
  
## <a name="generics-and-xaml-2009-features"></a>ジェネリックと XAML 2009 の機能  
 XAML 2009 を使用する場合、CLR をマップする代わりに基本の共通言語プリミティブの XAML 型を取得する型、使用することができます[XAML 2009 の組み込み型](built-in-types-for-common-xaml-language-primitives.md)内の情報項目として`x:TypeArguments`します。 たとえば、次を宣言できます (表示されませんが、マッピングのプレフィックスが`x`は XAML 2009 の XAML 言語の XAML 名前空間です)。  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>WPF およびその他の v3.5 フレームワークでジェネリックのサポート  
 具体的には WPF では、対象とする場合の XAML 2006 の使用状況の[X:class](x-class-directive.md)と同じ要素で指定する必要がありますも`x:TypeArguments`、し、その要素は、XAML ドキュメントのルート要素である必要があります。 ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。 例としては、<xref:System.Windows.Navigation.PageFunction%601>します。  
  
 ジェネリックの使用をサポートするために可能な回避策を含める、ジェネリック型を返すことができるカスタム マークアップ拡張機能を定義するか、ラップを提供するクラスのジェネリック型から派生しますが、平坦化して、独自のクラス定義内でジェネリック制約を定義します。  
  
 WPF と .NET Framework 4 を対象とすることができます、と共に XAML 2009 の機能を使用して`x:TypeArguments`、loose XAML (XAML マークアップ コンパイルされていない) に対してのみです。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
 .NET Framework 3.5 用の Windows Workflow Foundation でカスタム ワークフローは、XAML のジェネリックの使用法をサポートしていません。  
  
## <a name="see-also"></a>関連項目

- [x:TypeArguments ディレクティブ](x-typearguments-directive.md)
- [x:Class ディレクティブ](x-class-directive.md)
- [共通の XAML 言語プリミティブの組み込み型](built-in-types-for-common-xaml-language-primitives.md)
