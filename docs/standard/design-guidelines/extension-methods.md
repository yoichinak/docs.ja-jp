---
title: 拡張メソッド
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: bd5f67c3bd766625e7c22b3ca9986cfbca8854bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026420"
---
# <a name="extension-methods"></a>拡張メソッド
拡張メソッドは、言語機能により、インスタンス メソッドの呼び出し構文を使用して呼び出される静的メソッドです。 これらのメソッドは、メソッドは、操作の対象のインスタンスを表す 1 つ以上のパラメーターを取得する必要があります。  
  
 このような拡張メソッドを定義するクラスは、「スポンサー」クラスと呼ばれます、静的に宣言する必要があります。 拡張メソッドを使用するには、スポンサー クラスを定義する名前空間をインポート 1 つあります。  
  
 **X AVOID** いないこと、お持ちでない型に特に拡張メソッドを定義します。  
  
 型のソース コードを所有している場合は、通常のインスタンス メソッドを代わりに使用を検討してください。 所有していない場合に、メソッドを追加するには、十分に注意します。 自由に使用して拡張メソッドでは、これらのメソッドを使用してデザインされていない型の Api に混乱が生じる可能性があります。  
  
 **✓ CONSIDER** 拡張メソッドを使用して、次のシナリオのいずれかで。  
  
- ヘルパーを提供するには、コア インターフェイスの観点からは機能している場合、インターフェイスのすべての実装に関連する機能を記述できます。 具体的な実装は、インターフェイスにそれ以外の場合割り当てることはできないためにです。 たとえば、`LINQ to Objects`演算子は、すべての拡張メソッドとして実装されます<xref:System.Collections.Generic.IEnumerable%601>型。 そのため、いずれか`IEnumerable<>`実装は、LINQ で自動的に有効にします。  
  
- インスタンス メソッドがいくつかの型への依存関係がこのような依存関係をどのように導入するときに、依存関係の管理規則ができなくなります。 依存関係など<xref:System.String>に<xref:System.Uri?displayProperty=nameWithType>はおそらく、望ましくないため、`String.ToUri()`インスタンス メソッドが返す`System.Uri`依存関係の管理の観点から正しくない設計になります。 静的な拡張メソッド`Uri.ToUri(this string str)`返す`System.Uri`はるかに優れた設計になります。  
  
 **X AVOID** で拡張メソッドを定義する<xref:System.Object?displayProperty=nameWithType>です。  
  
 VB のユーザーは拡張メソッド構文を使用してオブジェクト参照でこのようなメソッドを呼び出すことができません。 VB は VB での参照を宣言するオブジェクトが遅延するすべてのメソッド呼び出しを強制的にバインドされているため、このようなメソッドの呼び出しをサポートしていません (と呼ばれる実際のメンバーは実行時に決定されます)、拡張メソッドへのバインドは、コンパイル時 (事前に決定中バインドされている場合)。  
  
 同じバインディング動作が存在する場合は、他の言語にガイドラインが適用されることに注意してください。 または、拡張メソッドがサポートされていません。  
  
 **X DO NOT** インターフェイスにメソッドを追加または依存関係の管理用である場合を除き、拡張の型と同じ名前空間の拡張メソッドを格納します。  
  
 **X AVOID** 異なる名前空間にある場合でも、同じシグネチャを持つ 2 つ以上の拡張メソッドを定義します。  
  
 **✓ CONSIDER** 型がインターフェイスで、ほとんどまたはすべてのケースで使用する拡張メソッドは、拡張された型と同じ名前空間に拡張メソッドを定義します。  
  
 **X DO NOT** 通常その他の機能に関連付けられている名前空間の機能を実装する拡張メソッドを定義します。 代わりに、所属する機能に関連付けられている名前空間で定義します。  
  
 **X AVOID** 拡張メソッド (たとえば、「拡張」) を専用の名前空間の汎用名前付けします。 わかりやすい名前を (たとえば、「ルーティング」) 代わりにします。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
