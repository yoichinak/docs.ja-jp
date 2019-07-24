---
title: XAML のコレクションおよびコレクション型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364340"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML のコレクションおよびコレクション型

このトピックでは、コレクションをサポートするために使用する型のプロパティを定義する方法と、親オブジェクト要素またはプロパティ要素の子要素としてコレクション項目をインスタンス化するための XAML 構文をサポートする方法について説明します。

## <a name="xaml-collection-concepts"></a>XAML コレクションの概念

概念的には、xaml オブジェクト要素または XAML プロパティ要素のスコープ内に複数の子項目がある XAML 内のリレーションシップは、コレクションとして実装する必要があります。 そのコレクションは、そのリレーションシップの親である XAML 型の特定の XAML プロパティに関連付けられている必要があります。 XAML プロセッサは、マークアップ内の各項目をバッキングコレクションプロパティの新しく追加された項目として割り当てることを想定しているため、プロパティはコレクションである必要があります。

XAML 言語レベルでは、コレクションサポートの正確な要件は完全には定義されていません。 コレクションがリストまたはディクショナリ (両方ではない) のいずれかであるという概念は、XAML 言語レベルで定義されていますが、どちらのバッキング型でも、リストまたはディクショナリは、XAML 言語で定義されていません。

XAML サービス .NET Framework xaml コレクションのサポートの概念は、.NET Framework のバッキング型に関してより明確に定義されています。 具体的には、コレクションの XAML サポートは、一般的な .NET Framework プログラミングのリストおよびディクショナリに使用されるいくつかの .NET Framework 概念と Api に基づいています。

1. インターフェイス<xref:System.Collections.IList>はリストコレクションを示します。

2. インターフェイス<xref:System.Collections.IDictionary>は、ディクショナリコレクションを示します。

3. <xref:System.Array>は配列を表し、配列はメソッド<xref:System.Collections.IList>をサポートします。

これらの各コレクションの概念では、.NET Framework xaml サービスの xaml プロセッサは、 `Add`コレクションプロパティの型の特定のインスタンスに対してメソッドを呼び出すことが想定されています。 また、シリアル化のシナリオでは、XAML プロセッサによって、リスト、ディクショナリ、または配列内の各項目について、各コレクションに固有の "項目" の概念に基づいて、個別の XAML 型のインスタンスが生成されます。 次のよう<xref:System.Collections.IList.Item%2A>なものがあります。の明示<xref:System.Array.System%23Collections%23IList%23Item%2A>的<xref:System.Array>な。 <xref:System.Collections.IDictionary.Item%2A>

## <a name="generic-collections"></a>ジェネリックコレクション

ジェネリックコレクションは、一般的な .NET Framework プログラミングに役立ち、XAML コレクションのプロパティにも使用できます。 ただし、ジェネリック<xref:System.Collections.Generic.IList%601>インターフェイスと<xref:System.Collections.Generic.IDictionary%602>は、.NET Framework xaml サービスの xaml プロセッサによって、非ジェネリック<xref:System.Collections.IList>または<xref:System.Collections.IDictionary>と同等のものとして識別されません。 ジェネリックコレクションプロパティの型の推奨される方法は、インターフェイスを実装するのではなく<xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.Generic.Dictionary%602>クラスまたはから派生することです。 これらのクラスは、非ジェネリックインターフェイスを実装します。したがって、基本実装で XAML コレクションの予想されるサポートが含まれます。

## <a name="read-only-collections-and-initialization-logic"></a>読み取り専用コレクションと初期化ロジック

.NET Framework プログラミングでは、コレクションの値を保持する任意のプロパティを読み取り専用コレクションとして作成するための一般的なデザインパターンです。 このパターンでは、コレクションプロパティを所有するインスタンスが、コレクションに対して実行される処理をより適切に制御できるようにします。 具体的には、プロパティを設定することによって、既存のコレクション全体が誤って置換されるのを防ぐことができます。 このパターンでは、呼び出し元によるコレクションへのアクセスは、コレクション型やなどの関連するコレクションインターフェイス<xref:System.Collections.IList>でサポートされているメソッドまたはプロパティを呼び出すことによって行う必要があります。

このパターンを使用すると、読み取り専用のコレクションプロパティを公開するすべてのクラスは、最初に空のコレクションを保持するためにそのプロパティを初期化する必要があります。 通常、初期化は、クラスの構築動作の一部として実行されます。 Xaml では、通常、このようなロジックがパラメーターなしのコンストラクターによって参照されることが重要です。 XAML では、プロパティを処理する前にパラメーターなしのコンストラクターが一般に呼び出されるためです (コレクションプロパティなど)。

## <a name="xaml-type-system-support-and-collections"></a>XAML 型システムのサポートとコレクション

Xaml の解析とコレクションプロパティの設定またはシリアル化の基本的なメカニズムに加えて、.NET Framework XAML サービスに実装されている XAML 型システムには、XAML のコレクションに関連するいくつかのデザイン機能が含まれています。

1. <xref:System.Xaml.XamlType.IsCollection%2A>xaml 型が XAML コレクションサポートを提供する型によってサポートされている場合に true を返します。

2. <xref:System.Xaml.XamlType.IsDictionary%2A>と<xref:System.Xaml.XamlType.IsArray%2A>は、XAML 型でサポートされているコレクションモードをさらに識別できます。 .NET Framework xaml サービスと xaml 型システムに基づくカスタム xaml プロセッサで、既存<xref:System.Xaml.XamlWriter>の実装に基づいていない場合は、どのメソッドを呼び出すかを知るために、どのコレクションモードが使用されているかを把握しておく必要があります。コレクションの処理。

3. 前の各プロパティ値は、XAML 型のの<xref:System.Xaml.XamlType.LookupCollectionKind%2A>オーバーライドによって影響を受ける可能性があります。
