---
title: 名前空間の名前
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709232"
---
# <a name="names-of-namespaces"></a>名前空間の名前
他の命名ガイドラインと同様に、名前空間に名前を付ける際の目的は、名前空間の内容がどのようなものである可能性があるかをすぐに把握するために、フレームワークを使用するプログラマにとって十分なわかりやすいものにすることです。 次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 次に例を示します。  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** から同じ名前を持つ異なる会社から名前空間を防ぐために、会社名と名前空間名をプレフィックスします。  
  
 **✓ DO** 名前空間の名前の 2 番目のレベルで、安定したバージョンに依存しない製品名を使用します。  
  
 **X DO NOT** 企業内のグループ名は、短時間である傾向があるため、名前空間の階層内の名前の基準として組織階層を使用します。 関連するテクノロジのグループを中心に、名前空間の階層を整理します。  
  
 **✓ DO** をピリオド pascal 表記を使用、および別の名前空間のコンポーネントを使用して (例: `Microsoft.Office.PowerPoint`)。 ブランドで nontraditional の大文字と小文字の区別が使用されている場合は、通常の名前空間の大文字と小文字が異なる場合でも、ブランドで定義されている大文字と小文字を  
  
 **✓ CONSIDER** 適切な場所に複数形の名前空間の名前を使用します。  
  
 たとえば、`System.Collection` の代わりに `System.Collections` を使用します。 ただし、ブランド名と頭字語は、このルールの例外です。 たとえば、`System.IOs` の代わりに `System.IO` を使用します。  
  
 **X DO NOT** その名前空間、名前空間と型に同じ名前を使用します。  
  
 たとえば、名前空間名として `Debug` を使用せずに、同じ名前空間に `Debug` という名前のクラスを指定することはできません。 いくつかのコンパイラでは、このような型を完全に修飾する必要があります。  
  
### <a name="namespaces-and-type-name-conflicts"></a>名前空間と型名の競合  
 **X DO NOT** など、ジェネリック型の名前を導入`Element`、 `Node`、 `Log`、および`Message`です。  
  
 これを行うと、一般的なシナリオでの型名の競合が発生する可能性が非常に高くなります。 ジェネリック型名 (`FormElement`、`XmlNode`、`EventLog`、`SoapMessage`) を修飾する必要があります。  
  
 名前空間のカテゴリごとに型名の競合を回避するための特定のガイドラインがあります。  
  
- **アプリケーションモデルの名前空間**  
  
     1つのアプリケーションモデルに属する名前空間は、一緒に使用されることがよくありますが、他のアプリケーションモデルの名前空間で使用されることはほとんどありません。 たとえば、<xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、<xref:System.Web.UI?displayProperty=nameWithType> 名前空間と一緒に使用されることはほとんどありません。 既知のアプリケーションモデル名前空間グループの一覧を次に示します。  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** 1 つのアプリケーション モデル内の名前空間の型に同じ名前を指定します。  
  
     たとえば、<xref:System.Web.UI?displayProperty=nameWithType> 名前空間には `Page`という名前の型が既に含まれているため、`Page` という名前の型を <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 名前空間に追加しないでください。  
  
- **インフラストラクチャの名前空間**  
  
     このグループには、一般的なアプリケーションの開発時にインポートされることがほとんどない名前空間が含まれています。 たとえば、`.Design` 名前空間は、主にプログラミングツールを開発するときに使用されます。 これらの名前空間の型との競合を回避することは、重要ではありません。  
  
- **コア名前空間**  
  
     コア名前空間には、アプリケーションモデルの名前空間とインフラストラクチャの名前空間を除く、すべての `System` 名前空間が含まれます。 コア名前空間には、他の、`System`、`System.IO`、`System.Xml`、および `System.Net`が含まれます。  
  
     **X DO NOT** 付与がコア名前空間の型と競合する名前を入力します。  
  
     たとえば、型名として `Stream` を使用しないでください。 これは、よく使用される型 <xref:System.IO.Stream?displayProperty=nameWithType>と競合します。  
  
- **テクノロジ名前空間グループ**  
  
     このカテゴリには、`Microsoft.Build.Utilities` や `Microsoft.Build.Tasks`など、`(<Company>.<Technology>*`) と同じ最初の2つの名前空間ノードを持つすべての名前空間が含まれます。 1つのテクノロジに属する型が互いに競合しないことが重要です。  
  
     **X DO NOT** 1 つのテクノロジ内の他の種類と競合する型の名前を割り当てます。  
  
     **X DO NOT** (場合を除く、テクノロジは、アプリケーション モデルで使用するものではありません) テクノロジの名前空間の型と、アプリケーション モデルの名前空間の型名の競合を紹介します。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
