---
title: フレームワーク デザインのガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: c20430f9cdcd71cc2e178d38aeed48f9fa4e75c5
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56834899"
---
# <a name="framework-design-guidelines"></a>フレームワーク デザインのガイドライン
このセクションでは、ライブラリを拡張し、.NET Framework との対話を設計するためのガイドラインを示します。 目標は、ライブラリの設計者は開発のために使用するプログラミング言語の独立した統一プログラミング モデルを提供することで API の一貫性と使いやすさを確認するためです。 .NET Framework を拡張するクラスやコンポーネントを開発する際に、これらのデザイン ガイドラインに従うことをお勧めします。 一貫性のないライブラリ デザインが悪影響を及ぼす開発者の生産性に影響し、導入を抑制します。  
  
 ガイドラインは言葉を使った簡単な推奨事項として編成されて`Do`、 `Consider`、 `Avoid`、および`Do not`します。 次のガイドラインの目的は、クラス ライブラリのデザイナーのさまざまなソリューション間のトレードオフを理解します。 優れたライブラリ デザインのこれらのデザイン ガイドラインに違反することが必要な場所の状況である可能性があります。 このような場合はまれで、する必要があります、意思決定の理由を明確かつ説得力のあることが重要です。  
  
 次のガイドライン、ブックからの抜粋は*Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリでは、2 nd Edition のパターン*Krzysztof Cwalina、Brad 内容。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 アセンブリ、名前空間、型、およびクラス ライブラリ内のメンバーの名前付けのガイドラインを提供します。  
  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 静的な抽象クラス、インターフェイス、列挙型、構造、およびその他の種類を使用するためのガイドラインを提供します。  
  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 設計とプロパティ、メソッド、コンス トラクター、フィールド、イベント、演算子、およびパラメーターの使用に関するガイドラインを提供します。  
  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 イベントや仮想メンバーは、コールバック関数を使用して、サブクラス化などの拡張メカニズムについて説明し、フレームワークの要件に最適なメカニズムを選択する方法について説明します。  
  
 [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)  
 デザイン、スロー、および例外をキャッチのデザイン ガイドラインについて説明します。  
  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 配列、属性、およびコレクションなどの一般的な型を使用して、シリアル化のサポート、等値演算子のオーバー ロードするためのガイドラインについて説明します。  
  
 [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 選択して、依存関係プロパティを実装するためのガイドラインを提供します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [概要](../../../docs/framework/get-started/overview.md)
- [開発ガイド](../../../docs/framework/development-guide.md)
