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
author: KrzysztofCwalina
ms.openlocfilehash: 0099c5c8a863023099b377e139461606de3e1e1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940986"
---
# <a name="names-of-namespaces"></a>名前空間の名前
として他の名前付けのガイドラインと名前空間の名前を付けるときの目標を作成するための十分なわかりやすくするために名前空間のコンテンツがある可能性がありますをすぐにいるフレームワークを使用するプログラマにとって。 次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 例を次に示します。  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** から同じ名前を持つ異なる会社から名前空間を防ぐために、会社名と名前空間名をプレフィックスします。  
  
 **✓ DO** 名前空間の名前の 2 番目のレベルで、安定したバージョンに依存しない製品名を使用します。  
  
 **X DO NOT** 企業内のグループ名は、短時間である傾向があるため、名前空間の階層内の名前の基準として組織階層を使用します。 関連するテクノロジのグループの周囲の名前空間の階層を整理します。  
  
 **✓ DO** をピリオド pascal 表記を使用、および別の名前空間のコンポーネントを使用して (例: `Microsoft.Office.PowerPoint`)。 ブランドは、従来とは異なる大文字小文字の区別を使用している場合は、名前空間の通常の文字種から以上逸脱している場合でも、ブランド名で定義されている大文字小文字の区別に従ってください。  
  
 **✓ CONSIDER** 適切な場所に複数形の名前空間の名前を使用します。  
  
 たとえば、`System.Collection` の代わりに `System.Collections` を使用します。 ブランド名や略語は、この規則の例外をただしです。 たとえば、`System.IOs` の代わりに `System.IO` を使用します。  
  
 **X DO NOT** その名前空間、名前空間と型に同じ名前を使用します。  
  
 たとえば、使用しないでください`Debug`、名前空間と名前を指定し、という名前のクラスも提供`Debug`同じ名前空間。 いくつかのコンパイラでは、このような型を完全に修飾する必要があります。  
  
### <a name="namespaces-and-type-name-conflicts"></a>名前空間と型名の競合  
 **X DO NOT** など、ジェネリック型の名前を導入`Element`、 `Node`、 `Log`、および`Message`です。  
  
 名前を入力すると、そう競合シナリオで共通の非常に高い確率があります。 ジェネリック型の名前を修飾する必要があります (`FormElement`、 `XmlNode`、 `EventLog`、 `SoapMessage`)。  
  
 異なるカテゴリの名前空間の型名の競合を回避するための特定のガイドラインがあります。  
  
- **アプリケーション モデルの名前空間**  
  
     1 つのアプリケーション モデルに属している名前空間が同時に、使用される非常に多くの場合がほとんどない他のアプリケーション モデルの名前空間を使用します。 たとえば、<xref:System.Windows.Forms?displayProperty=nameWithType>と共に名前空間が使用される非常にまれ、<xref:System.Web.UI?displayProperty=nameWithType>名前空間。 よく知られたアプリケーション モデルの名前空間のグループの一覧を次には。  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** 1 つのアプリケーション モデル内の名前空間の型に同じ名前を指定します。  
  
     たとえば、という名前の型を追加しないでください`Page`に、<xref:System.Web.UI.Adapters?displayProperty=nameWithType>名前空間、ため、<xref:System.Web.UI?displayProperty=nameWithType>名前空間に既にという名前の型が含まれている`Page`。  
  
- **インフラストラクチャの名前空間**  
  
     このグループには、ほとんどの一般的なアプリケーションの開発時にインポートされる名前空間が含まれています。 たとえば、`.Design`プログラミングの開発ツールと名前空間は主に使用します。 これらの名前空間内の型との競合を避けるは重要ではありません。  
  
- **コア名前空間**  
  
     すべてのコア名前空間を含める`System`アプリケーション モデルの名前空間およびインフラストラクチャの名前空間を除く、名前空間。 その他のコア名前空間が含まれます`System`、 `System.IO`、 `System.Xml`、および`System.Net`します。  
  
     **X DO NOT** 付与がコア名前空間の型と競合する名前を入力します。  
  
     たとえば、使用しないでください`Stream`型名として。 競合する<xref:System.IO.Stream?displayProperty=nameWithType>、非常によく型を使用します。  
  
- **テクノロジの名前空間のグループ**  
  
     このカテゴリには、同じ最初の 2 つの名前空間ノードを持つすべての名前空間が含まれています。 `(<Company>.<Technology>*`)、など`Microsoft.Build.Utilities`と`Microsoft.Build.Tasks`します。 1 つのテクノロジに属している型が互いに競合しないことが重要です。  
  
     **X DO NOT** 1 つのテクノロジ内の他の種類と競合する型の名前を割り当てます。  
  
     **X DO NOT** (場合を除く、テクノロジは、アプリケーション モデルで使用するものではありません) テクノロジの名前空間の型と、アプリケーション モデルの名前空間の型名の競合を紹介します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
