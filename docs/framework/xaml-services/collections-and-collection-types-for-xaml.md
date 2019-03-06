---
title: XAML のコレクションおよびコレクション型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494624"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML のコレクションおよびコレクション型

このトピックでは、コレクションをサポートして、親オブジェクトの要素またはプロパティ要素の子要素としてコレクション アイテムをインスタンス化するための XAML 構文をサポートすることを意図した型のプロパティを定義する方法について説明します。

## <a name="xaml-collection-concepts"></a>XAML のコレクションの概念

概念的には、XAML を XAML オブジェクト要素のスコープ内で複数の子項目がある、XAML プロパティ要素をコレクションとして実装する必要がありますまたは位置のリレーションシップです。 そのコレクションは、そのリレーションシップの親である XAML 型の特定の XAML プロパティを関連付ける必要があります。 XAML プロセッサで新しく追加された項目コレクションのプロパティのバッキングするマークアップ内の各項目を割り当てる必要がありますので、プロパティはコレクションである必要があります。

XAML 言語レベルでは、コレクションのサポートの正確な要件は完全には定義されていません。 コレクションできるリストまたはディクショナリ (ただし両方ではなく) の概念が、XAML 言語レベルで定義されているが、バッキング型がいずれかのリストを表すまたは辞書は、XAML 言語で定義されていません。

.NET Framework XAML サービスでは、バッキング型の .NET Framework の観点から、XAML コレクションのサポートの概念がより明確に定義します。 具体的には、コレクションの XAML のサポートは、いくつかの .NET Framework の概念と、リストと辞書の一般的な .NET Framework プログラミングに使用される Api に基づきます。

1. <xref:System.Collections.IList>インターフェイスは、リスト コレクションを表します。

2. <xref:System.Collections.IDictionary>インターフェイスは、ディクショナリ コレクションを表します。

3. <xref:System.Array> 配列、および配列のサポートを表します<xref:System.Collections.IList>メソッド。

呼び出す .NET Framework XAML サービスの XAML プロセッサでは、それぞれのこれらのコレクションの概念、`Add`コレクション プロパティの型の特定のインスタンス上のメソッド。 または、シリアル化のシナリオでは、XAML プロセッサ リスト、辞書または配列「項目」の各コレクションの特定の概念に基づいてで検出された各項目の個別の XAML 型のインスタンスを生成します。 これらは、: <xref:System.Collections.IList.Item%2A>;<xref:System.Collections.IDictionary.Item%2A>; 明示的な<xref:System.Array.System%23Collections%23IList%23Item%2A>の<xref:System.Array>します。

## <a name="generic-collections"></a>ジェネリック コレクション

ジェネリック コレクションはプログラミングでは、.NET Framework の一般的な役に立ち、XAML コレクション プロパティにも使用できます。 ただし、インターフェイスのジェネリック<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>として非ジェネリックと同等の .NET Framework XAML サービスの XAML プロセッサを識別しない<xref:System.Collections.IList>または<xref:System.Collections.IDictionary>します。 プロパティのジェネリック コレクション型のことをお勧めのクラスから派生するインターフェイスを実装するのではなく<xref:System.Collections.Generic.List%601>または<xref:System.Collections.Generic.Dictionary%602>します。 これらのクラスは、非ジェネリック インターフェイスを実装し、したがって、基本実装で XAML のコレクションの予想されるサポートが含まれます。

## <a name="read-only-collections-and-initialization-logic"></a>読み取り専用のコレクションと初期化ロジック

.NET Framework プログラミングでの読み取り専用コレクションとして一連の値を保持する任意のプロパティにする一般的な設計パターンになります。 このパターンは、コレクションの動作の制御を強化するコレクションのプロパティを所有するインスタンスを許可. 具体的には、パターンは、プロパティの設定を既存コレクション全体の偶発的な置換を抑止します。 このパターンでは、呼び出し元がコレクションにアクセスする必要があります代わりに行われる可能性などのコレクション型やコレクション関連インターフェイスでサポートされているメソッドまたはプロパティを呼び出すことによって<xref:System.Collections.IList>します。

このパターンを使用すると、読み取り専用コレクションのプロパティを公開する任意のクラスが、空のコレクションを保持するには、そのプロパティを初期化する必要がありますまずを意味します。 通常、初期化は、クラスの構築の動作の一部として実行されます。 XAML に便利ですが、ことが重要ですこのようなロジックが常に既定のコンス トラクターによって参照されている XAML は一般に、プロパティを処理する前に既定のコンス トラクターを呼び出すためです (コレクションのプロパティまたはそれ以外の場合)。

## <a name="xaml-type-system-support-and-collections"></a>XAML 型システムのサポートとコレクション

XAML を解析し、設定、またはコレクションのプロパティをシリアル化の基本的なしくみを超えた XAML 型システムに .NET Framework XAML サービス実装では、XAML 内のコレクションに関連するいくつかのデザイン機能が含まれています。

1. <xref:System.Xaml.XamlType.IsCollection%2A> XAML の型が XAML のコレクションのサポートを提供する型によってバックアップされている場合は true を返します。

2. <xref:System.Xaml.XamlType.IsDictionary%2A> <xref:System.Xaml.XamlType.IsArray%2A> XAML 型をサポートするコレクション モードをさらに特定できます。 カスタム XAML の .NET Framework XAML サービスと、XAML に基づくプロセッサは入力システムが、既存に基づいていない<xref:System.Xaml.XamlWriter>実装では、使用するコレクション モードを知る必要がありますを呼び出す方法を把握するためにコレクションの処理。

3. 前のプロパティ値の各のオーバーライドによって決まる可能性のある<xref:System.Xaml.XamlType.LookupCollectionKind%2A>XAML 型。
